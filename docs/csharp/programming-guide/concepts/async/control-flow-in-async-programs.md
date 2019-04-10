---
title: Tok řízení v asynchronních programech (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 6a7b8f3f41b2096e3e7524d03217bdc123f26f10
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326200"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="7857b-102">Tok řízení v asynchronních programech (C#)</span><span class="sxs-lookup"><span data-stu-id="7857b-102">Control flow in async programs (C#)</span></span>

<span data-ttu-id="7857b-103">Můžete napsat a snadněji udržovat asynchronní programy pomocí `async` a `await` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="7857b-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="7857b-104">Ale výsledků možná vás překvapí Pokud nevíte, jak program pracuje.</span><span class="sxs-lookup"><span data-stu-id="7857b-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="7857b-105">Toto téma sleduje tok řízení prostřednictvím jednoduchého asynchronního programu k zobrazení, když se ovládací prvek přesune z jedné metody na jinou a jaké informace jsou pokaždé přeneseny.</span><span class="sxs-lookup"><span data-stu-id="7857b-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="7857b-106">Obecně označujete metody, které obsahují asynchronní kód s [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="7857b-106">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="7857b-107">V metodě, která je označena asynchronním modifikátorem, můžete použít [await (C#)](../../../../csharp/language-reference/keywords/await.md) operátor k určení, kde Metoda počká na dokončení volaného asynchronního procesu.</span><span class="sxs-lookup"><span data-stu-id="7857b-107">In a method that's marked with an async modifier, you can use an [await (C#)](../../../../csharp/language-reference/keywords/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="7857b-108">Další informace najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="7857b-108">For more information, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="7857b-109">Následující příklad používá asynchronní metody ke stahování obsahu zadaného webu jako řetězec a zobrazí délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="7857b-109">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="7857b-110">Tento příklad obsahuje následující dvě metody.</span><span class="sxs-lookup"><span data-stu-id="7857b-110">The example contains the following two methods.</span></span>

-   `startButton_Click`<span data-ttu-id="7857b-111">, který volá `AccessTheWebAsync` a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="7857b-111">, which calls `AccessTheWebAsync` and displays the result.</span></span>

-   `AccessTheWebAsync`<span data-ttu-id="7857b-112">, který stáhne obsah webu jako řetězec a vrátí délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="7857b-112">, which downloads the contents of a website as a string and returns the length of the string.</span></span> `AccessTheWebAsync` <span data-ttu-id="7857b-113">používá asynchronní <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, chcete-li stáhnout obsah.</span><span class="sxs-lookup"><span data-stu-id="7857b-113">uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="7857b-114">Číslované řádky se zobrazí strategická místa v celém programu, které vám pomohou pochopit, jak program funguje a co se stane v každém bodu, který je označen jako zobrazení.</span><span class="sxs-lookup"><span data-stu-id="7857b-114">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="7857b-115">Zobrazené řádky jsou označeny "Jedna"až "šest."</span><span class="sxs-lookup"><span data-stu-id="7857b-115">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="7857b-116">Popisky představují pořadí, ve kterém dosáhne program tyto řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="7857b-116">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="7857b-117">Následující kód ukazuje osnovu třídy program.</span><span class="sxs-lookup"><span data-stu-id="7857b-117">The following code shows an outline of the program.</span></span>

```csharp
public partial class MainWindow : Window
{
    // . . .
    private async void startButton_Click(object sender, RoutedEventArgs e)
    {
        // ONE
        Task<int> getLengthTask = AccessTheWebAsync();

        // FOUR
        int contentLength = await getLengthTask;

        // SIX
        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {contentLength}.\r\n";
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("https://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

<span data-ttu-id="7857b-118">Každé z označených míst "Jedna"až "šest" zobrazí informace o aktuálním stavu programu.</span><span class="sxs-lookup"><span data-stu-id="7857b-118">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="7857b-119">Následující výstup je vytvořen:</span><span class="sxs-lookup"><span data-stu-id="7857b-119">The following output is produced:</span></span>

```text
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a><span data-ttu-id="7857b-120">Vytvoření programu</span><span class="sxs-lookup"><span data-stu-id="7857b-120">Set up the program</span></span>

<span data-ttu-id="7857b-121">Kód, který se používá v tomto tématu si můžete stáhnout z webu MSDN nebo si ho můžete vytvořit sami.</span><span class="sxs-lookup"><span data-stu-id="7857b-121">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="7857b-122">Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="7857b-122">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="7857b-123">Stáhnout program</span><span class="sxs-lookup"><span data-stu-id="7857b-123">Download the program</span></span>

<span data-ttu-id="7857b-124">Můžete stáhnout aplikaci pro toto téma z [asynchronní vzorek: Řízení toku v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="7857b-124">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="7857b-125">Následující postup otevře a spustí program.</span><span class="sxs-lookup"><span data-stu-id="7857b-125">The following steps open and run the program.</span></span>

1. <span data-ttu-id="7857b-126">Rozbalte stažený soubor a poté spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7857b-126">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="7857b-127">V panelu nabídky zvolte **souboru** > **otevřít** > **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="7857b-127">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="7857b-128">Přejděte do složky obsahující dekomprimovaný ukázkový kód, otevřete soubor řešení (.sln) a klikněte na tlačítko **F5** klíče pro sestavení a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="7857b-128">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="7857b-129">Vytvoření programu</span><span class="sxs-lookup"><span data-stu-id="7857b-129">Create the program Yourself</span></span>

<span data-ttu-id="7857b-130">Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="7857b-130">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="7857b-131">Spusťte projekt, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="7857b-131">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="7857b-132">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7857b-132">Start Visual Studio.</span></span>

2. <span data-ttu-id="7857b-133">V panelu nabídky zvolte **souboru** > **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="7857b-133">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="7857b-134">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7857b-134">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="7857b-135">Zvolte **nainstalováno** > **Visual C#** > **Windows Desktop** kategorie a klikněte na tlačítko **aplikace WPF** ze seznamu šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="7857b-135">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="7857b-136">Zadejte `AsyncTracer` jako název projektu a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7857b-136">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="7857b-137">Nový projekt se zobrazí v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="7857b-137">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="7857b-138">V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.</span><span class="sxs-lookup"><span data-stu-id="7857b-138">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="7857b-139">Pokud karta není zobrazena, otevřete místní nabídku souboru mainwindow.XAML v **Průzkumníka řešení**a klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="7857b-139">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="7857b-140">V **XAML** zobrazení souboru mainwindow.XAML, nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="7857b-140">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```csharp
    <Window
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="AsyncTracer.MainWindow"
            Title="Control Flow Trace" Height="350" Width="592">
        <Grid>
            <Button x:Name="startButton" Content="Start
    " HorizontalAlignment="Left" Margin="250,10,0,0" VerticalAlignment="Top" Width="75" Height="24"  Click="startButton_Click" d:LayoutOverrides="GridBox"/>
            <TextBox x:Name="resultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="576" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" Grid.ColumnSpan="3"/>
        </Grid>
    </Window>
    ```

     <span data-ttu-id="7857b-141">Jednoduché okno obsahující textové pole a tlačítko se zobrazí v **návrhu** zobrazení souboru MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="7857b-141">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="7857b-142">Přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="7857b-142">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="7857b-143">V **Průzkumníka řešení**, otevřete místní nabídku pro MainWindow.xaml.cs a pak zvolte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="7857b-143">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="7857b-144">V MainWindow.xaml.cs nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="7857b-144">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

    namespace AsyncTracer
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                InitializeComponent();
            }

            private async void startButton_Click(object sender, RoutedEventArgs e)
            {
                // The display lines in the example lead you through the control shifts.
                resultsTextBox.Text += "ONE:   Entering startButton_Click.\r\n" +
                    "           Calling AccessTheWebAsync.\r\n";

                Task<int> getLengthTask = AccessTheWebAsync();

                resultsTextBox.Text += "\r\nFOUR:  Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is started.\r\n" +
                    "           About to await getLengthTask -- no caller to return to.\r\n";

                int contentLength = await getLengthTask;

                resultsTextBox.Text += "\r\nSIX:   Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is finished.\r\n" +
                    "           Result from AccessTheWebAsync is stored in contentLength.\r\n" +
                    "           About to display contentLength and exit.\r\n";

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");

                resultsTextBox.Text += "\r\nTHREE: Back in AccessTheWebAsync.\r\n" +
                    "           Task getStringTask is started.";

                // AccessTheWebAsync can continue to work until getStringTask is awaited.

                resultsTextBox.Text +=
                    "\r\n           About to await getStringTask and return a Task<int> to startButton_Click.\r\n";

                // Retrieve the website contents when task is complete.
                string urlContents = await getStringTask;

                resultsTextBox.Text += "\r\nFIVE:  Back in AccessTheWebAsync." +
                    "\r\n           Task getStringTask is complete." +
                    "\r\n           Processing the return statement." +
                    "\r\n           Exiting from AccessTheWebAsync.\r\n";

                return urlContents.Length;
            }
        }
    }
    ```

10. <span data-ttu-id="7857b-145">Zvolte **F5** klíče ke spuštění programu a klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7857b-145">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="7857b-146">Zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7857b-146">The following output appears:</span></span>

    ```text
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a><span data-ttu-id="7857b-147">Trasování programu</span><span class="sxs-lookup"><span data-stu-id="7857b-147">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="7857b-148">Kroky 1 a 2</span><span class="sxs-lookup"><span data-stu-id="7857b-148">Steps ONE and TWO</span></span>

<span data-ttu-id="7857b-149">První dva zobrazené řádky sledují cestu jako `startButton_Click` volání `AccessTheWebAsync`, a `AccessTheWebAsync` volá asynchronní <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="7857b-149">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="7857b-150">Následující obrázek popisuje volání z metody do metody.</span><span class="sxs-lookup"><span data-stu-id="7857b-150">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="7857b-151">![Kroky 1 a 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="7857b-151">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="7857b-152">Návratový typ obou `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="7857b-152">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="7857b-153">Pro `AccessTheWebAsync`, je TResult celé číslo.</span><span class="sxs-lookup"><span data-stu-id="7857b-153">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="7857b-154">Pro `GetStringAsync`, TResult je řetězec.</span><span class="sxs-lookup"><span data-stu-id="7857b-154">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="7857b-155">Další informace o asynchronních návratových typech metod naleznete v tématu [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="7857b-155">For more information about async method return types, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>

<span data-ttu-id="7857b-156">Asynchronní metody vracející úlohy vrátí instance úlohy, když ovládací prvek přepne zpět do volajícího.</span><span class="sxs-lookup"><span data-stu-id="7857b-156">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="7857b-157">Se řízení vrací z asynchronní metodu jeho volajícímu buď pokud `await` se střetne s operátorem ve volané metodě, nebo po ukončení volané metody.</span><span class="sxs-lookup"><span data-stu-id="7857b-157">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="7857b-158">Zobrazené řádky, které jsou označeny jako "Tři"až "šest" trasují tuto část procesu.</span><span class="sxs-lookup"><span data-stu-id="7857b-158">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="7857b-159">Krok 3</span><span class="sxs-lookup"><span data-stu-id="7857b-159">Step THREE</span></span>

<span data-ttu-id="7857b-160">V `AccessTheWebAsync`, asynchronní metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> volána ke stažení obsahu cílové webové stránky.</span><span class="sxs-lookup"><span data-stu-id="7857b-160">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="7857b-161">Ovládací prvek vrátí `client.GetStringAsync` k `AccessTheWebAsync` při `client.GetStringAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="7857b-161">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="7857b-162">`client.GetStringAsync` Metoda vrátí úlohu řetězce, který je přiřazen `getStringTask` proměnné v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="7857b-162">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="7857b-163">Následující řádek v příkladu programu ukazuje volání do `client.GetStringAsync` a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="7857b-163">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="7857b-164">Úlohy si můžete představit jako za příslib od `client.GetStringAsync` nakonec vytvoří vytvoření skutečného řetězce.</span><span class="sxs-lookup"><span data-stu-id="7857b-164">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="7857b-165">Do té doby Pokud `AccessTheWebAsync` má pracovní postup, která není závislá na přislíbeném řetězci z `client.GetStringAsync`, této práci pokračovat během `client.GetStringAsync` čeká.</span><span class="sxs-lookup"><span data-stu-id="7857b-165">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="7857b-166">V tomto příkladu představují následující řádky výstupu, které nesou označení "Tři", příležitost k nezávislé práci.</span><span class="sxs-lookup"><span data-stu-id="7857b-166">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="7857b-167">Následující příkaz pozastaví průběh `AccessTheWebAsync` při `getStringTask` je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="7857b-167">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="7857b-168">Následující obrázek znázorňuje tok řízení z `client.GetStringAsync` k přiřazení na `getStringTask` a od vytvoření `getStringTask` k použití operátoru await.</span><span class="sxs-lookup"><span data-stu-id="7857b-168">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="7857b-169">![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace tři")</span><span class="sxs-lookup"><span data-stu-id="7857b-169">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="7857b-170">Výraz await pozastaví `AccessTheWebAsync` dokud `client.GetStringAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="7857b-170">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="7857b-171">Do té doby se ovládací prvek vrátí volajícímu metody `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="7857b-171">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="7857b-172">Obvykle můžete očekávat volání asynchronní metody okamžitě.</span><span class="sxs-lookup"><span data-stu-id="7857b-172">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="7857b-173">Například následující přiřazení může nahradit předchozí kód, který vytvoří a poté očekává `getStringTask`:</span><span class="sxs-lookup"><span data-stu-id="7857b-173">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`:</span></span> `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`
>
> <span data-ttu-id="7857b-174">V tomto tématu je později použit operátor await pro výstupní řádky, které označí tok řízení programem.</span><span class="sxs-lookup"><span data-stu-id="7857b-174">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="7857b-175">Krok 4</span><span class="sxs-lookup"><span data-stu-id="7857b-175">Step FOUR</span></span>

<span data-ttu-id="7857b-176">Deklarovaný návratový typ `AccessTheWebAsync` je `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="7857b-176">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="7857b-177">Proto když `AccessTheWebAsync` je pozastaven, vrátí úkol čísla do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="7857b-177">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="7857b-178">Měli byste pochopit, že vrácená úloha není `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="7857b-178">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="7857b-179">Vrácený úkol je nový úkol celého čísla, která představuje, co je ještě třeba provést v pozastavené metodě `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="7857b-179">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="7857b-180">Úkol je příslib z `AccessTheWebAsync` k vytvoření celého čísla po dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="7857b-180">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="7857b-181">Následující příkaz přiřadí tuto úlohu `getLengthTask` proměnné.</span><span class="sxs-lookup"><span data-stu-id="7857b-181">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="7857b-182">Stejně jako v `AccessTheWebAsync`, `startButton_Click` může pokračovat v práci, která nezávisí na výsledcích asynchronní úlohy (`getLengthTask`) dokud je na úkol čekáno.</span><span class="sxs-lookup"><span data-stu-id="7857b-182">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="7857b-183">Následující řádky výstupu představují tuto práci.</span><span class="sxs-lookup"><span data-stu-id="7857b-183">The following output lines represent that work.</span></span>

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="7857b-184">V průběhu `startButton_Click` se pozastavuje, když `getLengthTask` je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="7857b-184">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="7857b-185">Přiřazovací příkaz pozastaví `startButton_Click` dokud `AccessTheWebAsync` je dokončena.</span><span class="sxs-lookup"><span data-stu-id="7857b-185">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="7857b-186">Na následujícím obrázku šipky zobrazují tok řízení z výrazu await v metodě `AccessTheWebAsync` k přiřazení hodnoty ke `getLengthTask`, následované běžným zpracováním v `startButton_Click` dokud `getLengthTask` je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="7857b-186">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="7857b-187">![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace čtyři")</span><span class="sxs-lookup"><span data-stu-id="7857b-187">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="7857b-188">Krok 5</span><span class="sxs-lookup"><span data-stu-id="7857b-188">Step FIVE</span></span>

<span data-ttu-id="7857b-189">Když `client.GetStringAsync` signalizuje, že je dokončeno, zpracování v `AccessTheWebAsync` je uvolněno z pozastavení a může pokračovat po příkazu await.</span><span class="sxs-lookup"><span data-stu-id="7857b-189">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="7857b-190">Následující řádky výstupu představují opětovné zpracování.</span><span class="sxs-lookup"><span data-stu-id="7857b-190">The following lines of output represent the resumption of processing.</span></span>

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="7857b-191">Operanda příkazu return, `urlContents.Length`, je uložen v úloze, která `AccessTheWebAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="7857b-191">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="7857b-192">Výraz await získá tuto hodnotu z `getLengthTask` v `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="7857b-192">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="7857b-193">Následující obrázek znázorňuje přenos ovládání po `client.GetStringAsync` (a `getStringTask`) jsou dokončeny.</span><span class="sxs-lookup"><span data-stu-id="7857b-193">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="7857b-194">![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace pěti")</span><span class="sxs-lookup"><span data-stu-id="7857b-194">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 `AccessTheWebAsync` <span data-ttu-id="7857b-195">spuštění a dokončení, ovládací prvek vrátí na `startButton_Click`, který čeká na dokončení.</span><span class="sxs-lookup"><span data-stu-id="7857b-195">runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="7857b-196">Krok 6</span><span class="sxs-lookup"><span data-stu-id="7857b-196">Step SIX</span></span>

<span data-ttu-id="7857b-197">Když `AccessTheWebAsync` oznamuje, že je dokončeno, zpracování může pokračovat po příkazu await v `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="7857b-197">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="7857b-198">Program ve skutečnosti nemá žádnou další akci nelze provést.</span><span class="sxs-lookup"><span data-stu-id="7857b-198">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="7857b-199">Následující řádky výstupu představují opětovné zpracování ve službě `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="7857b-199">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="7857b-200">Výraz await získá z `getLengthTask` celočíselnou hodnotu, která je operandou příkazu return v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="7857b-200">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="7857b-201">Následující příkaz přiřadí tuto hodnotu `contentLength` proměnné.</span><span class="sxs-lookup"><span data-stu-id="7857b-201">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="7857b-202">Následující obrázek znázorňuje návrat ovládacího prvku z `AccessTheWebAsync` k `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="7857b-202">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="7857b-203">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="7857b-203">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="7857b-204">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7857b-204">See also</span></span>

- [<span data-ttu-id="7857b-205">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="7857b-205">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="7857b-206">Asynchronní návratové typy (C#)</span><span class="sxs-lookup"><span data-stu-id="7857b-206">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="7857b-207">Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="7857b-207">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="7857b-208">Ukázka asynchronní metody: Řízení toku v asynchronních programech (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7857b-208">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
