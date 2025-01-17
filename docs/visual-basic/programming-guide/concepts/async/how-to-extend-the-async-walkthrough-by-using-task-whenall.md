---
title: 'Postupy: roztažení asynchronního návodu pomocí Task. WhenAll (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 0a1d55fb8433d789326b03c402841dcaf3cc3994
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524317"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>Postupy: roztažení asynchronního návodu pomocí Task. WhenAll (Visual Basic)

Můžete zvýšit výkon asynchronního řešení v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) pomocí metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Tato metoda asynchronně očekává více asynchronních operací, které jsou reprezentovány jako kolekce úkolů.

Možná jste si všimli v návodu, že se weby stahují různými sazbami. Někdy je jeden z webů velmi pomalý, což zpozdí všechna zbývající stahování. Při spuštění asynchronních řešení, která sestavíte v tomto návodu, můžete program ukončit, pokud nechcete čekat, ale lepší možností je zahájit všechna stahování ve stejnou dobu a umožnit rychlejší stahování i nadále, aniž byste čekali na to, který z nich je  platba.

Metodu `Task.WhenAll` použijete pro kolekci úkolů. Aplikace `WhenAll` vrátí jednu úlohu, která není dokončena, dokud není dokončen každý úkol v kolekci. Úkoly se zdají běžet paralelně, ale nevytvoří se žádné další podprocesy. Úkoly mohou být dokončeny v libovolném pořadí.

> [!IMPORTANT]
> Následující postupy popisují rozšíření pro asynchronní aplikace, které jsou vyvíjeny v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Můžete vyvíjet aplikace buď dokončením návodu, nebo stažením kódu z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).
>
> Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Přidání metody Task.WhenAll do řešení GetURLContentsAsync

1. Přidejte metodu `ProcessURLAsync` do první aplikace, která je vyvíjena v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Pokud jste stáhli kód z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough a poté přidejte `ProcessURLAsync` do souboru MainWindow. XAML. vb.

    - Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` do aplikace, která obsahuje metodu `GetURLContentsAsync`. Soubor MainWindow. XAML. vb pro tuto aplikaci je prvním příkladem v části kompletní příklady kódu z návodu.

     Metoda `ProcessURLAsync` slučuje akce v těle `For Each` smyčky v `SumPageSizesAsync` v původním návodu. Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a poté zobrazí a vrátí délku bajtového pole.

    ```vb
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. Odkomentujte nebo odstraňte smyčku `For Each` v `SumPageSizesAsync`, jak ukazuje následující kód.

    ```vb
    'Dim total = 0
    'For Each url In urlList

    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

    '    ' The previous line abbreviates the following two assignment statements.

    '    ' GetURLContentsAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. Vytvořte kolekci úkolů. Následující kód definuje [dotaz](../../../../visual-basic/programming-guide/concepts/linq/index.md) , který při spuštění metodou <xref:System.Linq.Enumerable.ToArray%2A> vytvoří kolekci úkolů, které stáhnou obsah každého webu. Úkoly se spustí, když se dotaz vyhodnotí.

     Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `urlList`.

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. Použijte `Task.WhenAll` pro kolekci úloh `downloadTasks`. `Task.WhenAll` vrátí jednu úlohu, která skončí po dokončení všech úloh v kolekci úkolů.

     V následujícím příkladu výraz `Await` čeká na dokončení jedné úlohy, která `WhenAll` vrací. Výraz je vyhodnocen jako pole celých čísel, kde každé celé číslo je délka staženého webu. Do `SumPageSizesAsync` přidejte následující kód, a to hned za kód, který jste přidali v předchozím kroku.

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. Nakonec použijte metodu <xref:System.Linq.Enumerable.Sum%2A> pro výpočet součtu délek všech webů. Přidejte následující řádek pro `SumPageSizesAsync`.

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Přidání metody Task.WhenAll do řešení HttpClient.GetByteArrayAsync

1. Do druhé aplikace, která je vyvíjena v návodu, přidejte následující verzi `ProcessURLAsync` [: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Pokud jste stáhli kód z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough_HttpClient a poté přidejte `ProcessURLAsync` do souboru MainWindow. XAML. vb.

    - Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` do aplikace, která používá metodu `HttpClient.GetByteArrayAsync`. Soubor MainWindow. XAML. vb pro tuto aplikaci je druhým příkladem v části kompletní příklady kódu z návodu.

     Metoda `ProcessURLAsync` slučuje akce v těle `For Each` smyčky v `SumPageSizesAsync` v původním návodu. Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a poté zobrazí a vrátí délku bajtového pole.

     Jediným rozdílem od metody `ProcessURLAsync` v předchozím postupu je použití instance <xref:System.Net.Http.HttpClient> `client`.

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. Odkomentujte nebo odstraňte smyčku `For Each` v `SumPageSizesAsync`, jak ukazuje následující kód.

    ```vb
    'Dim total = 0
    'For Each url In urlList
    '    ' GetByteArrayAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

    '    ' The following two lines can replace the previous assignment statement.
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. Definujte [dotaz](../../../../visual-basic/programming-guide/concepts/linq/index.md) , který při spuštění metodou <xref:System.Linq.Enumerable.ToArray%2A> vytvoří kolekci úkolů, které stáhnou obsah každého webu. Úkoly se spustí, když se dotaz vyhodnotí.

     Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `client` a `urlList`.

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. Dále `Task.WhenAll` použít pro kolekci úloh `downloadTasks`. `Task.WhenAll` vrátí jednu úlohu, která skončí po dokončení všech úloh v kolekci úkolů.

     V následujícím příkladu výraz `Await` čeká na dokončení jedné úlohy, která `WhenAll` vrací. Po dokončení se výraz `Await` vyhodnotí jako pole celých čísel, kde každé celé číslo je délka staženého webu. Do `SumPageSizesAsync` přidejte následující kód, a to hned za kód, který jste přidali v předchozím kroku.

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. Nakonec použijte metodu <xref:System.Linq.Enumerable.Sum%2A> k získání součtu délek všech webů. Přidejte následující řádek pro `SumPageSizesAsync`.

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Otestování řešení Task.WhenAll

Pro jedno řešení zvolte klávesu F5 pro spuštění programu a pak klikněte na tlačítko **Start** . Výstup by měl vypadat podobně jako výstup z asynchronních řešení v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Všimněte si ale, že se weby v každé době zobrazují v jiném pořadí.

## <a name="example"></a>Příklad

Následující kód ukazuje rozšíření pro projekt, který používá metodu `GetURLContentsAsync` ke stažení obsahu z webu.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        'Dim total = 0
        'For Each url In urlList

        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

        '    ' The previous line abbreviates the following two assignment statements.

        '    ' GetURLContentsAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    ' The actions from the foreach loop are moved to this async method.
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                ' CopyToAsync returns a Task, not a Task<T>.
                Await responseStream.CopyToAsync(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="example"></a>Příklad

Následující kód ukazuje rozšíření pro projekt, který používá metodu `HttpClient.GetByteArrayAsync` ke stažení obsahu z webu.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        ''<snippet7>
        'Dim total = 0
        'For Each url In urlList
        '    ' GetByteArrayAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    '<snippet31>
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
        '    '</snippet31>

        '    ' The following two lines can replace the previous assignment statement.
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://www.msdn.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
