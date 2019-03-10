---
title: Sledování SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: e2cb86a92e075d9117f2fe208f2044d4bc30dac9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710014"
---
# <a name="sql-tracking"></a><span data-ttu-id="72aee-102">Sledování SQL</span><span class="sxs-lookup"><span data-stu-id="72aee-102">SQL Tracking</span></span>
<span data-ttu-id="72aee-103">Tato ukázka předvádí, jak napsat vlastní sledování účastník SQL, který zapíše záznamy sledování k databázi SQL.</span><span class="sxs-lookup"><span data-stu-id="72aee-103">This sample demonstrates how to write a custom SQL tracking participant, that writes tracking records to a SQL database.</span></span> <span data-ttu-id="72aee-104">Windows Workflow Foundation (WF) umožňuje získat přehled o spuštění instance pracovního postupu pro sledování pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="72aee-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="72aee-105">Modul runtime sledování vysílá pracovního postupu při provádění pracovního postupu pro sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="72aee-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="72aee-106">Další informace o sledování pracovního postupu najdete v tématu [pracovního postupu pro sledování a trasování](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="72aee-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="72aee-107">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="72aee-107">To use this sample</span></span>

1.  <span data-ttu-id="72aee-108">Ověření je třeba SQL Server 2008, SQL Server 2008 Express nebo novější nainstalován.</span><span class="sxs-lookup"><span data-stu-id="72aee-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="72aee-109">Skripty zabaleny s ukázkou předpokládá použití instance SQL Express na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="72aee-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="72aee-110">Pokud máte jinou instanci, upravte prosím databázi související skripty před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="72aee-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2.  <span data-ttu-id="72aee-111">Vytvořte databázi serveru SQL Server sledování spuštěním Trackingsetup.cmd v adresáři skriptů (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span><span class="sxs-lookup"><span data-stu-id="72aee-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="72aee-112">Tím se vytvoří databázi s názvem TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="72aee-112">This creates a database called TrackingSample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="72aee-113">Tento skript vytvoří databázi na výchozí instanci systému SQL Express.</span><span class="sxs-lookup"><span data-stu-id="72aee-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="72aee-114">Pokud chcete nainstalovat na jinou instanci databáze, upravte skript Trackingsetup.cmd.</span><span class="sxs-lookup"><span data-stu-id="72aee-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>  
  
3.  <span data-ttu-id="72aee-115">Otevřete SqlTrackingSample.sln v sadě Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="72aee-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>  
  
4.  <span data-ttu-id="72aee-116">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="72aee-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="72aee-117">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="72aee-117">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="72aee-118">Okno prohlížeče se otevře a zobrazí výpisu adresáře pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="72aee-118">The browser window opens and shows the directory listing for the application.</span></span>  
  
6.  <span data-ttu-id="72aee-119">V prohlížeči klikněte na tlačítko StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="72aee-119">In the browser, click StockPriceService.xamlx.</span></span>  
  
7.  <span data-ttu-id="72aee-120">Prohlížeč zobrazí na stránce StockPriceService, který obsahuje místní službě WSDL adresu.</span><span class="sxs-lookup"><span data-stu-id="72aee-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="72aee-121">Zkopírujte tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="72aee-121">Copy this address.</span></span>  
  
     <span data-ttu-id="72aee-122">Příkladem adresy místní služby WSDL je `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="72aee-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>  
  
8.  <span data-ttu-id="72aee-123">Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], spustit klienta testu WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="72aee-123">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="72aee-124">Je umístěn v adresáři sady Microsoft Visual Studio 10.0\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="72aee-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>  
  
9. <span data-ttu-id="72aee-125">Testovací klient WCF, klikněte na tlačítko **souboru** nabídky a vybereme **přidat službu**.</span><span class="sxs-lookup"><span data-stu-id="72aee-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="72aee-126">Vložte adresu místní služby v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="72aee-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="72aee-127">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="72aee-127">Click **OK** to close the dialog.</span></span>  
  
10. <span data-ttu-id="72aee-128">Testovací klient WCF, dvakrát klikněte na tlačítko **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="72aee-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="72aee-129">Tím se otevře `GetStockPrice` operace, která přijímá jeden parametr, typ hodnoty `Contoso` a klikněte na tlačítko **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="72aee-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>  
  
11. <span data-ttu-id="72aee-130">Emitovaný sledování záznamů se zapisují do služby SQL database.</span><span class="sxs-lookup"><span data-stu-id="72aee-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="72aee-131">Chcete-li zobrazit záznamy sledování, otevřete TrackingSample databázi SQL Management Studio a přejděte do tabulky.</span><span class="sxs-lookup"><span data-stu-id="72aee-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="72aee-132">Další informace o nástroji SQL Server Management Studio najdete v tématu [Představujeme SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span><span class="sxs-lookup"><span data-stu-id="72aee-132">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="72aee-133">SQL Server 2008 Management Studio Express si můžete stáhnout [tady](https://go.microsoft.com/fwlink/?LinkId=180520).</span><span class="sxs-lookup"><span data-stu-id="72aee-133">SQL Server 2008 Management Studio Express can be downloaded [here](https://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="72aee-134">Zpracování dotazu select a systémem tabulky zobrazí data v rámci záznamy sledování, které jsou uložené v obou tabulkách.</span><span class="sxs-lookup"><span data-stu-id="72aee-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="72aee-135">Chcete-li odinstalovat vzorku</span><span class="sxs-lookup"><span data-stu-id="72aee-135">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="72aee-136">Spusťte skript theTrackingcleanup.cmd v adresáři ukázkové (\WF\Basic\Tracking\SqlTracking).</span><span class="sxs-lookup"><span data-stu-id="72aee-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="72aee-137">Trackingcleanup.cmd pokusí odstranit databázi v místním počítači SQL Express.</span><span class="sxs-lookup"><span data-stu-id="72aee-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="72aee-138">Pokud používáte jiné instance systému SQL server, upravte Trackingcleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="72aee-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="72aee-139">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="72aee-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="72aee-140">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="72aee-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="72aee-141">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="72aee-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="72aee-142">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="72aee-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a><span data-ttu-id="72aee-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72aee-143">See also</span></span>
- [<span data-ttu-id="72aee-144">Ukázky AppFabric monitorování</span><span class="sxs-lookup"><span data-stu-id="72aee-144">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
