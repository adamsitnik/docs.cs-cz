---
title: 'Vzory návrhu: Vzor publikování–odběr založený na seznamu'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: e98fab5c8e7570917a4ba755fa372832fe0b26b5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312043"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="1af67-102">Vzory návrhu: Vzor publikování–odběr založený na seznamu</span><span class="sxs-lookup"><span data-stu-id="1af67-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="1af67-103">Tento příklad znázorňuje vzor založený na seznamu publikování a odběru implementovaná jako program Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1af67-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1af67-104">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="1af67-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1af67-105">Návrhový vzor založený na seznamu publikování a odběru je popsán v publikaci Microsoft Patterns a postupy [vzory integrace](https://go.microsoft.com/fwlink/?LinkId=95894).</span><span class="sxs-lookup"><span data-stu-id="1af67-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://go.microsoft.com/fwlink/?LinkId=95894).</span></span> <span data-ttu-id="1af67-106">Model publikování a odběru předává informace do kolekce příjemců, kteří se přihlásili k odběru tématu informace.</span><span class="sxs-lookup"><span data-stu-id="1af67-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="1af67-107">Na základě seznamu publikování a odběru udržuje seznam předplatitelů.</span><span class="sxs-lookup"><span data-stu-id="1af67-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="1af67-108">Po informace sdílet kopii posílá každému odběrateli v seznamu.</span><span class="sxs-lookup"><span data-stu-id="1af67-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="1af67-109">V této ukázce dynamické na základě seznamu vzorec, kde můžou klienti přihlášení k odběru nebo odběr tak často, podle potřeby publikování a odběru.</span><span class="sxs-lookup"><span data-stu-id="1af67-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="1af67-110">Ukázka založený na seznamu publikování a odběru se skládá z klienta, služby a data zdrojového programu.</span><span class="sxs-lookup"><span data-stu-id="1af67-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="1af67-111">Může existovat více než jednoho klienta a s více než jeden data zdrojového programu.</span><span class="sxs-lookup"><span data-stu-id="1af67-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="1af67-112">Klienti předplatné ke službě, dostávat oznámení a odhlášení odběru.</span><span class="sxs-lookup"><span data-stu-id="1af67-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="1af67-113">Programy pro zdroj dat odeslat informace o službě a sdílené s všichni aktuální předplatitelé.</span><span class="sxs-lookup"><span data-stu-id="1af67-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="1af67-114">V tomto zdroji ukázka, klient a data jsou programy konzoly (soubory .exe) a služba je knihovna (.dll) hostované v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="1af67-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="1af67-115">Zdrojová aktivita klienta a data jsou viditelné v klientských počítačích.</span><span class="sxs-lookup"><span data-stu-id="1af67-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="1af67-116">Služba používá duplexní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="1af67-116">The service uses duplex communication.</span></span> <span data-ttu-id="1af67-117">`ISampleContract` Kontrakt služby s oblastí `ISampleClientCallback` kontrakt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="1af67-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="1af67-118">Služba implementuje přihlásit k odběru a zrušení odběru operace služby, které klienti používají k připojení nebo ponechte seznam předplatitelů.</span><span class="sxs-lookup"><span data-stu-id="1af67-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="1af67-119">Služba také implementuje `PublishPriceChange` operace služby, která volá program zdroje dat k poskytování služby novými informacemi.</span><span class="sxs-lookup"><span data-stu-id="1af67-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="1af67-120">Implementuje klientskou aplikaci `PriceChange` operace služby, která volá službu oznámit všichni předplatitelé změna ceny.</span><span class="sxs-lookup"><span data-stu-id="1af67-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,   
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 <span data-ttu-id="1af67-121">Služba události rozhraní .NET Framework používá jako mechanismus k informování všichni předplatitelé o nové informace.</span><span class="sxs-lookup"><span data-stu-id="1af67-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="1af67-122">Když se klient připojuje služby podle volání přihlásit k odběru, poskytuje obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1af67-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="1af67-123">Když klient opustí, zrušení odběru své obslužné rutině události z události.</span><span class="sxs-lookup"><span data-stu-id="1af67-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="1af67-124">Když zdroji dat volá Služba hlášení změna ceny, službu vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="1af67-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="1af67-125">Volá se každá instance služby, jednu pro každého klienta, která se připojila a způsobí, že jejich obslužných rutin událostí k provedení.</span><span class="sxs-lookup"><span data-stu-id="1af67-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="1af67-126">Každá obslužná rutina události předá informace o jeho klienta pomocí funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="1af67-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
```  
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 <span data-ttu-id="1af67-127">Při spuštění ukázku spusťte několik klientů.</span><span class="sxs-lookup"><span data-stu-id="1af67-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="1af67-128">Klienti přihlásit ke službě.</span><span class="sxs-lookup"><span data-stu-id="1af67-128">The clients subscribe to the service.</span></span> <span data-ttu-id="1af67-129">Spusťte program zdroje dat, který odesílá informace do služby.</span><span class="sxs-lookup"><span data-stu-id="1af67-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="1af67-130">Služba předá informace všichni předplatitelé.</span><span class="sxs-lookup"><span data-stu-id="1af67-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="1af67-131">Zobrazit aktivitu na každého klienta konzoly potvrzení, přijímání informace.</span><span class="sxs-lookup"><span data-stu-id="1af67-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="1af67-132">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="1af67-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="1af67-133">K nastavení a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="1af67-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="1af67-134">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1af67-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1af67-135">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1af67-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="1af67-136">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="1af67-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="1af67-137">Test, můžete přístup ke službě pomocí prohlížeče zadáním následující adresy: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="1af67-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="1af67-138">Stránka s potvrzením má být zobrazena v odpovědi.</span><span class="sxs-lookup"><span data-stu-id="1af67-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="1af67-139">Spustit Client.exe z \client\bin\\, ze složky specifické pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="1af67-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="1af67-140">Činnost klienta se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="1af67-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="1af67-141">Spuštění několika klienty.</span><span class="sxs-lookup"><span data-stu-id="1af67-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="1af67-142">Spustit Datasource.exe z \datasource\bin\\, ze složky specifické pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="1af67-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="1af67-143">Aktivita zdroje dat se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="1af67-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="1af67-144">Jakmile se zdroje dat se odesílá informace do služby, jeho by měly být předány každého klienta.</span><span class="sxs-lookup"><span data-stu-id="1af67-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="1af67-145">Pokud klient, zdroj dat a aplikací služby nejsou schopné komunikovat, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1af67-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="1af67-146">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="1af67-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="1af67-147">Nastavení služby počítače:</span><span class="sxs-lookup"><span data-stu-id="1af67-147">Set up the service machine:</span></span>  
  
    1.  <span data-ttu-id="1af67-148">Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="1af67-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="1af67-149">Soubor Setupvroot.bat ze služby batch [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) je možné vytvořit na disku a virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="1af67-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2.  <span data-ttu-id="1af67-150">Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do ServiceModelSamples virtuálního adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="1af67-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="1af67-151">Nezapomeňte zahrnout soubory v adresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="1af67-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3.  <span data-ttu-id="1af67-152">Testovací službě můžete dostat z klientského počítače pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="1af67-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="1af67-153">Nastavte klientské počítače:</span><span class="sxs-lookup"><span data-stu-id="1af67-153">Set up the client machines:</span></span>  
  
    1.  <span data-ttu-id="1af67-154">Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientských počítačů.</span><span class="sxs-lookup"><span data-stu-id="1af67-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2.  <span data-ttu-id="1af67-155">V konfiguračním souboru každý klient změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="1af67-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="1af67-156">Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="1af67-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="1af67-157">Nastavte počítač pro zdroj dat:</span><span class="sxs-lookup"><span data-stu-id="1af67-157">Set up the data source machine:</span></span>  
  
    1.  <span data-ttu-id="1af67-158">Zkopírujte soubory programu zdroje dat ze složky \datasource\bin\ v rámci složky specifické pro jazyk, na počítač pro datové zdroje.</span><span class="sxs-lookup"><span data-stu-id="1af67-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2.  <span data-ttu-id="1af67-159">V souboru konfigurace zdroje dat změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="1af67-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="1af67-160">Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="1af67-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="1af67-161">Na klientské počítače spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="1af67-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="1af67-162">Na zdrojovém počítači data spusťte z příkazového řádku Datasource.exe.</span><span class="sxs-lookup"><span data-stu-id="1af67-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1af67-163">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="1af67-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1af67-164">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1af67-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1af67-165">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="1af67-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1af67-166">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1af67-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
