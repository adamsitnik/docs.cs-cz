---
title: 'Průvodce: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (C#)'
ms.date: 07/20/2015
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
ms.openlocfilehash: 20ed45b1796062973a1d4a9bcaa86782655d3867
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732697"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a><span data-ttu-id="a1254-102">Průvodce: Vložení informací o typu ze sestavení sady Microsoft Office v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="a1254-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="a1254-103">Je-li vložit informace o typu v aplikaci, která odkazuje na objekty modelu COM, můžete vyloučit potřebu primárního sestavení interop (PIA).</span><span class="sxs-lookup"><span data-stu-id="a1254-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="a1254-104">Kromě toho informace o typu embedded vám umožní dosáhnout nezávislosti na verzi pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a1254-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="a1254-105">To znamená váš program může zapisovat používat typy z více verzí knihovny COM bez nutnosti zvláštního PIA pro každou verzi.</span><span class="sxs-lookup"><span data-stu-id="a1254-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="a1254-106">Toto je běžný scénář pro aplikace, které používají objekty z knihoven Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="a1254-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="a1254-107">Vložení informací o typu umožňuje jednomu sestavení programu pracovat s různými verzemi sady Microsoft Office na různých počítačích bez nutnosti znovu nasazovat program nebo PIA pro každou verzi sady Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="a1254-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="a1254-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1254-108">Prerequisites</span></span>  
 <span data-ttu-id="a1254-109">Tento postup vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="a1254-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="a1254-110">Počítač, na kterém je nainstalováno Visual Studio a Microsoft Excelu.</span><span class="sxs-lookup"><span data-stu-id="a1254-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="a1254-111">Druhý počítač, na kterém je nainstalováno rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="a1254-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a> <span data-ttu-id="a1254-112">Chcete-li vytvořit aplikaci, která pracuje s více verzemi sady Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="a1254-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="a1254-113">Spusťte sadu Visual Studio na počítači, na kterém je nainstalována aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="a1254-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="a1254-114">Na **souboru** nabídce zvolte **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="a1254-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="a1254-115">V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="a1254-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="a1254-116">Vyberte **konzolovou aplikaci** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="a1254-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="a1254-117">V **název** zadejte `CreateExcelWorkbook`a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a1254-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="a1254-118">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="a1254-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="a1254-119">V **Průzkumníka řešení**, otevřete místní nabídku **odkazy** složky a klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="a1254-119">In **Solution Explorer**, open the shortcut menu for the **References** folder and then choose **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="a1254-120">Na **.NET** kartu, zvolte nejnovější verzi `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="a1254-120">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="a1254-121">Například **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="a1254-121">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="a1254-122">Zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a1254-122">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="a1254-123">V seznamu odkazů pro **CreateExcelWorkbook** projektu, vyberte odkaz pro `Microsoft.Office.Interop.Excel` , který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="a1254-123">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="a1254-124">V **vlastnosti** okno, ujistěte se, že `Embed Interop Types` je nastavena na `True`.</span><span class="sxs-lookup"><span data-stu-id="a1254-124">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1254-125">Aplikace vytvořené v tomto názorném postupu se spouští s různými verzemi sady Microsoft Office z důvodu informace o vloženém typu spolupráce.</span><span class="sxs-lookup"><span data-stu-id="a1254-125">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="a1254-126">Pokud `Embed Interop Types` je nastavena na `False`, musíte zahrnout PIA pro každou verzi sady Microsoft Office, která bude aplikace spuštěna s.</span><span class="sxs-lookup"><span data-stu-id="a1254-126">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="a1254-127">Otevřít **Program.cs** souboru.</span><span class="sxs-lookup"><span data-stu-id="a1254-127">Open the **Program.cs** file.</span></span> <span data-ttu-id="a1254-128">Nahraďte kód v souboru následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="a1254-128">Replace the code in the file with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.IO;  
    using Excel = Microsoft.Office.Interop.Excel;  
  
    namespace CreateExcelWorkbook  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                int[] values = {4, 6, 18, 2, 1, 76, 0, 3, 11};  
  
                CreateWorkbook(values, @"C:\SampleFolder\SampleWorkbook.xls");  
            }  
  
            static void CreateWorkbook(int[] values, string filePath)  
            {  
                Excel.Application excelApp = null;  
                Excel.Workbook wkbk;  
                Excel.Worksheet sheet;  
  
                try  
                {  
                        // Start Excel and create a workbook and worksheet.  
                        excelApp = new Excel.Application();  
                        wkbk = excelApp.Workbooks.Add();  
                        sheet = wkbk.Sheets.Add() as Excel.Worksheet;  
                        sheet.Name = "Sample Worksheet";  
  
                        // Write a column of values.  
                        // In the For loop, both the row index and array index start at 1.  
                        // Therefore the value of 4 at array index 0 is not included.  
                        for (int i = 1; i < values.Length; i++)  
                        {  
                            sheet.Cells[i, 1] = values[i];  
                        }  
  
                        // Suppress any alerts and save the file. Create the directory   
                        // if it does not exist. Overwrite the file if it exists.  
                        excelApp.DisplayAlerts = false;  
                        string folderPath = Path.GetDirectoryName(filePath);  
                        if (!Directory.Exists(folderPath))  
                        {  
                            Directory.CreateDirectory(folderPath);  
                        }  
                        wkbk.SaveAs(filePath);  
                }  
                catch  
                {  
                }  
                finally  
                {  
                    sheet = null;  
                    wkbk = null;  
  
                    // Close Excel.  
                    excelApp.Quit();  
                    excelApp = null;  
                }  
            }  
        }  
    }  
    ```  
  
8.  <span data-ttu-id="a1254-129">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="a1254-129">Save the project.</span></span>  
  
9. <span data-ttu-id="a1254-130">Stisknutím kláves CTRL + F5 sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="a1254-130">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="a1254-131">Ověřte, zda byl vytvořen sešit aplikace Excel v umístění zadaném v příkladu kódu: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="a1254-131">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a> <span data-ttu-id="a1254-132">K publikování aplikace na počítači, na kterém je nainstalovaná jiná verze systému Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="a1254-132">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="a1254-133">Otevřete projekt vytvořený v rámci tohoto návodu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a1254-133">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="a1254-134">Na **sestavení** nabídce zvolte **publikovat CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="a1254-134">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="a1254-135">Postupujte podle kroků v Průvodci publikováním vytvoření instalovatelnou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1254-135">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="a1254-136">Další informace najdete v tématu [Průvodce publikováním (vývoj pro Office v sadě Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="a1254-136">For more information, see [Publish Wizard (Office Development in Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).</span></span>  
  
3.  <span data-ttu-id="a1254-137">Nainstalujte aplikace na počítači, na kterém je nainstalováno rozhraní .NET Framework 4 nebo vyšší a jinou verzi aplikace Excel.</span><span class="sxs-lookup"><span data-stu-id="a1254-137">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="a1254-138">Po dokončení instalace spusťte nainstalovaný program.</span><span class="sxs-lookup"><span data-stu-id="a1254-138">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="a1254-139">Ověřte, zda byl vytvořen sešit aplikace Excel v umístění zadaném ve vzorovém kódu: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="a1254-139">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1254-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1254-140">See also</span></span>

- [<span data-ttu-id="a1254-141">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="a1254-141">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="a1254-142">/ Link (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a1254-142">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
