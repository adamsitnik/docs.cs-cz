---
title: Podpora vícenásobného přístupu v aplikacích s modifikátorem Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 0913a8b422d8ea3d6b38680a26bac143087dd2c8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324783"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="575c2-102">Podpora vícenásobného přístupu v aplikacích s modifikátorem Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="575c2-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>
<span data-ttu-id="575c2-103">Pokud zahrnete asynchronní kód ve vaší aplikaci, by měl zvážit a případně zabránit vícenásobnému přístupu, který se vztahuje k nutnosti opětovného zadávání asynchronní operace ještě před dokončením.</span><span class="sxs-lookup"><span data-stu-id="575c2-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="575c2-104">Pokud neidentifikujete a nemanipulujete vícenásobnému přístupu, může to způsobit neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="575c2-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 **<span data-ttu-id="575c2-105">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="575c2-105">In this topic</span></span>**  
  
-   [<span data-ttu-id="575c2-106">Rozpoznávání vícenásobného přístupu</span><span class="sxs-lookup"><span data-stu-id="575c2-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)  
  
-   [<span data-ttu-id="575c2-107">Vyřešení vícenásobného přístupu</span><span class="sxs-lookup"><span data-stu-id="575c2-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)  
  
    -   [<span data-ttu-id="575c2-108">Zakázání tlačítka Start</span><span class="sxs-lookup"><span data-stu-id="575c2-108">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
    -   [<span data-ttu-id="575c2-109">Zrušení a opětovné spuštění operace</span><span class="sxs-lookup"><span data-stu-id="575c2-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
    -   [<span data-ttu-id="575c2-110">Spuštění více operací a zařazení výstupu do fronty</span><span class="sxs-lookup"><span data-stu-id="575c2-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
-   [<span data-ttu-id="575c2-111">Prostudování a spuštění ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="575c2-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)  
  
> [!NOTE]
>  <span data-ttu-id="575c2-112">Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="575c2-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="575c2-113">Rozpoznávání vícenásobného přístupu</span><span class="sxs-lookup"><span data-stu-id="575c2-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="575c2-114">V příkladu v tomto tématu, zvolte možnost uživatelé **Start** tlačítko pro zahájení asynchronní aplikace, která stáhne řady webů a vypočítá celkový počet bajtů, které byly staženy.</span><span class="sxs-lookup"><span data-stu-id="575c2-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="575c2-115">Synchronní verze tohoto příkladu odpoví stejným způsobem bez ohledu na to, kolikrát uživatel vybere tlačítko, protože po prvním vlákně uživatelského rozhraní bude tyto události ignorovat až do ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="575c2-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="575c2-116">V asynchronní aplikaci však vlákno UI i nadále odpovídá a můžete znovu zadat asynchronní operace ještě před dokončením.</span><span class="sxs-lookup"><span data-stu-id="575c2-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="575c2-117">Následující příklad zobrazuje očekávaný výstup, když uživatel klikne **Start** tlačítko pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="575c2-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="575c2-118">Zobrazí se seznam stažených webových stránek s velikostí v bajtech každého webu.</span><span class="sxs-lookup"><span data-stu-id="575c2-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="575c2-119">Na konci se zobrazuje celkový počet bajtů.</span><span class="sxs-lookup"><span data-stu-id="575c2-119">The total number of bytes appears at the end.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="575c2-120">Pokud uživatel vybere tlačítko více než jednou, ale obslužná rutina události je vyvolána opakovaně, a proces stahování je znovu zadat pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="575c2-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="575c2-121">V důsledku toho několik asynchronních operací spuštěno ve stejnou dobu, výstup předřadí výsledky a celkový počet bajtů je matoucí.</span><span class="sxs-lookup"><span data-stu-id="575c2-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
7. msdn.microsoft.com                                            42972  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
7. msdn.microsoft.com                                            42972  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="575c2-122">Můžete zkontrolovat kód, který vytváří tento výstup, přechodem na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="575c2-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="575c2-123">Můžete experimentovat s kódem stažením řešení do místního počítače a následným spuštěním projektu WebsiteDownload nebo pomocí kódu na konci tohoto tématu k vytvoření vlastního projektu pro další informace a pokyny naleznete v tématu [ Prostudování a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="575c2-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>  
  
## <a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="575c2-124">Podpora vícenásobného přístupu</span><span class="sxs-lookup"><span data-stu-id="575c2-124">Handling Reentrancy</span></span>  
 <span data-ttu-id="575c2-125">Můžete zpracovat vícenásobnost různými způsoby v závislosti na tom, co chcete, aby vaše aplikace provést.</span><span class="sxs-lookup"><span data-stu-id="575c2-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="575c2-126">Toto téma představuje následující příklady:</span><span class="sxs-lookup"><span data-stu-id="575c2-126">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="575c2-127">Zakázání tlačítka Start</span><span class="sxs-lookup"><span data-stu-id="575c2-127">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
     <span data-ttu-id="575c2-128">Zakažte **Start** tlačítko během operace tak, aby uživatel nemohl přerušit ho.</span><span class="sxs-lookup"><span data-stu-id="575c2-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="575c2-129">Zrušení a opětovné spuštění operace</span><span class="sxs-lookup"><span data-stu-id="575c2-129">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
     <span data-ttu-id="575c2-130">Zrušit jakoukoli operaci, která je stále spuštěna, když uživatel klikne **Start** tlačítko znovu, a potom pokračujte umožňují nedávno požadované operace.</span><span class="sxs-lookup"><span data-stu-id="575c2-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="575c2-131">Spuštění více operací a zařazení výstupu do fronty</span><span class="sxs-lookup"><span data-stu-id="575c2-131">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
     <span data-ttu-id="575c2-132">Povolit, že všechny požadované operace běžely asynchronně, ale koordinovat zobrazení výstupu tak, aby se výsledky z každé operace zobrazovaly společně a v pořadí.</span><span class="sxs-lookup"><span data-stu-id="575c2-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
### <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="575c2-133">Zakázání tlačítka Start</span><span class="sxs-lookup"><span data-stu-id="575c2-133">Disable the Start Button</span></span>  
 <span data-ttu-id="575c2-134">Můžete blokovat **Start** tlačítko, když je spuštěná operace, zakázáním tlačítka v horní části `StartButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="575c2-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="575c2-135">Potom můžete znovu povolit tlačítko z `Finally` blokovat po ukončení operace tak, aby uživatelé můžou aplikaci spouštět znovu.</span><span class="sxs-lookup"><span data-stu-id="575c2-135">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="575c2-136">Následující kód znázorňuje tyto změny, které jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="575c2-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="575c2-137">Změny můžete přidat do kódu na konci tohoto tématu nebo si můžete stáhnout hotovou aplikaci z [asynchronní vzorky: Vícenásobný přístup v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="575c2-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="575c2-138">Název projektu je DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="575c2-138">The project name is DisableStartButton.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' This line is commented out to make the results clearer in the output.  
    'ResultsTextBox.Text = ""  
  
    ' ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = False  
  
    Try  
        Await AccessTheWebAsync()  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    ' ***Enable the Start button in case you want to run the program again.   
    Finally  
        StartButton.IsEnabled = True  
  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="575c2-139">V důsledku změny, tlačítko nereaguje zatímco `AccessTheWebAsync` stahuje webové stránky, takže proces nelze znovu zadat.</span><span class="sxs-lookup"><span data-stu-id="575c2-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
### <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="575c2-140">Nerušte a nerestartujte operace</span><span class="sxs-lookup"><span data-stu-id="575c2-140">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="575c2-141">Namísto zakázání **Start** tlačítko, můžete zachovat tlačítko aktivní, ale, pokud uživatel vybere toto tlačítko znovu, zrušit operaci, která je již spuštěna a nechá pokračovat v operaci naposledy spuštěnou.</span><span class="sxs-lookup"><span data-stu-id="575c2-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="575c2-142">Další informace o zrušení naleznete v tématu [asynchronní aplikace Fine-Tuning (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="575c2-142">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="575c2-143">Nastavit tento scénář, proveďte následující změny základního kódu, která je součástí [Prostudování a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="575c2-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="575c2-144">Také můžete stáhnout hotovou aplikaci z [asynchronní vzorky: Vícenásobný přístup v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="575c2-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="575c2-145">Název tohoto projektu je CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="575c2-145">The name of this project is CancelAndRestart.</span></span>  
  
1. <span data-ttu-id="575c2-146">Deklarace <xref:System.Threading.CancellationTokenSource> proměnnou, `cts`, která je v oboru pro všechny metody.</span><span class="sxs-lookup"><span data-stu-id="575c2-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2. <span data-ttu-id="575c2-147">V `StartButton_Click`, určete, zda již probíhá operace.</span><span class="sxs-lookup"><span data-stu-id="575c2-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="575c2-148">Pokud hodnota `cts` je `Nothing`, žádná operace ještě není aktivní.</span><span class="sxs-lookup"><span data-stu-id="575c2-148">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="575c2-149">Pokud hodnota není `Nothing`, je zrušena operace, která je již spuštěna.</span><span class="sxs-lookup"><span data-stu-id="575c2-149">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3. <span data-ttu-id="575c2-150">Nastavte `cts` na jinou hodnotu, která představuje aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="575c2-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4. <span data-ttu-id="575c2-151">Na konci `StartButton_Click`, je aktuální proces dokončen, takže nastavte hodnotu `cts` zpět `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="575c2-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 <span data-ttu-id="575c2-152">Následující kód ukazuje všechny změny v `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="575c2-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="575c2-153">Přidání jsou označena hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="575c2-153">The additions are marked with asterisks.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' This line is commented out to make the results clearer.   
    'ResultsTextBox.Text = ""  
  
    ' *** If a download process is underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
  
    Try  
        ' *** Send a token to carry the message if the operation is canceled.  
        Await AccessTheWebAsync(cts.Token)  
  
    Catch ex As OperationCanceledException  
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    End Try  
  
    ' *** When the process is complete, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
End Sub  
```  
  
 <span data-ttu-id="575c2-154">V `AccessTheWebAsync`, proveďte následující změny.</span><span class="sxs-lookup"><span data-stu-id="575c2-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="575c2-155">Přidat parametr pro přijetí tokenu zrušení z `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="575c2-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="575c2-156">Použití <xref:System.Net.Http.HttpClient.GetAsync%2A> metoda stažení webových stránek, protože `GetAsync` přijímá <xref:System.Threading.CancellationToken> argument.</span><span class="sxs-lookup"><span data-stu-id="575c2-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="575c2-157">Před voláním `DisplayResults` Chcete-li zobrazit výsledky pro každý stažený web, zkontrolujte `ct` k ověření, že aktuální operace nebyla zrušena.</span><span class="sxs-lookup"><span data-stu-id="575c2-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="575c2-158">Následující kód znázorňuje tyto změny, které jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="575c2-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
```vb  
' *** Provide a parameter for the CancellationToken from StartButton_Click.  
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
    ' Declare an HttpClient object.  
    Dim client = New HttpClient()  
  
    ' Make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    Dim total = 0  
    Dim position = 0  
  
    For Each url In urlList  
        ' *** Use the HttpClient.GetAsync method because it accepts a   
        ' cancellation token.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' *** Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' *** Check for cancellations before displaying information about the   
        ' latest site.   
        ct.ThrowIfCancellationRequested()  
  
        position += 1  
        DisplayResults(url, urlContents, position)  
  
        ' Update the total.  
        total += urlContents.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="575c2-159">Pokud se rozhodnete **Start** tlačítko několikrát během spuštění této aplikace mohou být vráceny výsledky, které se podobají následujícímu výstupu.</span><span class="sxs-lookup"><span data-stu-id="575c2-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               122505  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="575c2-160">Chcete-li odstranit dílčí seznamy, zrušte komentář u prvního řádku kódu v `StartButton_Click` vymazání textového pole pokaždé, když uživatel znovu spustí operaci.</span><span class="sxs-lookup"><span data-stu-id="575c2-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
### <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="575c2-161">Spustit více operací a zařazení výstupu do fronty</span><span class="sxs-lookup"><span data-stu-id="575c2-161">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="575c2-162">Tento třetí příklad je v nejkomplikovanější v tom, že aplikace spustí jinou asynchronní operaci pokaždé, když uživatel klikne **Start** tlačítko a všechny operace běží až do dokončení.</span><span class="sxs-lookup"><span data-stu-id="575c2-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="575c2-163">Všechny požadované operace stahují webové stránky ze seznamu asynchronně, ale výstup z operací je uveden postupně.</span><span class="sxs-lookup"><span data-stu-id="575c2-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="575c2-164">To znamená, že skutečná aktivita stahování je prokládána, jak poukazuje výstup v [rozpoznávání vícenásobného přístupu](#BKMK_RecognizingReentrancy) zobrazí, ale seznam výsledků pro každou skupinu je předkládán samostatně.</span><span class="sxs-lookup"><span data-stu-id="575c2-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="575c2-165">Operace sdílí globální <xref:System.Threading.Tasks.Task>, `pendingWork`, který slouží jako správce pro zpracování zobrazení.</span><span class="sxs-lookup"><span data-stu-id="575c2-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="575c2-166">Tento příklad lze spustit zadáním nebo vložením změn do kódu v [aplikaci](#BKMK_BuildingTheApp), nebo můžete postupovat podle pokynů v [si stáhnou aplikaci](#BKMK_DownloadingTheApp) ke stažení vzorku a spuštění projektu QueueResults.</span><span class="sxs-lookup"><span data-stu-id="575c2-166">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="575c2-167">Následující výstup zobrazuje výsledek, když uživatel klikne **Start** tlačítko pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="575c2-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="575c2-168">Označení písmenem A označuje, že výsledek pochází z prvního **Start** kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="575c2-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="575c2-169">Čísla popisují pořadí adres URL v seznamu cílů ke stažení.</span><span class="sxs-lookup"><span data-stu-id="575c2-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               209858  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
A-7. msdn.microsoft.com                                            53266  
A-8. msdn.microsoft.com/library/ff730837.aspx               148020  
  
TOTAL bytes returned:  918876  
  
#Group A is complete.  
```  
  
 <span data-ttu-id="575c2-170">Pokud uživatel klikne **Start** tlačítko třikrát, aplikace vytvoří výstup, který se podobá následujícím řádkům.</span><span class="sxs-lookup"><span data-stu-id="575c2-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="575c2-171">Podepsat informační řádky, které začínají znakem křížku (#), sledují průběh aplikace.</span><span class="sxs-lookup"><span data-stu-id="575c2-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71259  
A-6. msdn.microsoft.com/library/ms404677.aspx               199185  
  
#Starting group B.  
#Task assigned for group B.  
  
A-7. msdn.microsoft.com                                            53266  
  
#Starting group C.  
#Task assigned for group C.  
  
A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916095  
  
B-1. msdn.microsoft.com/library/hh191443.aspx                87389  
B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
  
#Group A is complete.  
  
B-7. msdn.microsoft.com                                            53266  
B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916097  
  
C-1. msdn.microsoft.com/library/hh191443.aspx                87389  
C-2. msdn.microsoft.com/library/aa578028.aspx               207089  
  
#Group B is complete.  
  
C-3. msdn.microsoft.com/library/jj155761.aspx                30870  
C-4. msdn.microsoft.com/library/hh290140.aspx               119027  
C-5. msdn.microsoft.com/library/hh524395.aspx                72765  
C-6. msdn.microsoft.com/library/ms404677.aspx               199186  
C-7. msdn.microsoft.com                                            56190  
C-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  920526  
  
#Group C is complete.  
```  
  
 <span data-ttu-id="575c2-172">Skupiny B a C se spustí před dokončením skupiny A, ale výstup pro jednotlivé skupiny se zobrazí odděleně.</span><span class="sxs-lookup"><span data-stu-id="575c2-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="575c2-173">Veškerý výstup pro skupinu A zobrazí se první, následovaný všemi výstupy pro skupinu B a pak veškerý výstup pro skupinu C. Aplikace vždy zobrazí skupiny v pořadí a pro každou skupinu vždy zobrazí informace o jednotlivých webech v pořadí, ve kterém se zobrazí v seznamu adres URL adresy URL.</span><span class="sxs-lookup"><span data-stu-id="575c2-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="575c2-174">Nelze však předvídat pořadí, ve kterém se soubory ke stažení skutečně došlo.</span><span class="sxs-lookup"><span data-stu-id="575c2-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="575c2-175">Po spuštění více skupin, jsou všechny aktivní úlohy stahování, které generují.</span><span class="sxs-lookup"><span data-stu-id="575c2-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="575c2-176">Nelze předpokládat, že A-1 se stáhne před b-1 a nelze předpokládat, že A-1 se stáhne před a-2.</span><span class="sxs-lookup"><span data-stu-id="575c2-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="575c2-177">Globální definice</span><span class="sxs-lookup"><span data-stu-id="575c2-177">Global Definitions</span></span>  
 <span data-ttu-id="575c2-178">Ukázka kódu obsahuje následující dvě globální deklarace, které jsou viditelné ze všech metod.</span><span class="sxs-lookup"><span data-stu-id="575c2-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 <span data-ttu-id="575c2-179">`Task` Proměnnou, `pendingWork`, dohlíží na proces zobrazení a zabrání jakékoli skupině v přerušení operace zobrazení jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="575c2-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="575c2-180">Proměnné znaku `group`, značí výstup z různých skupin a ověřte tak, že výsledky zobrazí v očekávaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="575c2-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="575c2-181">Obslužná rutina události kliknutí</span><span class="sxs-lookup"><span data-stu-id="575c2-181">The Click Event Handler</span></span>  
 <span data-ttu-id="575c2-182">Obslužná rutina události `StartButton_Click`, zvyšuje písmeno skupiny pokaždé, když uživatel klikne **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="575c2-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="575c2-183">Potom rutina volá `AccessTheWebAsync` ke spuštění operace stahování.</span><span class="sxs-lookup"><span data-stu-id="575c2-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' ***Verify that each group's results are displayed together, and that  
    ' the groups display in order, by marking each group with a letter.  
    group = ChrW(AscW(group) + 1)  
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)  
  
    Try  
        ' *** Pass the group value to AccessTheWebAsync.  
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)  
  
        ' The following line verifies a successful return from the download and   
        ' display procedures.   
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
    End Try  
End Sub  
```  
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="575c2-184">Metoda AccessTheWebAsync</span><span class="sxs-lookup"><span data-stu-id="575c2-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="575c2-185">V tomto příkladu rozdělí `AccessTheWebAsync` do dvou metod.</span><span class="sxs-lookup"><span data-stu-id="575c2-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="575c2-186">První metoda `AccessTheWebAsync`, spustí všechny úlohy stahování pro skupinu a nastaví `pendingWork` k řízení procesu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="575c2-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="575c2-187">Metoda používá Language Integrated Query (LINQ dotaz) a <xref:System.Linq.Enumerable.ToArray%2A> zahájíte stahování všech úloh ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="575c2-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 `AccessTheWebAsync` <span data-ttu-id="575c2-188">pak zavolá `FinishOneGroupAsync` čekání na dokončení každého stažení a zobrazení jeho délky.</span><span class="sxs-lookup"><span data-stu-id="575c2-188">then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 `FinishOneGroupAsync` <span data-ttu-id="575c2-189">Vrátí úlohu, která je přiřazena `pendingWork` v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="575c2-189">returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="575c2-190">Tato hodnota zabraňuje přerušení jinou operací před dokončením úkolu.</span><span class="sxs-lookup"><span data-stu-id="575c2-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
```vb  
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)  
  
    Dim client = New HttpClient()  
  
    ' Make a list of the web addresses to download.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Dim getContentTasks As Task(Of Byte())() =  
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()  
  
    ' ***Call the method that awaits the downloads and displays the results.  
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)  
  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)  
  
    ' ***This task is complete when a group has finished downloading and displaying.  
    Await pendingWork  
  
    ' You can do other work here or just return.  
    Return grp  
End Function  
```  
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="575c2-191">Metoda FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="575c2-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="575c2-192">Tato metoda projde stažené úlohy ve skupině, čeká na každé z nich, zobrazení délky staženého webu a přičtením délky k celku.</span><span class="sxs-lookup"><span data-stu-id="575c2-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="575c2-193">První příkaz v `FinishOneGroupAsync` používá `pendingWork` abyste měli jistotu, že zadávání metody není v konfliktu s operací, která je již v procesu zobrazení nebo která již čeká.</span><span class="sxs-lookup"><span data-stu-id="575c2-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="575c2-194">Pokud tato operace probíhá, operace zadávání musí čekat, než přijde.</span><span class="sxs-lookup"><span data-stu-id="575c2-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
```vb  
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task  
  
    ' Wait for the previous group to finish displaying results.  
    If pendingWork IsNot Nothing Then  
        Await pendingWork  
    End If  
  
    Dim total = 0  
  
    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    For i As Integer = 0 To contentTasks.Length - 1  
        ' Await the download of a particular URL, and then display the URL and  
        ' its length.  
        Dim content As Byte() = Await contentTasks(i)  
        DisplayResults(urls(i), content, i, grp)  
        total += content.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="575c2-195">Tento příklad lze spustit zadáním nebo vložením změn do kódu v [aplikaci](#BKMK_BuildingTheApp), nebo můžete postupovat podle pokynů v [si stáhnou aplikaci](#BKMK_DownloadingTheApp) ke stažení vzorku a spuštění projektu QueueResults.</span><span class="sxs-lookup"><span data-stu-id="575c2-195">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="575c2-196">Body zájmu</span><span class="sxs-lookup"><span data-stu-id="575c2-196">Points of Interest</span></span>  
 <span data-ttu-id="575c2-197">Informační řádky, které začínají znakem křížku (#) ve výstupu vysvětlení, jak tento příklad funguje.</span><span class="sxs-lookup"><span data-stu-id="575c2-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="575c2-198">Výstup zobrazuje následující vzory.</span><span class="sxs-lookup"><span data-stu-id="575c2-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="575c2-199">Skupiny může být spuštěna, když předchozí skupina zobrazuje výstup, ale zobrazení výstupu předchozí skupiny není přerušeno.</span><span class="sxs-lookup"><span data-stu-id="575c2-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
    ```  
    #Starting group A.  
    #Task assigned for group A. Download tasks are active.  
  
    A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037  
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
  
    A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    A-7. msdn.microsoft.com                                            53078  
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915919  
  
    B-1. msdn.microsoft.com/library/hh191443.aspx                87388  
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
  
    #Group A is complete.  
  
    B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    B-7. msdn.microsoft.com                                            53078  
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915908  
    ```  
  
-   <span data-ttu-id="575c2-200">`pendingWork` Úkol je `Nothing` na začátku `FinishOneGroupAsync` pouze u skupiny A, která začíná jako první.</span><span class="sxs-lookup"><span data-stu-id="575c2-200">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="575c2-201">Skupina A dosud nedokončila výraz await, až dosáhne `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="575c2-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="575c2-202">Proto se ovládací prvek nevrátil do `AccessTheWebAsync`a první přiřazení k `pendingWork` nedošlo k.</span><span class="sxs-lookup"><span data-stu-id="575c2-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="575c2-203">Následující dva řádky vždy zobrazí společně ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="575c2-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="575c2-204">Kód není nikdy přerušen mezi spuštěním operace skupiny `StartButton_Click` a přiřazením úkolu skupiny `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="575c2-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="575c2-205">Po vstupu skupiny do `StartButton_Click`, operace nedokončí výraz await, dokud operace nevstoupí do `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="575c2-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="575c2-206">Proto se žádná jiná operace nemůže získat kontrolu během tohoto segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="575c2-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
## <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="575c2-207">Prostudování a spuštění ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="575c2-207">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="575c2-208">Pro lepší pochopení příkladu aplikace, můžete si ho stáhnout, sestavit ji sami nebo zkontrolovat kód na konci tohoto tématu bez implementace aplikace.</span><span class="sxs-lookup"><span data-stu-id="575c2-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="575c2-209">Chcete-li spustit příklad jako aplikaci klasické pracovní plochy Windows Presentation Foundation (WPF), musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="575c2-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="575c2-210">Stažení aplikace</span><span class="sxs-lookup"><span data-stu-id="575c2-210">Downloading the App</span></span>  
  
1. <span data-ttu-id="575c2-211">Stáhněte si komprimovaný soubor z [asynchronní vzorky: Vícenásobný přístup v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="575c2-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>  
  
2. <span data-ttu-id="575c2-212">Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="575c2-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3. <span data-ttu-id="575c2-213">V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="575c2-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4. <span data-ttu-id="575c2-214">Přejděte do složky obsahující dekomprimovaný ukázkový kód a potom otevřete soubor řešení (.sln).</span><span class="sxs-lookup"><span data-stu-id="575c2-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5. <span data-ttu-id="575c2-215">V **Průzkumníka řešení**, otevřete místní nabídku pro projekt, který chcete spustit a klikněte na tlačítko **nastavit jako výchozí projekt**.</span><span class="sxs-lookup"><span data-stu-id="575c2-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6. <span data-ttu-id="575c2-216">Stiskněte klávesy CTRL + F5 sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="575c2-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
### <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="575c2-217">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="575c2-217">Building the App</span></span>  
 <span data-ttu-id="575c2-218">Následující část obsahuje kód pro vytváření příklad jako aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="575c2-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="575c2-219">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="575c2-219">To build a WPF app</span></span>  
  
1. <span data-ttu-id="575c2-220">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="575c2-220">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="575c2-221">V panelu nabídky zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="575c2-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="575c2-222">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="575c2-222">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="575c2-223">V **nainstalované šablony** podokně rozbalte **jazyka Visual Basic**a potom rozbalte **Windows**.</span><span class="sxs-lookup"><span data-stu-id="575c2-223">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>  
  
4. <span data-ttu-id="575c2-224">V seznamu typů projektů zvolte **aplikace WPF**.</span><span class="sxs-lookup"><span data-stu-id="575c2-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5. <span data-ttu-id="575c2-225">Pojmenujte projekt `WebsiteDownloadWPF`a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="575c2-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="575c2-226">Nový projekt se zobrazí v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="575c2-226">The new project appears in **Solution Explorer**.</span></span>  
  
6. <span data-ttu-id="575c2-227">V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.</span><span class="sxs-lookup"><span data-stu-id="575c2-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="575c2-228">Pokud karta není zobrazena, otevřete místní nabídku souboru mainwindow.XAML v **Průzkumníka řešení**a klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="575c2-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7. <span data-ttu-id="575c2-229">V **XAML** zobrazení souboru mainwindow.XAML, nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="575c2-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:local="using:WebsiteDownloadWPF"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        mc:Ignorable="d">  
  
        <Grid Width="517" Height="360">  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="575c2-230">Jednoduché okno obsahující textové pole a tlačítko se zobrazí v **návrhu** zobrazení souboru MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="575c2-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8. <span data-ttu-id="575c2-231">Přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="575c2-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="575c2-232">V **Průzkumníka řešení**, otevřete místní nabídku pro soubor MainWindow.xaml.vb a klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="575c2-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="575c2-233">V souboru MainWindow.xaml.vb nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="575c2-233">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
    ```vb  
    ' Add the following Imports statements, and add a reference for System.Net.Http.  
    Imports System.Net.Http  
    Imports System.Threading  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
            ' This line is commented out to make the results clearer in the output.  
            'ResultsTextBox.Text = ""  
  
            Try  
                Await AccessTheWebAsync()  
  
            Catch ex As Exception  
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
            End Try  
        End Sub  
  
        Private Async Function AccessTheWebAsync() As Task  
  
            ' Declare an HttpClient object.  
            Dim client = New HttpClient()  
  
            ' Make a list of web addresses.  
            Dim urlList As List(Of String) = SetUpURLList()  
  
            Dim total = 0  
            Dim position = 0  
  
            For Each url In urlList  
                ' GetByteArrayAsync returns a task. At completion, the task  
                ' produces a byte array.  
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
                position += 1  
                DisplayResults(url, urlContents, position)  
  
                ' Update the total.  
                total += urlContents.Length  
            Next  
  
            ' Display the total count for all of the websites.  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
        End Function  
  
        Private Function SetUpURLList() As List(Of String)  
            Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com/library/hh191443.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/jj155761.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/hh524395.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
            Return urls  
        End Function  
  
        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)  
            ' Display the length of each website. The string format is designed  
            ' to be used with a monospaced font, such as Lucida Console or  
            ' Global Monospace.  
  
            ' Strip off the "http:'".  
            Dim displayURL = url.Replace("https://", "")  
            ' Display position in the URL list, the URL, and the number of bytes.  
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)  
        End Sub  
    End Class  
    ```  
  
11. <span data-ttu-id="575c2-234">Stiskněte klávesy CTRL + F5 ke spuštění programu a klikněte na tlačítko **Start** tlačítko několikrát.</span><span class="sxs-lookup"><span data-stu-id="575c2-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="575c2-235">Proveďte požadované změny z [zakázat tlačítko Start](#BKMK_DisableTheStartButton), [nerušte a nerestartujte operaci](#BKMK_CancelAndRestart), nebo [spustit více operací a fronty výstupu](#BKMK_RunMultipleOperations) pro zpracování vícenásobného přístupu.</span><span class="sxs-lookup"><span data-stu-id="575c2-235">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="575c2-236">Viz také:</span><span class="sxs-lookup"><span data-stu-id="575c2-236">See also</span></span>

- [<span data-ttu-id="575c2-237">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="575c2-237">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="575c2-238">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="575c2-238">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
