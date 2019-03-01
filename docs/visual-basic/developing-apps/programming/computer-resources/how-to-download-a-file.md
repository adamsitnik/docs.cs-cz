---
title: 'Postupy: Stáhněte si soubor v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 927f2598e064ddcda30a13d811bc4a986207b23d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969008"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="24181-102">Postupy: Stáhněte si soubor v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24181-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="24181-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Metodu je možné stáhnout soubor vzdálené a uloží je do určitého umístění.</span><span class="sxs-lookup"><span data-stu-id="24181-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="24181-104">Pokud `ShowUI` parametr je nastaven na `True`, zobrazí se dialogové okno zobrazuje průběh stahování a uživatelé si můžou na zrušení operace.</span><span class="sxs-lookup"><span data-stu-id="24181-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="24181-105">Ve výchozím nastavení nejsou přepsány existující soubory se stejným názvem. Pokud chcete přepsat existující soubory, nastavte `overwrite` parametr `True`.</span><span class="sxs-lookup"><span data-stu-id="24181-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="24181-106">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="24181-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="24181-107">Název disku je neplatný (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="24181-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="24181-108">Nebyla zadána potřebné ověřovací (<xref:System.UnauthorizedAccessException> nebo <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="24181-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="24181-109">Server neobjeví odpověď během zadaného `connectionTimeout` (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="24181-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
-   <span data-ttu-id="24181-110">Požadavek se zamítne na webu (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="24181-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="24181-111">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="24181-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="24181-112">Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="24181-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="24181-113">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="24181-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="24181-114">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="24181-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="24181-115">Ke stažení souboru</span><span class="sxs-lookup"><span data-stu-id="24181-115">To download a file</span></span>  
  
-   <span data-ttu-id="24181-116">Použití `DownloadFile` metoda ke stažení souboru, zadáte umístění cílového souboru jako řetězec nebo identifikátor URI a zadání umístění, kam chcete soubor uložit.</span><span class="sxs-lookup"><span data-stu-id="24181-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="24181-117">Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a ukládá ji do `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="24181-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="24181-118">Ke stažení souboru, intervalem časového limitu</span><span class="sxs-lookup"><span data-stu-id="24181-118">To download a file, specifying a time-out interval</span></span>  
  
-   <span data-ttu-id="24181-119">Použití `DownloadFile` metoda ke stažení souboru, určení umístění cílového souboru jako řetězec nebo identifikátor URI, zadáte umístění, kam chcete uložit soubor a intervalem časového limitu v milisekundách (výchozí hodnota je 1000).</span><span class="sxs-lookup"><span data-stu-id="24181-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="24181-120">Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a ukládá ji do `C:\Documents and Settings\All Users\Documents`, intervalem časového limitu 500 MS:</span><span class="sxs-lookup"><span data-stu-id="24181-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="24181-121">Ke stažení souboru, zadávání uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="24181-121">To download a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="24181-122">Použití `DownLoadFile` metoda ke stažení souboru, zadáte umístění cílového souboru jako řetězec nebo identifikátor URI a určení umístění, kam chcete uložit soubor, uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="24181-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="24181-123">Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a ukládá ji do `C:\Documents and Settings\All Users\Documents`, s uživatelským jménem `anonymous` a heslo necháte prázdné.</span><span class="sxs-lookup"><span data-stu-id="24181-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="24181-124">Protokol FTP používá `DownLoadFile` metoda odesílá informace, včetně hesel ve formátu prostého textu a neměli byste používat k přenosu citlivých informací.</span><span class="sxs-lookup"><span data-stu-id="24181-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24181-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24181-125">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="24181-126">Postupy: Nahrát soubor</span><span class="sxs-lookup"><span data-stu-id="24181-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="24181-127">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="24181-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
