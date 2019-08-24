---
title: Ukázka třídy XmlReader
ms.date: 03/30/2017
helpviewer_keywords:
- XML Reader
ms.assetid: 60e5848d-7d9c-4ea5-bed9-22758c9ac16c
ms.openlocfilehash: afc6679b6ca9ba8991ff928b664552e02f494c6a
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016054"
---
# <a name="xmlreader-sample"></a><span data-ttu-id="924a5-102">Ukázka třídy XmlReader</span><span class="sxs-lookup"><span data-stu-id="924a5-102">XmlReader Sample</span></span>

<span data-ttu-id="924a5-103">Ukázka XmlReader ukazuje zpracování těla zprávy pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="924a5-103">The XmlReader sample demonstrates the processing of a message body using an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="924a5-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="924a5-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="924a5-105">Byla přidána další operace `Sum`služby, která přijímá zprávu obsahující pole hodnot, které se mají přidat dohromady.</span><span class="sxs-lookup"><span data-stu-id="924a5-105">An additional service operation, `Sum`, has been added that accepts a message that contains an array of values to add together.</span></span> <span data-ttu-id="924a5-106">Služba přečte zprávu pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="924a5-106">The service reads the message using an <xref:System.Xml.XmlReader>.</span></span>

> [!NOTE]
> <span data-ttu-id="924a5-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="924a5-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="924a5-108">Rozhraní kalkulačky obsahuje operaci služby s názvem `Sum` , která <xref:System.ServiceModel.Channels.Message> přijímá parametr, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="924a5-108">The calculator interface includes a service operation named `Sum` that accepts a <xref:System.ServiceModel.Channels.Message> parameter, as shown in the following sample code.</span></span>

```csharp
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
    [OperationContract]
    Message Sum(Message message);
}
```

<span data-ttu-id="924a5-109">Přístup `Sum` klienta při prvním vytvoření pole celočíselných hodnot a následným vytvořením zprávy z pole a následným `Sum` voláním metody pomocí vytvořené zprávy, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="924a5-109">The client accesses `Sum` by first creating an array of integer values, then creating a message from the array, and then calling the `Sum` method using the created message, as shown in the following sample code.</span></span>

```csharp
CalculatorClient client = new CalculatorClient();
//...

// Call the Sum service operation.
int[] values = { 1, 2, 3, 4, 5 };
using (new OperationContextScope(client.InnerChannel))
{
    Message request = Message.CreateMessage(OperationContext.Current.OutgoingMessageHeaders.MessageVersion, "http://Microsoft.ServiceModel.Samples/ICalculator/Sum", values);
    Message reply = client.Sum(request);
    int sum = reply.GetBody<int>();

    Console.WriteLine("Sum(1,2,3,4,5) = {0}", sum);
}
```

<span data-ttu-id="924a5-110">Implementace operace `Sum` služby v rámci služby přistupuje k tělo zprávy <xref:System.Xml.XmlReader> pomocí objektu pro iteraci hodnotami, které se mají sečíst.</span><span class="sxs-lookup"><span data-stu-id="924a5-110">In the service, the implementation of the service operation `Sum` accesses the message body using an <xref:System.Xml.XmlReader> object to iterate through the values to sum.</span></span> <span data-ttu-id="924a5-111"><xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> Metoda je volána pro přístup k tělo zprávy, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="924a5-111">The <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> method is called to access the message body, as shown in the following sample code.</span></span>

```csharp
public int Sum(Message message)
{
    int sum = 0;
    string text = "";

    //The body of the message contains a list of numbers that are read
    //directly using an XmlReader.
    XmlReader body = message.GetReaderAtBodyContents ();
    while (body.Read())
    {
        text = body.ReadString().Trim();
        if (text.Length>0)
        {
            sum += Convert.ToInt32(text);
        }
    }
    body.Close();
    Message response = Message.CreateMessage(
       "http://Microsoft.ServiceModel.Samples/ICalculator/SumResponse",
       sum);
    return response;
}
```

<span data-ttu-id="924a5-112">Při spuštění ukázky se žádosti a odpovědi na operaci zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="924a5-112">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="924a5-113">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="924a5-113">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Sum(1,2,3,4,5) = 15

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="924a5-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="924a5-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="924a5-115">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="924a5-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="924a5-116">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="924a5-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="924a5-117">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="924a5-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="924a5-118">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="924a5-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="924a5-119">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="924a5-119">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="924a5-120">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="924a5-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="924a5-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="924a5-121">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\XmlReader`
