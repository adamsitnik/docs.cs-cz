---
title: 'Postupy: Programování pro Office (C# a Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
ms.openlocfilehash: d4a2562324259bda0bab523849449d584736b2ae
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423187"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>Postupy: Programování pro Office (C# a Visual Basic)

Visual Studio nabízí funkce v C# a Visual Basic, které zlepšují systém Microsoft Office programování. K C# užitečným funkcím patří pojmenované a nepovinné argumenty a návratové hodnoty typu `dynamic`. V programování modelu COM můžete vynechat klíčové slovo `ref` a získat přístup k indexovaným vlastnostem. Funkce v Visual Basic zahrnují automaticky implementované vlastnosti, příkazy ve výrazech lambda a Inicializátory kolekcí.

Oba jazyky umožňují vkládání informací o typu, což umožňuje nasazení sestavení, která komunikují s komponentami modelu COM bez nutnosti nasadit primární definiční sestavení (PIA) do počítače uživatele. Další informace naleznete v tématu [Návod: Vložení typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md).

Tento názorný postup ukazuje tyto funkce v kontextu programování v systému Office, ale mnoho z těchto funkcí je užitečné také při obecném programování. V tomto návodu použijete k vytvoření excelového sešitu aplikaci doplňku Excel. V dalším kroku vytvoříte dokument aplikace Word, který obsahuje odkaz na sešit. Nakonec uvidíte, jak povolit a zakázat závislost PIA.

## <a name="prerequisites"></a>Požadavky

Abyste mohli dokončit tento postup, musíte mít v počítači nainstalovanou aplikaci systém Microsoft Office Excel a systém Microsoft Office Word.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-set-up-an-excel-add-in-application"></a>Nastavení doplňku aplikace Excel

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

3. V podokně **Nainstalované šablony** rozbalte **Visual Basic** nebo **C#vizuál**, rozbalte **Office**a potom klikněte na rok verze produktu Office.

4. V podokně **šablony** klikněte na možnost **Excel \<version > doplňku**.

5. Podívejte se na horní část podokna **šablony** , abyste se ujistili, že se v poli **cílová architektura** zobrazí **.NET Framework 4**nebo novější verze.

6. Do pole **název** zadejte název projektu, pokud chcete.

7. Klikněte na tlačítko **OK**.

8. Nový projekt se zobrazí v **Průzkumník řešení**.

### <a name="to-add-references"></a>Přidání odkazů

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu a pak klikněte na **Přidat odkaz**. Zobrazí se dialogové okno **Přidat odkaz** .

2. Na kartě **sestavení** vyberte **Microsoft. Office. Interop. Excel**, verze `<version>.0.0.0` (pro klíč k číslům verze produktu Office, viz [verze Microsoft](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)), v seznamu **název součásti** a pak podržte klávesu CTRL a Vyberte **Microsoft. Office. Interop. Word**, `version <version>.0.0.0`. Pokud nevidíte sestavení, možná bude nutné zajistit, aby byly nainstalovány a zobrazovány (viz [Postup: instalace primárních sestavení vzájemné spolupráce pro systém Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).

3. Klikněte na tlačítko **OK**.

### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Přidání potřebných příkazů Imports nebo direktiv using

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor **ThisAddIn. vb** nebo **ThisAddIn.cs** a pak klikněte na **Zobrazit kód**.

2. Přidejte následující příkazy `Imports` (Visual Basic) nebo direktivy `using` (C#) na začátek souboru kódu, pokud již nejsou přítomny.

     [!code-csharp[csOfficeWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#1)]

     [!code-vb[csOfficeWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#1)]

### <a name="to-create-a-list-of-bank-accounts"></a>Vytvoření seznamu bankovních účtů

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu, klikněte na **Přidat**a potom klikněte na **Třída**. Pojmenujte třídu Account. vb, pokud používáte Visual Basic nebo Account.cs, pokud používáte C#. Klikněte na tlačítko **Přidat**.

2. Nahraďte definici `Account` třídy následujícím kódem. Definice tříd používají *automaticky implementované vlastnosti*. Další informace najdete v tématu věnovaném [automaticky implementovaným vlastnostem](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).

     [!code-csharp[csOfficeWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/account.cs#2)]

     [!code-vb[csOfficeWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/account.vb#2)]

3. Chcete-li vytvořit seznam `bankAccounts`, který obsahuje dva účty, přidejte následující kód do metody `ThisAddIn_Startup` v *ThisAddIn. vb* nebo *ThisAddIn.cs*. Deklarace seznamu používají *inicializátory kolekce*. Další informace najdete v tématu [inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

     [!code-csharp[csOfficeWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#3)]

     [!code-vb[csOfficeWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#3)]

### <a name="to-export-data-to-excel"></a>Export dat do aplikace Excel

1. Do stejného souboru přidejte následující metodu do třídy `ThisAddIn`. Metoda nastaví sešit aplikace Excel a exportuje do něj data.

     [!code-csharp[csOfficeWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#4)]

     [!code-vb[csOfficeWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#4)]

     V této C# metodě se používají dvě nové funkce. Obě tyto funkce již existují v Visual Basic.

    - Metoda [Add](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) má *volitelný parametr* pro určení konkrétní šablony. Volitelné parametry, novinka C# ve 4, umožňují vynechat argument pro tento parametr, pokud chcete použít výchozí hodnotu parametru. Vzhledem k tomu, že v předchozím příkladu není odeslán žádný argument, `Add` používá výchozí šablonu a vytvoří nový sešit. Ekvivalent příkazu v dřívějších verzích pro C# vyžaduje zástupný argument: `excelApp.Workbooks.Add(Type.Missing)`.

         Další informace naleznete v tématu [pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md).

    - Vlastnosti `Range` a `Offset` objektu [Range](<xref:Microsoft.Office.Interop.Excel.Range>) využívají funkci *indexovaných vlastností* . Tato funkce umožňuje využívání těchto vlastností z typů modelu COM pomocí následující typické C# syntaxe. Indexované vlastnosti umožňují také použít vlastnost `Value` objektu `Range` a eliminují nutnost použití vlastnosti `Value2`. Vlastnost `Value` je indexována, ale index je nepovinný. Nepovinné argumenty a indexované vlastnosti fungují společně v následujícím příkladu.

         [!code-csharp[csOfficeWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#5)]

         V dřívějších verzích jazyka je vyžadována následující speciální syntaxe.

         [!code-csharp[csOfficeWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#6)]

         Nemůžete vytvořit indexované vlastnosti, které vlastníte. Funkce podporuje jenom spotřebu stávajících indexovaných vlastností.

         Další informace najdete v tématu [Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md).

2. Přidejte následující kód na konec `DisplayInExcel` a upravte šířku sloupců tak, aby odpovídaly obsahu.

     [!code-csharp[csOfficeWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#7)]

     [!code-vb[csOfficeWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#7)]

     Tyto doplňky ukazují další funkci v C#systému: zpracovávání `Object` hodnot vrácených hostiteli com, jako je například sada Office, jako kdyby byly typu [dynamické](../../language-reference/builtin-types/reference-types.md). K tomu dochází automaticky při **Vložení typů spolupráce** do výchozí hodnoty, `True` nebo ekvivalentní, pokud je na sestavení odkazováno pomocí možnosti kompilátoru [-Link](../../language-reference/compiler-options/link-compiler-option.md) . Typ `dynamic` umožňuje pozdní vazbu, která je již k dispozici v Visual Basic a zabraňuje explicitnímu přetypování vyžadovanému v C# 3,0 a starších verzích jazyka.

     Například `excelApp.Columns[1]` vrátí `Object`a `AutoFit` je metoda [rozsahu](<xref:Microsoft.Office.Interop.Excel.Range>) aplikace Excel. Bez `dynamic`je nutné přetypování objektu vráceného `excelApp.Columns[1]` jako instance `Range` před voláním metody `AutoFit`.

     [!code-csharp[csOfficeWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#8)]

     Další informace o vkládání typů spolupráce naleznete v tématu procedury "Vyhledání odkazu PIA" a "obnovení závislosti PIA" dále v tomto tématu. Další informace o `dynamic` naleznete v tématu [dynamické](../../language-reference/builtin-types/reference-types.md) nebo [použití typu Dynamic](../types/using-type-dynamic.md).

### <a name="to-invoke-displayinexcel"></a>Pro vyvolání DisplayInExcel

1. Na konec metody `ThisAddIn_StartUp` přidejte následující kód. Volání `DisplayInExcel` obsahuje dva argumenty. První argument je název seznamu účtů, které se mají zpracovat. Druhý argument je víceřádkový výraz lambda definující způsob zpracování dat. Hodnoty `ID` a `balance` pro každý účet se zobrazí v sousedících buňkách a řádek se zobrazí červeně, pokud je zůstatek menší než nula. Další informace naleznete v tématu [lambda výrazy](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

     [!code-csharp[csOfficeWalkthrough#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#9)]

     [!code-vb[csOfficeWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#9)]

2. Chcete-li program spustit, stiskněte klávesu F5. Zobrazí se excelový list obsahující data z účtů.

### <a name="to-add-a-word-document"></a>Přidání dokumentu aplikace Word

1. Přidejte následující kód na konec metody `ThisAddIn_StartUp` pro vytvoření dokumentu aplikace Word, který obsahuje odkaz na excelový sešit.

     [!code-csharp[csOfficeWalkthrough#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#10)]

     [!code-vb[csOfficeWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#10)]

     Tento kód ukazuje několik nových funkcí v C#nástroji: schopnost vynechat klíčové slovo `ref` v programování com, pojmenované argumenty a volitelné argumenty. Tyto funkce již existují v Visual Basic. Metoda [PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) má sedm parametrů, přičemž všechny jsou definovány jako volitelné referenční parametry. Pojmenované a volitelné argumenty umožňují určit parametry, ke kterým chcete získat přístup podle názvu a odeslat argumenty pouze do těchto parametrů. V tomto příkladu jsou odesílány argumenty, které označují, že by měl být vytvořen odkaz na sešit ve schránce (parametr `Link`) a zda se má odkaz zobrazit v dokumentu aplikace Word jako ikona (`DisplayAsIcon` parametru). Vizuál C# také umožňuje vynechat klíčové slovo `ref` pro tyto argumenty.

### <a name="to-run-the-application"></a>Spuštění aplikace

1. Stisknutím klávesy F5 spusťte aplikaci. Aplikace Excel spustí a zobrazí tabulku, která obsahuje informace ze dvou účtů v `bankAccounts`. Pak se zobrazí dokument aplikace Word obsahující odkaz na excelovou tabulku.

### <a name="to-clean-up-the-completed-project"></a>Vyčištění dokončeného projektu

1. V aplikaci Visual Studio klikněte na možnost **Vyčistit řešení** v nabídce **sestavení** . V opačném případě se doplněk spustí pokaždé, když v počítači otevřete aplikaci Excel.

### <a name="to-find-the-pia-reference"></a>Vyhledání odkazu PIA

1. Spusťte aplikaci znovu, ale neklepejte na tlačítko **Vyčistit řešení**.

2. Vyberte **Spustit**. Vyhledejte **Microsoft Visual Studio \<version >** a otevřete příkazový řádek pro vývojáře.

3. Do okna Developer Command Prompt pro aplikaci Visual Studio zadejte `ildasm` a potom stiskněte klávesu ENTER. Zobrazí se okno IL DASM.

4. V nabídce **soubor** v okně DASM Il vyberte **soubor**  > **otevřít**. Dvakrát klikněte na **Visual Studio \<version >** a dvakrát klikněte na **projekty**. Otevřete složku pro váš projekt a vyhledejte složku bin/Debug pro *váš projekt název*. dll. Dvakrát klikněte na *název projektu*. dll. Nové okno zobrazuje atributy vašeho projektu, Kromě odkazů na jiné moduly a sestavení. Všimněte si, že obory názvů `Microsoft.Office.Interop.Excel` a `Microsoft.Office.Interop.Word` jsou zahrnuty v sestavení. Ve výchozím nastavení v aplikaci Visual Studio importuje kompilátor typy, které potřebujete, z odkazovaného PIA do sestavení.

     Další informace najdete v tématu [Postup: zobrazení obsahu sestavení](../../../standard/assembly/view-contents.md).

5. Dvakrát klikněte na ikonu **manifestu** . Zobrazí se okno obsahující seznam sestavení, která obsahují položky, na které se odkazuje v projektu. v seznamu nejsou zahrnuté `Microsoft.Office.Interop.Excel` a `Microsoft.Office.Interop.Word`. Vzhledem k tomu, že typy, které váš projekt potřebuje, byly importovány do sestavení, odkazy na PIA nejsou požadovány. Díky tomu je nasazení snazší. Nasazení PIA nemusí být k dispozici v počítači uživatele a protože aplikace nevyžaduje nasazení konkrétní verze služby PIA, aplikace může být navržena pro práci s více verzemi Office za předpokladu, že potřebná rozhraní API existují ve všech verzích. .

     Vzhledem k tomu, že nasazení PIA již není nutné, můžete vytvořit aplikaci v pokročilých scénářích, které fungují s více verzemi systému Office, včetně starších verzí. To ale funguje jenom v případě, že váš kód nepoužívá žádná rozhraní API, která nejsou k dispozici ve verzi Office, se kterou pracujete. V dřívější verzi není vždycky jasné, jestli konkrétní rozhraní API bylo dostupné, a z tohoto důvodu se nedoporučuje pracovat s předchozími verzemi Office.

    > [!NOTE]
    > Office nezveřejnil PIA před Office 2003. Proto jediným způsobem, jak vytvořit definiční sestavení pro Office 2002 nebo starší verze, je importování odkazu modelu COM.

6. Zavřete okno manifest a okno sestavení.

### <a name="to-restore-the-pia-dependency"></a>Obnovení závislosti PIA

1. V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** . Rozbalte složku **odkazy** a vyberte **Microsoft. Office. Interop. Excel**. Stisknutím klávesy F4 zobrazte okno **vlastnosti** .

2. V okně **vlastnosti** změňte vlastnost **Embed Interop Types** z **hodnoty true** na **false**.

3. Opakujte kroky 1 a 2 v tomto postupu pro `Microsoft.Office.Interop.Word`.

4. V C#nástroji Odkomentujte dvě volání `Autofit` na konci metody `DisplayInExcel`.

5. Stisknutím klávesy F5 ověřte, zda je projekt stále správně spuštěn.

6. Opakujte kroky 1-3 z předchozího postupu a otevřete tak okno sestavení. Všimněte si, že `Microsoft.Office.Interop.Word` a `Microsoft.Office.Interop.Excel` už nejsou v seznamu vložených sestavení.

7. Dvakrát klikněte na ikonu **manifestu** a procházejte seznamem odkazovaných sestavení. V seznamu jsou `Microsoft.Office.Interop.Word` i `Microsoft.Office.Interop.Excel`. Vzhledem k tomu, že se aplikace odkazuje na PIA v aplikacích Excel a Word a vlastnost **Embed Interop Types** je nastavena na **hodnotu false**, musí existovat obě sestavení v počítači koncového uživatele.

8. V aplikaci Visual Studio klikněte na možnost **Vyčistit řešení** v nabídce **sestavení** a vyčistěte dokončený projekt.

## <a name="see-also"></a>Viz také:

- [Automaticky implementované vlastnosti (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Automaticky implementované vlastnosti (C#)](../classes-and-structs/auto-implemented-properties.md)
- [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Inicializátory objektu a kolekce](../classes-and-structs/object-and-collection-initializers.md)
- [Nepovinné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Předávání argumentů podle pozice a názvu](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)
- [Pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md)
- [Statické a dynamické vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Použití typu dynamic](../types/using-type-dynamic.md)
- [Výrazy lambda (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Výrazy lambda (C#)](../statements-expressions-operators/lambda-expressions.md)
- [Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)
- [Návod: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ee317478(v%3dvs.120))
- [Návod: Vložení typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md)
- [Návod: Vytvoření prvního doplňku VSTO pro Excel](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)
- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Interoperabilita](./index.md)
