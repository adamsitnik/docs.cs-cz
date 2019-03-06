---
title: 'Asynchronní programování pomocí modifikátoru async a operátoru await (C#)'
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
---
# <a name="asynchronous-programming-with-async-and-await-c"></a>Asynchronní programování pomocí modifikátoru async a operátoru await (C#)
Pomocí asynchronního programování se můžete vyhnout kritickým bodům a zlepšit celkovou rychlost reakce aplikace. Tradiční techniky pro psaní asynchronních aplikací však mohou být složité, takže je obtížné je napsat, ladit a udržovat.  
  
[C# 5](../../../whats-new/csharp-version-history.md#c-version-50) zavedené zjednodušený přístup, asynchronní programování, který využívá asynchronní podpory v rozhraní .NET Framework 4.5 a vyšší, .NET Core a prostředí Windows Runtime. Kompilátor na sebe přejímá náročnou práci, kterou vykonával vývojář, a vaše aplikace si zachovává logickou strukturu, která se podobá synchronnímu kódu. Výsledkem je, že získáte všechny výhody asynchronního programování při pouhém zlomku úsilí.  
  
Toto téma obsahuje přehled kdy a jak použít asynchronní programování a obsahuje odkazy na témata podpory, která obsahují podrobné informace a příklady.  
  
## <a name="BKMK_WhentoUseAsynchrony"></a> Asynchronní programování zlepšuje odezvu  
 Asynchronie je nezbytná pro aktivity, které mohou potenciálně blokovat, jako je web Accessu. Přístup k webovému prostředku je někdy pomalý nebo zpožděný. Pokud je taková činnost blokována v synchronního procesu, musí čekat celá aplikace. U asynchronního procesu může aplikace pokračovat v další práci, která nezávisí na webovém prostředku, dokud neskončí potenciálně blokující úloha.  
  
 Následující tabulka ukazuje typické oblasti, kde asynchronní programování zlepšuje rychlost reakce. Uvedená rozhraní API z .NET a modulem Windows Runtime obsahují metody, které podporují asynchronní programování.  
  
| Oblast aplikace    | Typy .NET u asynchronních metod     | Typy modulu Windows Runtime s asynchronní metody  |
|---------------------|-----------------------------------|-------------------------------------------|
|Webový přístup|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Práce se soubory|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|  
|Práce s obrázky||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|  
|Programování WCF|[Synchronní a asynchronní operace](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||  
  
Asynchronie je obzvláště užitečná pro aplikace, které přistupují k vláknu UI, protože všechny aktivity související s uživatelským rozhraním obvykle sdílí jedno vlákno. Pokud je jakýkoli proces blokován v synchronní aplikaci, jsou blokovány všechny. Vaše aplikace přestane reagovat a můžete dojít k závěru, že selhala, i když místo toho čeká.  
  
 Při použití asynchronních metod bude aplikace i nadále odpovídat na uživatelské rozhraní. Pokud nechcete čekat na dokončení, můžete změnit velikost nebo minimalizovat okno, například můžete zavřít aplikaci.  
  
 Asynchronní přístup přidává ekvivalent automatického přenosu do seznamu možností, z nichž můžete vybírat při vytváření asynchronní operace. To znamená, že získáte všechny výhody tradičního asynchronního programování, ale s mnohem menším úsilím ze strany vývojáře.  
  
## <a name="BKMK_HowtoWriteanAsyncMethod"></a> Je snazší psát asynchronní metody  
 [Asynchronní](../../../../csharp/language-reference/keywords/async.md) a [await](../../../../csharp/language-reference/keywords/await.md) klíčová slova v jazyce C# jsou základem asynchronního programování. Pomocí těchto dvou klíčových slov můžete použít zdroje v rozhraní .NET Framework, .NET Core nebo prostředí Windows Runtime k vytvoření asynchronní metody téměř stejně snadno, jako vytváříte synchronní metody. Asynchronní metody, které definujete pomocí `async` – klíčové slovo se označují jako *asynchronní metody*.  
  
 Následující příklad ukazuje asynchronní metodu. Téměř vše v rámci kódu by vám mělo být zcela známé. Komentáře volají funkce, které jste přidali při tvorbě asynchronie.  
  
 Úplný ukázkový soubor Windows Presentation Foundation (WPF) na konci tohoto tématu můžete najít a si můžete stáhnout ukázku z [asynchronní vzorek: Příklad z "asynchronní programování pomocí modifikátoru Async a Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```csharp  
// Three things to note in the signature:  
//  - The method has an async modifier.   
//  - The return type is Task or Task<T>. (See "Return Types" section.)  
//    Here, it is Task<int> because the return statement returns an integer.  
//  - The method name ends in "Async."  
async Task<int> AccessTheWebAsync()  
{   
    // You need to add a reference to System.Net.Http to declare client.  
    using (HttpClient client = new HttpClient())  
    {  
        // GetStringAsync returns a Task<string>. That means that when you await the  
        // task you'll get a string (urlContents).  
        Task<string> getStringTask = client.GetStringAsync("https://docs.microsoft.com");  
  
        // You can do work here that doesn't rely on the string from GetStringAsync.  
        DoIndependentWork();  
  
        // The await operator suspends AccessTheWebAsync.  
        //  - AccessTheWebAsync can't continue until getStringTask is complete.  
        //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
        //  - Control resumes here when getStringTask is complete.   
        //  - The await operator then retrieves the string result from getStringTask.  
        string urlContents = await getStringTask;  
  
        // The return statement specifies an integer result.  
        // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
        return urlContents.Length;  
    }  
}  
```  
  
 Pokud `AccessTheWebAsync` nemá žádnou práci, kterou lze provádět mezi voláním `GetStringAsync` a čekáním na její dokončení, můžete zjednodušit kód voláním a čekáním následujícím jediným příkazem.  
  
```csharp  
string urlContents = await client.GetStringAsync("https://docs.microsoft.com");  
```  
 
Následující charakteristiky představují shrnutí, co dělá předchozí příklad asynchronní metodou.  
  
-   Podpis metody zahrnuje `async` modifikátor.  
  
-   Název asynchronní metody končí podle konvence příponou „Async“.  
  
-   Návratový typ je jeden z následujících typů:  
  
    -   <xref:System.Threading.Tasks.Task%601> Pokud vaše metoda disponuje návratovým příkazem, ve kterém je operand typu `TResult`.  
  
    -   <xref:System.Threading.Tasks.Task> Pokud vaše metoda nemá návratový stav nebo vrátila příkaz bez operandu.  
  
    -   `void` Pokud píšete asynchronní obslužnou rutinu události.  

    -   Typ, který má `GetAwaiter` – metoda (od verze C# 7.0).
  
     Další informace najdete v tématu [vrátí typy a parametry](#BKMK_ReturnTypesandParameters) oddílu.  
  
-   Metoda obvykle zahrnuje nejméně jeden očekávaný výraz, který označuje bod, kde metoda nemůže pokračovat, dokud očekávaná asynchronní operace nebude dokončena. Během této doby je metoda pozastavena a ovládací prvek se vrátí volajícímu metody. Další část tohoto tématu ukazuje, co se stane v okamžiku pozastavení.  
  
 V asynchronních metodách používáte zadaná klíčová slova a typy pro označení, jakou akci chcete provést, a kompilátor udělá zbytek, včetně udržování přehledu o tom, co musí nastat, když se řízení vrátí do bodu „await“ pozastavené metody. Některé běžné procesy, jako je zpracování smyček a výjimek, může být v tradičním asynchronním kódu obtížné zpracovat. V asynchronní metodě zapisujete tyto prvky podobně, jako byste to udělali v synchronním řešení, a problém je vyřešen.  
  
 Další informace o asynchronii v předchozích verzích rozhraní .NET Framework najdete v tématu [TPL a tradiční rozhraní .NET Framework Asynchronous Programming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Co se děje v asynchronní metodě  
 Nejdůležitějším principem, který je třeba pochopit v asynchronním programování, je, jak ovládat přesuny toků od metody k metodě. Následující diagram vás provede procesem.  
  
 ![Trasování aplikace asynchronní](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Čísla v diagramu odpovídají následujícím krokům.  
  
1.  Obslužná rutina události zavolá a očekává `AccessTheWebAsync` asynchronní metody.  
  
2.  `AccessTheWebAsync` vytvoří <xref:System.Net.Http.HttpClient> instance a volání <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronní metody ke stahování obsahu webu jako řetězec.  
  
3.  Něco se stane v `GetStringAsync` , která způsobí zastavení průběhu. Možná je třeba vyčkat na dokončení stahování nebo jiné blokující aktivity na webu. Chcete-li zabránit zablokování, `GetStringAsync` vrací řízení volajícímu, `AccessTheWebAsync`.  
  
     `GetStringAsync` Vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je řetězec, a `AccessTheWebAsync` přiřadí úlohu `getStringTask` proměnné. Úloha představuje trvalý proces pro volání `GetStringAsync`, se závazkem vyrábět aktuální řetězcovou hodnotu po dokončení práce.  
  
4.  Protože `getStringTask` ještě nebyla očekávána, metoda `AccessTheWebAsync` můžete pokračovat v další práci, která nezávisí na konečném výsledku `GetStringAsync`. Daná práce je reprezentována voláním synchronní metody `DoIndependentWork`.  
  
5.  `DoIndependentWork` je synchronní metoda, která provede svou práci a vrátí výsledek volajícímu.  
  
6.  `AccessTheWebAsync` nemá dostatek práce, kterou můžete provést bez výsledku z `getStringTask`. `AccessTheWebAsync` dále potřebuje vypočítat a vrátit délku staženého řetězce, ale metoda nemůže hodnotu vypočítat, dokud se tato metoda má řetězec.  
  
     Proto `AccessTheWebAsync` používá operátor await k pozastavení jeho průběhu a výnosu z ovládacího prvku v metodě, která volá `AccessTheWebAsync`. `AccessTheWebAsync` Vrátí `Task<int>` volajícímu. Úloha představuje slib vyrábět celé číslo výsledku, který má délku staženého řetězce.  
  
    > [!NOTE]
    >  Pokud `GetStringAsync` (a tedy `getStringTask`) dokončena dříve, než `AccessTheWebAsync` čeká na jeho ovládací prvek zůstane v `AccessTheWebAsync`. Prostředky na zastavení a vrácení k `AccessTheWebAsync` by byly ztraceny, pokud volaný asynchronní proces (`getStringTask`) již dokončen a `AccessTheWebSync` nebude muset čekat na konečný výsledek.  
  
     Uvnitř volajícího (v tomto případě obslužná rutina události) bude vzor zpracování pokračovat. Volající může provádět další operace, které nejsou závislé na výsledku `AccessTheWebAsync` před čeká na výsledek, nebo volající může použít funkci await okamžitě.   Obslužná rutina události čeká na všesměrově `AccessTheWebAsync`, a `AccessTheWebAsync` čeká `GetStringAsync`.  
  
7.  `GetStringAsync` dokončí a vytvoří výsledek řetězce. Výsledek řetězce není vrácený voláním na `GetStringAsync` způsobem, který by se dalo očekávat. (Mějte na paměti, že metoda již vrátila úlohu v kroku 3.) Místo toho je výsledek řetězce uložen v úkolu, který představuje dokončení metody, `getStringTask`. Operátor await načítá výsledek z `getStringTask`. Přiřazovací příkaz přiřadí načtený výsledek do `urlContents`.  
  
8.  Když `AccessTheWebAsync` má řetězec výsledek, metoda může vypočítat délku řetězce. Pak je práce `AccessTheWebAsync` kompletní a můžete pokračovat v obslužné rutině události čekání. V úplném příkladu na konci tématu si můžete potvrdit, že obslužná rutina události načte a vytiskne hodnotu výsledné délky.    
Pokud jste v oblasti asynchronního programování nováčky, zvažte rozdíl mezi synchronním a asynchronním chováním. Synchronní metoda je vrácena, jakmile je její práce dokončena (krok 5), ale asynchronní metoda vrátí hodnotu úlohy, když je její práce pozastavena (kroky 3 a 6). Když asynchronní metoda nakonec dokončí svou práci, je úloha označena jako dokončená a výsledek, pokud existuje, je uložen v úloze.  
  
Další informace o toku řízení naleznete v tématu [tok řízení v asynchronních programech (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="BKMK_APIAsyncMethods"></a> Asynchronní metody rozhraní API  
 Možná se ptáte kde nalézt metody jako `GetStringAsync` , které podporují asynchronní programování. Rozhraní .NET Framework 4.5 nebo vyšší a .NET Core obsahují mnoho členů, které pracují s `async` a `await`. Můžete rozpoznat podle přípony "Async", která se připojuje k názvu člena a podle jejich návratového typu <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Například `System.IO.Stream` třída obsahuje metody, jako například <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, a <xref:System.IO.Stream.WriteAsync%2A> vedle synchronních metod <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, a <xref:System.IO.Stream.Write%2A>.  
  
 Modul Runtime Windows také obsahuje mnoho metod, které můžete použít s `async` a `await` v aplikacích pro Windows. Další informace najdete v tématu [asynchronní programování a zřetězení](/windows/uwp/threading-async/) pro vývoj pro UPW, a [asynchronní programování (aplikace pro Windows Store)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) a [rychlý start: Volání asynchronního rozhraní API C# nebo Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) Pokud používáte starší verze prostředí Windows Runtime.  
  
## <a name="BKMK_Threads"></a> Vlákna  
Asynchronní metody mají být neblokující operace. `await` Výrazu v asynchronní metodě nebude blokovat aktuální vlákno, zatímco očekávaná úloha běží. Namísto toho se výraz zaregistruje pro zbývající metody jako pokračování a vrátí řízení volajícímu asynchronní metody.  
  
`async` a `await` klíčová slova nezpůsobí další vlákna, který se má vytvořit. Asynchronní metody nevyžadují multithreading, protože asynchronní metoda není spuštěna ve vlastním vlákně. Metoda pracuje na aktuálním kontextu synchronizace a používá čas ve vlákně pouze v případě, že je metoda aktivní. Můžete použít <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> pro přesun práce vázané na procesor do vlákna na pozadí, ale na pozadí vlákno nepomůže s procesem, který pouze čeká na zpřístupnění výsledků.  
  
Asynchronní přístup při asynchronním programování se doporučuje v téměř každém případě existujících přístupů. Konkrétně tento přístup je obecně lepší než <xref:System.ComponentModel.BackgroundWorker> třídy pro vstupně-výstupní operace vzhledem k tomu, že kód je jednodušší a nemusíte pomáhalo chránit před časování. V kombinaci s <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metoda, je asynchronní programování lepší než <xref:System.ComponentModel.BackgroundWorker> pro operace vázané na procesor protože asynchronní programování odděluje koordinaci podrobností od spouštění kódu z práce, která `Task.Run` přenese fondu vláken.  
  
## <a name="BKMK_AsyncandAwait"></a> Async a operátoru await  
 Pokud určíte, že metoda je metodou asynchronní pomocí [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor, povolíte tím následující dvě možnosti.  
  
-   Označená asynchronní metoda může použít [await](../../../../csharp/language-reference/keywords/await.md) k určení místa pozastavení možnost. `await` Operátor sděluje kompilátoru, že asynchronní metoda nemůže pokračovat za tímto bodem, dokud nebude dokončen očekávaný asynchronní proces. Během této doby se ovládací prvek vrátí volajícímu asynchronní metody.  
  
     Pozastavení asynchronní metody na `await` výraz nebude představovat východ z metody, a `finally` bloky při spuštění.  
  
-   Samotná označená asynchronní metoda může být očekávána metodami, které ji volaly.  
  
Asynchronní metoda obvykle obsahuje jeden nebo více výskytů `await` operátoru, ale absence `await` výrazy nezpůsobí chybu kompilátoru. Pokud asynchronní metoda nepoužívá `await` operátor označení bodu pozastavení, metoda provede jako synchronní metoda funguje, bez ohledu `async` modifikátor. Kompilátor u takových metod zahlásí upozornění.  
  
 `async` a `await` jsou kontextová klíčová slova. Další informace a příklady naleznete v následujících tématech:  
  
-   [async](../../../../csharp/language-reference/keywords/async.md)  
  
-   [await](../../../../csharp/language-reference/keywords/await.md)  
  
## <a name="BKMK_ReturnTypesandParameters"></a> Typy vrácených hodnot a parametrů  
Asynchronní metoda obvykle vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. V asynchronní metodě `await` operátor je použít pro úlohu, která je vrácena z volání do jiné asynchronní metody.  
  
Zadáte <xref:System.Threading.Tasks.Task%601> jako návratový typ, pokud metoda obsahuje [vrátit](../../../../csharp/language-reference/keywords/return.md) příkaz, který určuje typ operandu `TResult`. 
  
Použijete <xref:System.Threading.Tasks.Task> jako návratový typ, pokud metoda nemá žádný návratový příkaz nebo má návratový příkaz, který nevrací operand.  

Od verze C# 7.0, můžete také zadat jiné návratovým typem, za předpokladu, že obsahuje typ `GetAwaiter` metody. <xref:System.Threading.Tasks.ValueTask%601> je příkladem takového typu. Je k dispozici [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) balíček NuGet.
  
 Následující příklad ukazuje, jak deklarovat a volat metodu, která se vrátí <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>.  
  
```csharp  
// Signature specifies Task<TResult>  
async Task<int> GetTaskOfTResultAsync()  
{  
    int hours = 0;  
    await Task.Delay(0);  
    // Return statement specifies an integer result.  
    return hours;  
}  
  
// Calls to GetTaskOfTResultAsync  
Task<int> returnedTaskTResult = GetTaskOfTResultAsync();  
int intResult = await returnedTaskTResult;  
// or, in a single statement  
int intResult = await GetTaskOfTResultAsync();  
  
// Signature specifies Task  
async Task GetTaskAsync()  
{  
    await Task.Delay(0);  
    // The method has no return statement.    
}  
  
// Calls to GetTaskAsync  
Task returnedTask = GetTaskAsync();  
await returnedTask;  
// or, in a single statement  
await GetTaskAsync();  
```  
  
Každá vrácená úloha představuje probíhající práci. Úloha zapouzdřuje informace o stavu asynchronního procesu a posléze buď konečný výsledek z procesu, nebo výjimku, kterou proces vyvolá v případě neúspěchu.  
  
Asynchronní metoda může mít také `void` návratového typu. Tento typ vrácení se používá především k definování obslužných rutin událostí, kde `void` návratový typ je povinný. Asynchronní obslužné rutiny událostí často slouží jako výchozí bod pro asynchronní programy.  
  
Asynchronní metoda, která má `void` vrátit typ nemůže být očekávána a volající metody vracející typ void nemůže zachytit žádné výjimky, které metoda vyvolá.  
  
Asynchronní metoda nemůže deklarovat [v](../../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, ale metoda může volat metody, které mají tyto parametry. Asynchronní metoda podobně, nemůže vracet hodnotu odkazem, i když může volat metody s ref návratové hodnoty. 
  
Další informace a příklady najdete v tématu [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md). Další informace o tom, jak zachytávat výjimky v asynchronních metodách, naleznete v tématu [bloku try-catch](../../../../csharp/language-reference/keywords/try-catch.md). 
  
Asynchronní rozhraní API v programování v prostředí Windows Runtime některou z následujících návratových typů, které jsou podobné úkolům:  
  
-   <xref:Windows.Foundation.IAsyncOperation%601>, který odpovídá <xref:System.Threading.Tasks.Task%601>  
  
-   <xref:Windows.Foundation.IAsyncAction>, který odpovídá <xref:System.Threading.Tasks.Task>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
   
  
## <a name="BKMK_NamingConvention"></a> Zásady vytváření názvů  
Podle konvence, metody, které vracejí běžně očekávatelný typů (například `Task`, `Task<T>`, `ValueTask`, `ValueTask<T>`) by měly mít názvy, které končí řetězcem "Async". Metody, které začít asynchronní operaci, ale nevrátí očekávatelný typ by neměly mít názvy, které končí "Async", ale může začínat "Begin", "Start" nebo některé operace navrhnout tato metoda vrátí nebo vyvolat výsledek operace.
  
 Můžete ignorovat konvenci, kde událost, základní třída a rozhraní smlouvy navrhují odlišný název. Například byste neměli přejmenovat běžné obslužné rutiny událostí, jako například `Button1_Click`.  
  
## <a name="BKMK_RelatedTopics"></a> Související témata a ukázky (Visual Studio)  
  
|Název|Popis|Ukázka|  
|-----------|-----------------|------------|  
|[Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Ukazuje, jak převést synchronní řešení WPF na asynchronní řešení WPF. Aplikace stáhne řadu webových stránek.|[Ukázka asynchronní metody: Přístup k webovému návodu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[Postupy: Rozšíření návodu úloh pomocí metody Task.whenall asynchronních (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Přidá <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> k předchozímu návodu. Použití `WhenAll` zahájí všechna stahování současně.||  
|[Postupy: Paralelní provádění vícenásobných webových pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ukazuje, jak spustit několik úloh současně.|[Ukázka asynchronní metody: Paralelní provádění vícenásobných webových](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[Asynchronní návratové typy (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)|Znázorňuje typy, které může vrátit asynchronní metoda, a vysvětluje, kdy se každý typ hodí.||  
|[Tok řízení v asynchronních programech (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)|Podrobně sleduje tok řízení pomocí sledu očekávání výrazů v asynchronním programu.|[Ukázka asynchronní metody: Tok řízení v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[Doladění aplikace s modifikátorem Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Ukazuje, jak přidat k asynchronnímu řešení následující funkce:<br /><br /> -   [Zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Zrušení asynchronních úloh po určitou dobu (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Zrušení zbývajících asynchronních úloh po dokončení (C#) jedné z nich](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Ukázka asynchronní metody: Vyladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[Podpora vícenásobného přístupu v aplikacích s modifikátorem Async (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Ukazuje, jak zpracovat případy, ve kterých je aktivní asynchronní operace restartována po jejím spuštění.||  
|[WhenAny: Přemostění rozhraní .NET Framework a prostředí Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Ukazuje, jak propojit typy úloh v rozhraní .NET Framework a iasyncoperations v rámci [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby vám <xref:System.Threading.Tasks.Task.WhenAny%2A> s [!INCLUDE[wrt](~/includes/wrt-md.md)] metoda.|[Ukázka asynchronní metody: Přemostění mezi rozhraním .NET a prostředí Windows Runtime (AsTask a WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|  
|Asynchronní zrušení: Přemostění rozhraní .NET Framework a prostředí Windows Runtime|Ukazuje, jak propojit typy úloh v rozhraní .NET Framework a iasyncoperations v rámci [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby vám <xref:System.Threading.CancellationTokenSource> s [!INCLUDE[wrt](~/includes/wrt-md.md)] metoda.|[Ukázka asynchronní metody: Přemostění mezi rozhraním .NET a prostředí Windows Runtime (AsTask a zrušení)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[Použití modifikátoru Async pro přístup k souborům (C#)](../../../../csharp/programming-guide/concepts/async/using-async-for-file-access.md)|Seznam a ukázka výhod použití operátorů async a await při přístupu k souborům.||  
|[Asynchronní vzor založený na úlohách (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Popisuje nový vzor pro asynchronii v rozhraní .NET Framework. Vzorek je založen na <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> typy.||  
|[Videa o asynchronním programování na kanálu Channel 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Poskytuje odkazy na různá videa o asynchronním programování.||  
  
## <a name="BKMK_CompleteExample"></a> Kompletní příklad  
 Následující kód je soubor MainWindow.xaml.cs z aplikace Windows Presentation Foundation (WPF), která toto téma popisuje. Můžete stáhnout ukázku z [asynchronní vzorek: Příklad z "asynchronní programování pomocí modifikátoru Async a Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http;  
using System.Net.Http;  
  
namespace AsyncFirstExample  
{  
    public partial class MainWindow : Window  
    {  
        // Mark the event handler with async so you can use await in it.  
        private async void StartButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Call and await separately.  
            //Task<int> getLengthTask = AccessTheWebAsync();  
            //// You can do independent work here.  
            //int contentLength = await getLengthTask;  
  
            int contentLength = await AccessTheWebAsync();  
  
            resultsTextBox.Text +=
                $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }  
  
        // Three things to note in the signature:  
        //  - The method has an async modifier.   
        //  - The return type is Task or Task<T>. (See "Return Types" section.)  
        //    Here, it is Task<int> because the return statement returns an integer.  
        //  - The method name ends in "Async."  
        async Task<int> AccessTheWebAsync()  
        {   
            // You need to add a reference to System.Net.Http to declare client.  
            using (HttpClient client = new HttpClient())  
            {  
                    // GetStringAsync returns a Task<string>. That means that when you await the  
                    // task you'll get a string (urlContents).  
                    Task<string> getStringTask = client.GetStringAsync("https://docs.microsoft.com");  
  
                    // You can do work here that doesn't rely on the string from GetStringAsync.  
                    DoIndependentWork();  
  
                    // The await operator suspends AccessTheWebAsync.  
                    //  - AccessTheWebAsync can't continue until getStringTask is complete.  
                    //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
                    //  - Control resumes here when getStringTask is complete.   
                    //  - The await operator then retrieves the string result from getStringTask.  
                    string urlContents = await getStringTask;  
  
                    // The return statement specifies an integer result.  
                    // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
                    return urlContents.Length;  
            }  
        }  
  
        void DoIndependentWork()  
        {  
            resultsTextBox.Text += "Working . . . . . . .\r\n";  
        }  
    }  
}  
  
// Sample Output:  
  
// Working . . . . . . .  
  
// Length of the downloaded string: 25035.  
```  
  
## <a name="see-also"></a>Viz také:

- [async](../../../../csharp/language-reference/keywords/async.md)
- [await](../../../../csharp/language-reference/keywords/await.md)
- [Asynchronní programování](../../../../csharp/async.md)
- [Přehled asynchronních](../../../../standard/async.md)
