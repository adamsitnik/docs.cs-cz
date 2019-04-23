---
title: Používání třídy CodeActivity vytváření aktivit pracovního postupu
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 549acec8b8101312d48bd20e63a4a988b798ff38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767393"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>Používání třídy CodeActivity vytváření aktivit pracovního postupu
Aktivity vytvořené pomocí dědění z <xref:System.Activities.CodeActivity> základní imperativní chování můžete implementovat tak, že přepíšete <xref:System.Activities.CodeActivity.Execute%2A> metody.

## <a name="using-codeactivitycontext"></a>Pomocí CodeActivityContext
 Funkce modulu runtime pracovního postupu je přístupný z v rámci <xref:System.Activities.CodeActivity.Execute%2A> metoda pomocí členy `context` parametr typu <xref:System.Activities.CodeActivityContext>. Funkcí dostupných prostřednictvím <xref:System.Activities.CodeActivityContext> patří následující:

-   Získání a nastavení hodnoty proměnných a argumentů.

-   Vlastní sledování funkce pomocí <xref:System.Activities.CodeActivityContext.Track%2A>.

-   Přístup k vlastnostem spuštění aktivity pomocí <xref:System.Activities.CodeActivityContext.GetProperty%2A>.

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>Chcete-li vytvořit vlastní aktivitu, která dědí z třídy CodeActivity

1. Open Visual Studio 2010.

2. Vyberte **souboru**, **nové**a potom **projektu**. Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** okna a vyberte **v2010** uzlu. Vyberte **knihovny aktivit** v **šablony** okna. Název nového projektu HelloActivity.

3. Klikněte pravým tlačítkem na Activity1.xaml HelloActivity projektu a vyberte **odstranit**.

4. Klikněte pravým tlačítkem na projekt HelloActivity a vyberte **přidat** a potom **třídy**. Pojmenujte novou třídu HelloActivity.cs.

5. V souboru HelloActivity.cs, přidejte následující `using` direktivy.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. Ujistěte se, nová třída dědila z <xref:System.Activities.CodeActivity> přidáním základní třídu pro deklaraci třídy.

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. Přidání funkce do třídy tak, že přidáte <xref:System.Activities.CodeActivity.Execute%2A> metody.

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. Použití <xref:System.Activities.CodeActivityContext> vytvořit záznamem sledování.

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
