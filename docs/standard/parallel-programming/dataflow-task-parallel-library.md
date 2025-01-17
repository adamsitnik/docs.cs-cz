---
title: Tok dat (Task Parallel Library)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library
ms.assetid: 643575d0-d26d-4c35-8de7-a9c403e97dd6
ms.openlocfilehash: 7f5969bc6f73b2260ae1ffa4b0026d5b4119ff88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134262"
---
# <a name="dataflow-task-parallel-library"></a>Tok dat (Task Parallel Library)
<a name="top"></a>Task Parallel Library (TPL) poskytuje součásti toku dat, které vám pomůžou zvýšit odolnost aplikací s podporou souběžného zpracování. Tyto komponenty toku dat jsou souhrnně označovány jako *Knihovna rozhraní TPL Dataflow*. Tento model toku dat propaguje programování založené na objektu actor tím, že zajišťuje předávání zpráv v procesu pro hrubý úlohy toku dat a zřetězení. Komponenty toku dat se vytvářejí na typech a plánování infrastruktury aplikace TPL a integrují se s podporou C#, Visual Basic a F# jazykovou podporou pro asynchronní programování. Tyto součásti toku dat jsou užitečné v případě, že máte více operací, které musí komunikovat s jiným asynchronním nebo pokud chcete data zpracovat, jakmile budou k dispozici. Zvažte například aplikaci, která zpracovává obrazová data z webové kamery. Pomocí modelu toku dat aplikace může zpracovat snímky imagí, jakmile budou k dispozici. Pokud aplikace vylepšuje snímky obrázků, například provedením světlé nápravy nebo snížení červeného oka, můžete vytvořit *kanál* komponent toku dat. Každá fáze kanálu může použít více hrubých paralelních funkcí, jako jsou funkce, které poskytuje TPL, k transformaci image.  
  
 Tento dokument poskytuje přehled knihovny toku dat TPL. Popisuje programovací model, předdefinované typy bloků toku dat a způsob konfigurace bloků toku dat pro splnění konkrétních požadavků vašich aplikací.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
 Tento dokument obsahuje následující části:  
  
- [Programovací model](#model)  
  
- [Předdefinované typy bloků toku dat](#predefined_types)  
  
- [Konfigurace chování bloku toku dat](#behavior)  
  
- [Vlastní bloky toku dat](#custom)  
  
<a name="model"></a>   
## <a name="programming-model"></a>Programovací model  
 Knihovna TPL Dataflow poskytuje základ pro předávání zpráv a virtuálního aplikací náročných na výkon procesoru a vstupně-výstupní operace s vysokou propustností a nízkou latencí. Poskytuje vám také explicitní kontrolu nad tím, jak jsou data ukládána do vyrovnávací paměti a pohybují se systémem. Pro lepší pochopení programovacího modelu toku dat zvažte aplikaci, která asynchronně načte obrázky z disku a vytvoří složený z těchto imagí. Tradiční programovací modely obvykle vyžadují, abyste k koordinaci úloh a přístupu ke sdíleným datům použili zpětná volání a synchronizační objekty, jako jsou zámky. Pomocí modelu programování toku dat můžete vytvořit objekty Dataflow, které zpracovávají obrázky při jejich čtení z disku. V modelu toku dat deklarujete, jakým způsobem jsou data zpracována, jakmile budou k dispozici, a také všechny závislosti mezi daty. Vzhledem k tomu, že modul runtime spravuje závislosti mezi daty, můžete se často vyhnout nutnosti synchronizovat přístup ke sdíleným datům. Kromě toho, vzhledem k tomu, že modul runtime plánuje práci na základě asynchronního příjezdu dat, může tok dat zlepšit odezvu a propustnost tím, že efektivně spravuje podkladová vlákna. Příklad, který používá programovací model Dataflow k implementaci zpracování bitové kopie v aplikaci model Windows Forms, naleznete v tématu [Návod: použití toku dat v aplikaci model Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
### <a name="sources-and-targets"></a>Zdroje a cíle  
 Knihovna TPL Dataflow se skládá z *bloků toku*dat, což jsou datové struktury, které ukládají data do vyrovnávací paměti a zpracovávají data. TPL definuje tři druhy bloků toku: *zdrojové bloky*, *cílové bloky*a *bloky pro šíření*. Zdrojový blok funguje jako zdroj dat a lze ho číst z. Cílový blok funguje jako přijímač dat a lze do něj zapisovat. Blok šíření funguje jako zdrojový blok i cílový blok a lze ho číst z a zapisovat do. TPL definuje rozhraní <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> pro reprezentaci zdrojů, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> k reprezentování cílů a <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602?displayProperty=nameWithType> k reprezentování přenosů. <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> dědí z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Knihovna TPL Dataflow poskytuje několik předdefinovaných typů bloků toku dat, které implementují rozhraní <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>a <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>. Tyto typy bloků toku dat jsou popsány v tomto dokumentu v části [předdefinované typy bloků toku](#predefined_types)dat.  
  
### <a name="connecting-blocks"></a>Spojovací bloky  
 Bloky toku dat můžete propojit s *kanály*pro formuláře, které jsou lineární sekvence bloků toku dat nebo *sítě*, které jsou grafy bloků toku dat. Kanál je jedna forma sítě. V kanálu nebo v síti zdroje asynchronně šíří data do cílů, jakmile budou tato data k dispozici. Metoda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=nameWithType> propojuje zdrojový blok toku dat s cílovým blokem. Zdroj může být propojený s žádným nebo více cíli. cíle lze propojit z nula nebo více zdrojů. Bloky toku dat můžete do nebo z kanálu nebo sítě souběžně přidávat nebo odebírat. Předdefinované typy bloků toku dat zpracovávají všechny aspekty bezpečnosti pro přístup z více vláken při propojování a odpojování.  
  
 Příklad, který spojuje bloky toku dat s cílem vytvořit základní kanál, najdete v tématu [Návod: vytvoření kanálu toku](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)dat. Příklad propojení bloků toku dat za účelem vytvoření komplexnější sítě najdete v tématu [Návod: použití toku dat v aplikaci model Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md). Příklad, který odpojí cíl ze zdroje po tom, co zdroj nabízí cíl zprávy, naleznete v tématu [How to: Unlink Dataflow Blocks](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md).  
  
#### <a name="filtering"></a>Filtrování  
 Při volání metody <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=nameWithType> pro propojení zdroje s cílem, můžete zadat delegáta, který určuje, zda cílový blok přijme nebo odmítne zprávu na základě hodnoty této zprávy. Tento mechanismus filtrování je užitečný způsob, jak zajistit, aby blok toku dat přijímal jenom určité hodnoty. Pro většinu předdefinovaných typů bloku toku dat je-li zdrojový blok připojen k více cílovým blokům, poté, co cílový blok odmítne zprávu, zdroj nabídne tuto zprávu dalšímu cíli. Pořadí, ve kterém zdroj nabízí zprávy na cíle, je definováno zdrojem a může se lišit podle typu zdroje. Většina typů zdrojových bloků zastaví nabízenou zprávu po tom, co jeden cíl přijme tuto zprávu. Jedinou výjimkou z tohoto pravidla je <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> třída, která nabízí každou zprávu všem cílům i v případě, že některé cíle odmítnou zprávu. Příklad, který používá filtrování pro zpracování pouze určitých zpráv, naleznete v tématu [Návod: použití toku dat v aplikaci model Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
> [!IMPORTANT]
> Vzhledem k tomu, že každý předdefinovaný typ bloku toku dat zaručuje, že se zprávy šíří v pořadí, ve kterém byly přijaty, musí být každá zpráva načtena ze zdrojového bloku předtím, než může zdrojový blok zpracovat další zprávu. Proto když použijete filtrování k připojení více cílů ke zdroji, ujistěte se, že alespoň jeden cílový blok obdrží každou zprávu. V opačném případě se aplikace může zablokovat.  
  
### <a name="message-passing"></a>Předávání zpráv  
 Programovací model Dataflow se vztahuje na pojem *předávání zpráv*, kde nezávislé komponenty programu spolu komunikují prostřednictvím posílání zpráv. Jedním ze způsobů, jak šířit zprávy mezi součástmi aplikace, je volat <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> metody pro odesílání zpráv do cílového bloku toku dat post (<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> funguje synchronně; <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> funguje asynchronně) a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A><xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A> metody pro příjem zpráv ze zdrojových bloků. Tyto metody můžete kombinovat s kanály toku dat nebo sítěmi tím, že odesíláte vstupní data do hlavního uzlu (cílový blok) a přijímáte výstupní data z uzlu terminálu kanálu nebo uzlů terminálů sítě (jeden nebo více zdrojových bloků). Můžete také použít metodu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Choose%2A> ke čtení z prvního z poskytnutých zdrojů, které mají data k dispozici a k provádění akcí u těchto dat.  
  
 Zdrojové bloky nabízejí data do cílových bloků voláním metody <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A?displayProperty=nameWithType>. Cílový blok odpoví na nabízenou zprávu jedním ze tří způsobů: může přijmout zprávu, odmítnout zprávu nebo odložit zprávu. Když cíl přijme zprávu, metoda <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Accepted>. Když cíl zprávu odmítne, metoda <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Declined>. Pokud cíl vyžaduje, aby již nepřijímal žádné zprávy ze zdroje, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.DecliningPermanently>. Předdefinované typy zdrojových bloků nenabízejí zprávy do propojených cílů po přijetí takové návratové hodnoty a automaticky odpojí z těchto cílů.  
  
 Když cílový blok odloží zprávu pro pozdější použití, metoda <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> vrátí <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Postponed>. Cílový blok, který odloží zprávu, může později zavolat metodu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReserveMessage%2A?displayProperty=nameWithType> a pokusit se vyhradit nabízenou zprávu. V tomto okamžiku je zpráva buď stále k dispozici, a může ji použít cílovým blokem, nebo zpráva byla pořízena jiným cílem. Pokud cílový blok později vyžaduje zprávu nebo už zprávu nepotřebuje, volá metodu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReleaseReservation%2A>, v uvedeném pořadí. Rezervace zprávy obvykle používá typy bloků toku dat, které fungují v nehladovém režimu. Nehladový režim je vysvětlen dále v tomto dokumentu. Místo zachovávání odložené zprávy může cílový blok také použít metodu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=nameWithType> k pokusu o přímé využití odložené zprávy.  
  
### <a name="dataflow-block-completion"></a>Dokončení bloku toku dat  
 Bloky toku dat také podporují koncept *dokončení*. Blok toku dat, který je v dokončeném stavu, neprovede žádnou další práci. Každý blok toku dat má přidružený objekt <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, který se označuje jako *úloha dokončení*, která představuje stav dokončení bloku. Vzhledem k tomu, že můžete počkat na dokončení <xref:System.Threading.Tasks.Task> objektu, můžete pomocí úloh dokončení počkat na dokončení jednoho nebo více uzlů terminálů sítě toku dat. Rozhraní <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> definuje metodu <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>, která informuje blok toku dat žádosti o dokončení a vlastnost <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A>, která vrací úlohu dokončení pro blok toku dat. Rozhraní <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> dědí jak <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, tak <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Existují dva způsoby, jak určit, zda byl blok toku dat dokončen bez chyb, došlo k jedné nebo více chybám nebo byl zrušen. Prvním způsobem je zavolat metodu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> u úlohy dokončení ve `try`-bloku `catch` (`Try`-`Catch` v Visual Basic). Následující příklad vytvoří objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, který vyvolá <xref:System.ArgumentOutOfRangeException>, pokud jeho vstupní hodnota je menší než nula. <xref:System.AggregateException> je vyvolána, když tento příklad volá <xref:System.Threading.Tasks.Task.Wait%2A> na úkol dokončení. K <xref:System.ArgumentOutOfRangeException> je k dispozici prostřednictvím vlastnosti <xref:System.AggregateException.InnerExceptions%2A> objektu <xref:System.AggregateException>.  
  
 [!code-csharp[TPLDataflow_Overview#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#10)]
 [!code-vb[TPLDataflow_Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#10)]  
  
 Tento příklad ukazuje případ, ve kterém výjimka Neošetřená v delegátu pro spuštění bloku toku dat. Doporučujeme zpracovávat výjimky v podvodních blocích. Nicméně pokud to nemůžete udělat, blok se chová, jako by byl zrušen a nezpracovává příchozí zprávy.  
  
 Pokud je blok toku dat explicitně zrušen, objekt <xref:System.AggregateException> obsahuje <xref:System.OperationCanceledException> ve vlastnosti <xref:System.AggregateException.InnerExceptions%2A>. Další informace o zrušení toku dat najdete v části [Povolení zrušení](#enabling-cancellation) .  
  
 Druhým způsobem, jak určit stav dokončení bloku toku dat, je použití pokračování úlohy dokončení nebo použití asynchronních funkcí jazyka C# a Visual Basic k asynchronnímu čekání na úkol dokončení. Delegát, který zadáte metodě <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>, přebírá objekt <xref:System.Threading.Tasks.Task>, který představuje předchozí úlohu. V případě vlastnosti <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> má delegát pro pokračování vlastní úlohu dokončení. Následující příklad je podobný předchozímu, s tím rozdílem, že používá také metodu <xref:System.Threading.Tasks.Task.ContinueWith%2A> k vytvoření pokračování úlohy, která vytiskne stav celkové operace toku dat.  
  
 [!code-csharp[TPLDataflow_Overview#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#11)]
 [!code-vb[TPLDataflow_Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#11)]  
  
 V těle úlohy pokračování můžete také použít vlastnosti, například <xref:System.Threading.Tasks.Task.IsCanceled%2A>, a určit tak další informace o stavu dokončení bloku toku dat. Další informace o pokračujících úkolech a jejich vztahu ke zrušení a zpracování chyb naleznete v tématu [zřetězení úloh pomocí úloh pokračování](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md), [zrušení úkolu](../../../docs/standard/parallel-programming/task-cancellation.md)a [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
 [[Přejít na začátek](#top)]  
  
<a name="predefined_types"></a>   
## <a name="predefined-dataflow-block-types"></a>Předdefinované typy bloků toku dat  
 Knihovna TPL Dataflow poskytuje několik předdefinovaných typů bloků toku dat. Tyto typy jsou rozděleny do tří kategorií: *bloky ukládání do vyrovnávací paměti*, *bloky spouštění*a *bloky seskupení*. Následující části popisují typy bloků, které tvoří tyto kategorie.  
  
### <a name="buffering-blocks"></a>Bloky ukládání do vyrovnávací paměti  
 Ukládání bloků do vyrovnávací paměti blokuje data, která používají příjemci dat. Knihovna TPL Dataflow poskytuje tři typy bloků vyrovnávací paměti: <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601?displayProperty=nameWithType>a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601?displayProperty=nameWithType>.  
  
#### <a name="bufferblockt"></a>BufferBlock (T)  
 Třída <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> představuje asynchronní strukturu zasílání zpráv pro obecné účely. Tato třída ukládá do fronty první v, první ven (FIFO) zprávy, na které může zapisovat více zdrojů nebo číst z více cílů. Když cíl obdrží zprávu z objektu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>, tato zpráva se odebere z fronty zpráv. Proto i když objekt <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> může mít více cílů, obdrží každou zprávu pouze jeden cíl. Třída <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> je užitečná v případě, že chcete předat více zpráv jiné komponentě a tato součást musí přijmout každou zprávu.  
  
 Následující základní příklad účtuje několik <xref:System.Int32> hodnot do objektu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> a pak tyto hodnoty přečte z tohoto objektu.  
  
 [!code-csharp[TPLDataflow_Overview#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#1)]
 [!code-vb[TPLDataflow_Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#1)]  
  
 Úplný příklad, který ukazuje, jak napsat zprávy do a číst zprávy z objektu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>, naleznete v tématu [How to: Write Message and Read Messages from the Dataflow Block](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md).  
  
#### <a name="broadcastblockt"></a>BroadcastBlock (T)  
 Třída <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> je užitečná v případě, že je nutné předat více zpráv jiné komponentě, ale komponenta potřebuje pouze nejnovější hodnotu. Tato třída je užitečná také v případě, že chcete vysílat zprávu na více součástí.  
  
 Následující základní příklad účtuje <xref:System.Double> hodnotu do objektu <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> a pak tuto hodnotu z tohoto objektu přečte několikrát. Vzhledem k tomu, že hodnoty nejsou odebrány z <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> objektů po jejich čtení, je stejná hodnota vždy k dispozici.  
  
 [!code-csharp[TPLDataflow_Overview#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#2)]
 [!code-vb[TPLDataflow_Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#2)]  
  
 Úplný příklad, který ukazuje, jak použít <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> pro vysílání zprávy do více cílových bloků, naleznete v tématu [How to: určení Plánovač úloh v bloku toku](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)dat.  
  
#### <a name="writeonceblockt"></a>WriteOnceBlock (T)  
 Třída <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> se podobá <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> třídy s tím rozdílem, že objekt <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> může být zapsán pouze jednorázově. Můžete si představit <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> jako v C# klíčovém slově [ReadOnly](../../csharp/language-reference/keywords/readonly.md) ([ReadOnly](../../visual-basic/language-reference/modifiers/readonly.md) v Visual Basic), s tím rozdílem, že objekt <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> se po přijetí hodnoty namísto konstrukce stala neměnné. Podobně jako třída <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>, když cíl obdrží zprávu z objektu <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>, tato zpráva není odebrána z tohoto objektu. Proto více cílů obdrží kopii zprávy. Třída <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> je užitečná v případě, že chcete rozšířit pouze prvních více zpráv.  
  
 Následující základní příklad účtuje více <xref:System.String> hodnot do objektu <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> a pak přečte hodnotu vrácenou z tohoto objektu. Vzhledem k tomu, že objekt <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> lze zapsat pouze jednou, poté, co objekt <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obdrží zprávu, zahodí následné zprávy.  
  
 [!code-csharp[TPLDataflow_Overview#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#3)]
 [!code-vb[TPLDataflow_Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#3)]  
  
 Úplný příklad, který ukazuje, jak použít <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> pro získání hodnoty první operace, která skončí, naleznete v tématu [How to: Unlink Dataflow Blocks](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md).  
  
### <a name="execution-blocks"></a>Bloky spuštění  
 Bloky spouštění volají uživatelem poskytnutý delegát pro každou část přijatých dat. Knihovna TPL Dataflow poskytuje tři typy bloku spuštění: <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.  
  
#### <a name="actionblockt"></a>ActionBlock (T)  
 Třída <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> je cílový blok, který volá delegáta při přijímání dat. Objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> můžete představit jako delegát, který se spouští asynchronně, když budou data k dispozici. Delegát, který zadáte do objektu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, může být typu <xref:System.Action%601> nebo typu `System.Func<TInput, Task>`. Použijete-li objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> s <xref:System.Action%601>, zpracování každého elementu vstupu je považováno za dokončené, když se delegát vrátí. Použijete-li objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> s `System.Func<TInput, Task>`, zpracování každého vstupního elementu je považováno za dokončené pouze v případě, že je vrácen objekt <xref:System.Threading.Tasks.Task> dokončen. Pomocí těchto dvou mechanismů lze použít <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> pro synchronní i asynchronní zpracování každého elementu Input.  
  
 Následující základní příklad účtuje více <xref:System.Int32>ch hodnot do objektu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. Objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> vytiskne tyto hodnoty do konzoly. Tento příklad nastaví blok na stav dokončeno a počká na dokončení všech úloh toku dat.  
  
 [!code-csharp[TPLDataflow_Overview#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#4)]
 [!code-vb[TPLDataflow_Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#4)]  
  
 Kompletní příklady, které ukazují, jak používat delegáty s třídou <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, naleznete v tématu [How to: Action, když blok toku dat přijímá data](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md).  
  
#### <a name="transformblocktinput-toutput"></a>Operace TransformBlock (TInput, TOutput)  
 Třída <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> se podobá <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> třídy, s tím rozdílem, že funguje jako zdroj i jako cíl. Delegát, který předáte objektu <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, vrací hodnotu typu `TOutput`. Delegát, který zadáte do objektu <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, může být typu `System.Func<TInput, TOutput>` nebo typu `System.Func<TInput, Task<TOutput>>`. Použijete-li objekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> s `System.Func<TInput, TOutput>`, zpracování každého elementu vstupu je považováno za dokončené, když se delegát vrátí. Použijete-li objekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, který se používá s `System.Func<TInput, Task<TOutput>>`, zpracování každého vstupního elementu je považováno za dokončené pouze v případě, že je vrácen objekt <xref:System.Threading.Tasks.Task%601> dokončen. Stejně jako u <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>pomocí těchto dvou mechanismů lze použít <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pro synchronní i asynchronní zpracování každého elementu Input.  
  
 Následující základní příklad vytvoří objekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, který vypočítá druhou odmocninu jeho vstupu. Objekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> přebírá <xref:System.Int32> hodnoty jako vstup a generuje <xref:System.Double> hodnoty jako výstup.  
  
 [!code-csharp[TPLDataflow_Overview#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#5)]
 [!code-vb[TPLDataflow_Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#5)]  
  
 Kompletní příklady, které používá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> v síti bloků toku dat, které provádí zpracování bitové kopie v model Windows Forms aplikaci naleznete v tématu [Návod: použití toku dat v aplikaci model Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
#### <a name="transformmanyblocktinput-toutput"></a>TransformManyBlock(TInput, TOutput)  
 Třída <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> se podobá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> třídy, s tím rozdílem, že <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> vytvoří pro každou vstupní hodnotu nula nebo více výstupních hodnot namísto jedné výstupní hodnoty pro každou vstupní hodnotu. Delegát, který zadáte do objektu <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>, může být typu `System.Func<TInput, IEnumerable<TOutput>>` nebo typu `System.Func<TInput, Task<IEnumerable<TOutput>>>`. Použijete-li objekt <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> s `System.Func<TInput, IEnumerable<TOutput>>`, zpracování každého elementu vstupu je považováno za dokončené, když se delegát vrátí. Použijete-li objekt <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> s `System.Func<TInput, Task<IEnumerable<TOutput>>>`, zpracování každého vstupního elementu je považováno za kompletní pouze v případě, že je vrácen objekt `System.Threading.Tasks.Task<IEnumerable<TOutput>>` dokončen.  
  
 Následující základní příklad vytvoří objekt <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>, který rozdělí řetězce do jejich jednotlivých znakových sekvencí. Objekt <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> přebírá <xref:System.String> hodnoty jako vstup a generuje <xref:System.Char> hodnoty jako výstup.  
  
 [!code-csharp[TPLDataflow_Overview#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#6)]
 [!code-vb[TPLDataflow_Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#6)]  
  
 Kompletní příklady, které používají <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> k vytvoření více nezávislých výstupů pro každý vstup v kanálu toku dat, naleznete v tématu [Návod: vytvoření kanálu toku](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)dat.  
  
#### <a name="degree-of-parallelism"></a>Stupeň paralelismu  
 Každý <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekt ukládá do vyrovnávací paměti vstupní zprávy, dokud je blok připravený na jejich zpracování. Ve výchozím nastavení tyto třídy zpracovávají zprávy v pořadí, ve kterém jsou přijímány, vždy jedna zpráva. Můžete také určit stupeň paralelismu pro povolení <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objektů pro souběžné zpracování více zpráv. Další informace o souběžném spuštění najdete v části určení stupně paralelismu v níže v tomto dokumentu. Příklad, který nastaví míru paralelismus pro povolení bloku toku dat spouštění pro zpracování více než jedné zprávy najednou, naleznete v tématu [How to: set a stupně paralelismus v bloku toku](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)dat.  
  
#### <a name="summary-of-delegate-types"></a>Souhrn typů delegátů  
 Následující tabulka shrnuje typy delegátů, které lze zadat pro objekty <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>. Tato tabulka také určuje, zda typ delegáta funguje synchronně nebo asynchronně.  
  
|Typ|Typ synchronního delegáta|Typ asynchronního delegáta|  
|----------|-------------------------------|--------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|`System.Action`|`System.Func<TInput, Task>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|`System.Func<TInput, TOutput>`|`System.Func<TInput, Task<TOutput>>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|`System.Func<TInput, IEnumerable<TOutput>>`|`System.Func<TInput, Task<IEnumerable<TOutput>>>`|  
  
 Lambda výrazy můžete použít také při práci s typy bloku spuštění. Příklad, který ukazuje, jak použít výraz lambda s blokem spuštění, naleznete v tématu [How to: Action, když blok toku dat přijímá data](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md).  
  
### <a name="grouping-blocks"></a>Bloky seskupení  
 Bloky seskupení seskupují data z jednoho nebo více zdrojů a v různých omezeních. Knihovna TPL Dataflow poskytuje tři typy bloku spojení: <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>.  
  
#### <a name="batchblockt"></a>Tříd BatchBlock (T)  
 Třída <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> kombinuje sady vstupních dat, které se označují jako dávky, do polí výstupních dat. Velikost každé dávky určíte při vytváření objektu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>. Když objekt <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> dostane zadaný počet vstupních elementů, asynchronně se rozšíří pole, které obsahuje tyto prvky. Pokud je objekt <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> nastavený na stav dokončeno, ale neobsahuje dostatek prvků pro vytvoření dávky, rozšíří konečné pole, které obsahuje zbývající vstupní prvky.  
  
 Třída <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> pracuje buď v *hladovém* , nebo v *nehladovém* režimu. V režimu hladce, který je výchozím nastavením, <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekt akceptuje každou zprávu, že je nabízena a šíří pole po přijetí zadaného počtu prvků. V nehladovém režimu objekt <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> odloží všechny příchozí zprávy, dokud dostatek zdrojů nenabídly do bloku zprávy, aby mohl vytvořit dávku. Hladový režim obvykle provádí lepší režim než hladec, protože vyžaduje méně režijních nákladů na zpracování. Nehladý režim však můžete použít v případě, že je nutné sjednotit spotřebu z více zdrojů atomicky. Nastavte Nehladový režim nastavením <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> na `False` v parametru `dataflowBlockOptions` v konstruktoru <xref:System.Threading.Tasks.Dataflow.BatchBlock%601.%23ctor%2A>.  
  
 Následující základní příklad účtuje několik <xref:System.Int32> hodnot do objektu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, který obsahuje deset prvků v dávce. Aby bylo zaručeno, že všechny hodnoty šíří mimo <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, tento příklad volá metodu <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>. Metoda <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> nastaví objekt <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> na stav dokončeno, a proto objekt <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> rozšíří zbývající prvky jako finální dávku.  
  
 [!code-csharp[TPLDataflow_Overview#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#7)]
 [!code-vb[TPLDataflow_Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#7)]  
  
 Kompletní příklad, který používá <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> ke zlepšení efektivity operací vložení databáze, najdete v tématu [Názorný postup: použití tříd BatchBlock a BatchedJoinBlock ke zvýšení efektivity](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md).  
  
#### <a name="joinblockt1-t2-"></a>JoinBlock (T1, T2,...)  
 Třídy <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> shromažďují vstupní prvky a šíří objekty <xref:System.Tuple%602?displayProperty=nameWithType> nebo <xref:System.Tuple%603?displayProperty=nameWithType> objektů, které obsahují tyto prvky. Třídy <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> nedědí z <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>. Místo toho poskytují vlastnosti, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target1%2A>, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target2%2A>a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603.Target3%2A>, které implementují <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Stejně jako <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> fungují v hladovém nebo nehladovém režimu. V režimu hladce, což je výchozí hodnota, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nebo <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objekt akceptuje každou zprávu, že je nabízena a šíří řazenou kolekci členů po každém z jeho cílů, obdrží alespoň jednu zprávu. V nehladovém režimu objekt <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nebo <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> odloží všechny příchozí zprávy, dokud nebudou všechny cíle nabídnuty daty, která jsou potřebná k vytvoření řazené kolekce členů. V tomto okamžiku se zablokuje pomocí dvoufázového potvrzovacího protokolu, aby byly atomicky načteny všechny požadované položky ze zdrojů. Díky tomuto odložení je možné, že by jiná entita mohla data během této doby spotřebovat, aby celkový systém mohl předávat pokrok.  
  
 Následující základní příklad ukazuje případ, ve kterém <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> objekt vyžaduje více dat pro výpočet hodnoty. Tento příklad vytvoří objekt <xref:System.Threading.Tasks.Dataflow.JoinBlock%603>, který vyžaduje dvě hodnoty <xref:System.Int32> a <xref:System.Char> hodnotu pro provedení aritmetické operace.  
  
 [!code-csharp[TPLDataflow_Overview#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#8)]
 [!code-vb[TPLDataflow_Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#8)]  
  
 Kompletní příklad, který používá <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objektů v nehladovém režimu pro kovizuální sdílení prostředku, naleznete v tématu [How to: use JoinBlock ke čtení dat z více zdrojů](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md).  
  
#### <a name="batchedjoinblockt1-t2-"></a>BatchedJoinBlock (T1, T2,...)  
 Třídy <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%603> shromažďují dávky vstupních prvků a šíří objekty `System.Tuple(IList(T1), IList(T2))` nebo `System.Tuple(IList(T1), IList(T2), IList(T3))` objektů, které obsahují tyto prvky. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> můžete představit jako kombinaci <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> a <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>. Určete velikost každé dávky při vytváření objektu <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> také poskytuje vlastnosti, <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A>, které implementují <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>. Při přijetí zadaného počtu vstupních prvků ze všech cílů objekt <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> asynchronně šíří `System.Tuple(IList(T1), IList(T2))` objekt, který obsahuje tyto prvky.  
  
 Následující základní příklad vytvoří objekt <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>, který obsahuje výsledky, <xref:System.Int32> hodnoty a chyby, které jsou <xref:System.Exception> objekty. Tento příklad provede více operací a zapíše výsledky do vlastnosti <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A> a do vlastnosti <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A> objektu <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>. Vzhledem k tomu, že počet úspěšných a neúspěšných operací není v předstihu znám, <xref:System.Collections.Generic.IList%601> objekty umožňují, aby každý cíl přijímal nula nebo více hodnot.  
  
 [!code-csharp[TPLDataflow_Overview#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#9)]
 [!code-vb[TPLDataflow_Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#9)]  
  
 Kompletní příklad, který používá <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> k zachycení výsledků a všech výjimek, ke kterým dojde, když program načítá z databáze, najdete v tématu [Návod: použití tříd BatchBlock a BatchedJoinBlock ke zvýšení efektivity](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md).  
  
 [[Přejít na začátek](#top)]  
  
<a name="behavior"></a>   
## <a name="configuring-dataflow--block-behavior"></a>Konfigurace chování bloku toku dat  
 Můžete povolit další možnosti poskytnutím <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=nameWithType> objektu konstruktoru typu bloku toku dat. Tyto možnosti řídí chování, jako je Plánovač, který spravuje základní úlohu a stupeň paralelismu. <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions> má také odvozené typy, které určují chování specifické pro určité typy bloků toku dat. Následující tabulka shrnuje, které typy možností jsou spojené s každým typem bloku toku dat.  
  
|Typ bloku toku dat|typ <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
  
 Následující části poskytují další informace o důležitých typech možností bloku toku dat, které jsou k dispozici prostřednictvím tříd <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions?displayProperty=nameWithType>a <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions?displayProperty=nameWithType>.  
  
### <a name="specifying-the-task-scheduler"></a>Určení Plánovač úloh  
 Každý předdefinovaný blok toku dat používá mechanizmus plánování úloh TPL k provádění aktivit, jako je například šíření dat do cíle, příjem dat ze zdroje a spuštění uživatelem definovaných delegátů, když budou data k dispozici. <xref:System.Threading.Tasks.TaskScheduler> je abstraktní třída, která představuje Plánovač úloh, který vyřadí do fronty úlohy do vláken. Výchozí Plánovač úloh <xref:System.Threading.Tasks.TaskScheduler.Default%2A>používá ke frontování a provádění práce třídu <xref:System.Threading.ThreadPool>. Výchozí Plánovač úloh můžete přepsat nastavením vlastnosti <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> při vytváření objektu bloku toku dat.  
  
 Když stejný Plánovač úloh spravuje více bloků toku dat, může v nich vyhovět zásadám. Například pokud jsou jednotlivé bloky toku dat nakonfigurovány tak, aby cílí na výhradní Plánovač stejného <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu, bude serializována veškerá práce, která běží v těchto blocích. Podobně platí, že pokud jsou tyto bloky nakonfigurovány tak, aby cílí na souběžný Plánovač stejného <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu a aby byl Plánovač nakonfigurován tak, aby měl maximální úroveň souběžnosti, všechny práce z těchto bloků budou omezeny na tento počet souběžných operací. Příklad, který používá třídu <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> k povolení, aby operace čtení probíhaly paralelně, ale operace zápisu mají být provedeny výhradně pro všechny ostatní operace, naleznete v tématu [How to: určení Plánovač úloh v bloku toku](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)dat. Další informace o Plánovači úloh v TPL naleznete v tématu <xref:System.Threading.Tasks.TaskScheduler> třídy.  
  
### <a name="specifying-the-degree-of-parallelism"></a>Určení stupně paralelismu  
 Ve výchozím nastavení mají tři typy bloku spuštění, které poskytuje knihovna Dataflow v TPL, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>, zpracovávat jednu zprávu v jednom okamžiku. Tyto typy bloků toku dat také zpracovávají zprávy v pořadí, ve kterém jsou přijaty. Chcete-li těmto blokům toku dat Povolit souběžné zpracování zpráv, nastavte vlastnost <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> při vytváření objektu bloku toku dat.  
  
 Výchozí hodnota <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> je 1, což zaručuje, že blok toku dat zpracuje vždy jednu zprávu. Když nastavíte tuto vlastnost na hodnotu, která je větší než 1, povolí blok toku dat souběžně zpracovávat více zpráv. Nastavením této vlastnosti na <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=nameWithType> povolíte základnímu Plánovači úloh spravovat maximální stupeň souběžnosti.  
  
> [!IMPORTANT]
> Když zadáte maximální stupeň paralelismu, který je větší než 1, zpracovává se souběžně několik zpráv, takže zprávy nemusejí být zpracovány v pořadí, ve kterém byly přijaty. Pořadí, ve kterém jsou zprávy výstupem z bloku, je však stejné jako v tom, v jakém byly přijaty.  
  
 Vzhledem k tomu, že vlastnost <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> představuje maximální stupeň paralelismu, může být blok toku dat proveden s menším stupněm paralelismu, než určíte. Blok toku dat může používat menší stupeň paralelismu k splnění jeho funkčních požadavků nebo nedostatku dostupných systémových prostředků. Blok toku dat nikdy nevolí více paralelismu, než zadáte.  
  
 Hodnota vlastnosti <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> je exkluzivní pro každý objekt bloku toku dat. Pokud například čtyři objekty bloku Dataflow každý určí 1 pro maximální stupeň paralelismu, mohou být všechny čtyři objekty bloku toku dat potenciálně spouštěny paralelně.  
  
 Příklad, který nastaví maximální stupeň paralelismu na paralelní výskyt operací, naleznete v tématu [How to: set a stupně paralelismus v bloku toku](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)dat.  
  
### <a name="specifying-the-number-of-messages-per-task"></a>Určení počtu zpráv na úlohu  
 Předdefinované typy bloků toku dat používají úlohy ke zpracování více elementů vstupu. To pomáhá minimalizovat počet objektů úloh, které jsou požadovány pro zpracování dat, což umožňuje aplikacím běžet efektivněji. Pokud ale úkoly z jedné sady bloků toku dat zpracovávají data, může se stát, že se úlohy z jiných bloků toku budou muset čekat na dobu zpracování v rámci řazení zpráv do fronty. Chcete-li umožnit lepší rovnost mezi úlohami toku dat, nastavte vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A>. Pokud je <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> nastaveno na <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=nameWithType>, což je výchozí hodnota, úloha používaná blokem toku dat zpracovává tolik zpráv, kolik jich je k dispozici. Pokud je <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> nastaveno na jinou hodnotu než <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded>, blok toku dat zpracovává maximálně tento počet zpráv na objekt <xref:System.Threading.Tasks.Task>. I když nastavení vlastnosti <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> může zvýšit spravedlivosti mezi úkoly, může způsobit, že systém vytvoří více úloh, než kolik je potřeba, což může snížit výkon.  
  
### <a name="enabling-cancellation"></a>Povolení zrušení  
 TPL poskytuje mechanismus, který umožňuje úlohám koordinovat zrušení v rámci spolupráce. Chcete-li povolit bloky toku dat pro účast v tomto mechanismu zrušení, nastavte vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>. Pokud je tento objekt <xref:System.Threading.CancellationToken> nastavený na stornovaný stav, všechny bloky toku dat, které monitorují toto spuštění tohoto tokenu aktuální položky, ale nespouštějí následné zpracování položek. Tyto bloky toku dat také vymažou všechny zprávy ve vyrovnávací paměti, vydávají připojení k jakémukoli zdrojovému a cílovému bloku a přechod do stavu zrušeno. Přechodem do stornovaného stavu má vlastnost <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> vlastnost <xref:System.Threading.Tasks.Task.Status%2A> nastavenou na <xref:System.Threading.Tasks.TaskStatus.Canceled>, pokud během zpracování nedošlo k výjimce. V takovém případě je <xref:System.Threading.Tasks.Task.Status%2A> nastaveno na <xref:System.Threading.Tasks.TaskStatus.Faulted>.  
  
 Příklad, který ukazuje, jak použít zrušení v model Windows Forms aplikace, naleznete v tématu [How to: Cancel a Block toku](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)dat. Další informace o zrušení v TPL naleznete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="specifying-greedy-versus-non-greedy-behavior"></a>Určení hladového versus nehladového chování  
 Několik typů bloků datového toku pro seskupení může pracovat buď v *hladovém* , nebo *nehladovém* režimu. Ve výchozím nastavení jsou předdefinované typy bloků toku dat provozovány v hladovém režimu.  
  
 Pro typy bloku JOIN, jako je například <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>, hladový režim znamená, že blok okamžitě přijímá data, i když odpovídající data, ke kterým se má připojit, ještě nejsou k dispozici. Nehladový režim znamená, že blok odloží všechny příchozí zprávy, dokud není k dispozici na všech svých cílech pro dokončení spojení. Pokud již žádná z odložených zpráv není k dispozici, blok spojení uvolní všechny odložené zprávy a restartuje proces. Pro třídu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>, hladové a nehladé chování je podobné, s výjimkou toho, že v nehladovém režimu, objekt <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> odloží všechny příchozí zprávy, dokud není dostatek dostupných z různých zdrojů k dokončení dávky.  
  
 Chcete-li určit Nehladový režim pro blok toku dat, nastavte <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> na `False`. Příklad, který ukazuje, jak použít nehladý režim pro povolení více spojovacích bloků pro efektivnější sdílení zdroje dat, naleznete v tématu [How to: use JoinBlock ke čtení dat z více zdrojů](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md).  
  
 [[Přejít na začátek](#top)]  
  
<a name="custom"></a>   
## <a name="custom-dataflow-blocks"></a>Vlastní bloky toku dat  
 I když knihovna TPL Dataflow poskytuje mnoho předdefinovaných typů bloku, můžete vytvořit další typy bloků, které provádějí vlastní chování. Implementujte rozhraní <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nebo <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> přímo nebo použijte metodu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> k sestavení komplexního bloku, který zapouzdřuje chování existujících typů bloků. Příklady, které ukazují, jak implementovat vlastní funkci bloku toku dat, naleznete v tématu [Návod: Vytvoření vlastního typu bloku toku](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)dat.  
  
 [[Přejít na začátek](#top)]  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Zápis zpráv do bloku toku dat a čtení zpráv z bloku toku dat](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md)|Ukazuje, jak psát zprávy do a číst zprávy z objektu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>.|  
|[Postupy: Implementace vzoru toku dat producent–příjemce](../../../docs/standard/parallel-programming/how-to-implement-a-producer-consumer-dataflow-pattern.md)|Popisuje, jak použít model toku dat pro implementaci vzoru producent-příjemce, kde producent posílá zprávy do bloku toku dat a příjemce čte zprávy z tohoto bloku.|  
|[Postupy: Provádění akcí po přijetí dat do bloku toku dat](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)|Popisuje, jak poskytnout delegáty pro spouštění typů bloku toku dat <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>.|  
|[Návod: Vytvoření kanálu toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)|V této části najdete popis postupu vytvoření kanálu toku dat, který stahuje text z webu a provádí operace s tímto textem.|  
|[Postupy: Zrušení propojení bloků toku dat](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)|Ukazuje, jak použít metodu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> k odpojení cílového bloku od zdroje poté, co zdroj nabídne zprávu cíli.|  
|[Návod: Použití toku dat v aplikaci Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)|Ukazuje, jak vytvořit síť bloků toku dat, které provádějí zpracování bitové kopie v aplikaci model Windows Forms.|  
|[Postupy: Zrušení bloku toku dat](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)|Ukazuje, jak použít zrušení v aplikaci model Windows Forms.|  
|[Postupy: Načítání dat z více zdrojů pomocí třídy JoinBlock](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)|Vysvětluje, jak použít třídu <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> k provedení operace, když jsou data k dispozici z více zdrojů a jak používat Nehladový režim k povolení sdílení zdroje dat více spojovacími bloky.|  
|[Postupy: Určení stupně paralelního zpracování v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)|Popisuje, jak nastavit vlastnost <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A>, aby umožňovala zpracování bloku toku dat spouštění více zpráv najednou.|  
|[Postupy: Určení plánovače úloh v bloku toku dat](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)|Ukazuje, jak přidružit konkrétní Plánovač úloh při použití toku dat ve vaší aplikaci.|  
|[Návod: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)|Popisuje, jak použít třídu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> ke zlepšení efektivity operací vložení databáze a způsobu použití třídy <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> k zachycení výsledků a všech výjimek, ke kterým dojde, když program načítá z databáze.|  
|[Návod: Vytvoření bloku toku dat vlastního typu](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)|Ukazuje dva způsoby vytvoření typu bloku toku dat, který implementuje vlastní chování.|  
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Zavádí TPL, knihovnu, která zjednodušuje paralelní a souběžné programování v aplikacích .NET Framework.|
