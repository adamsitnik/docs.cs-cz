---
title: Ukázka Začínáme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: 5f5418da63b2bc5fc9b20f5c262890b7a06ce5dd
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989925"
---
# <a name="getting-started-sample"></a>Ukázka Začínáme

Ukázka Začínáme ukazuje, jak implementovat typickou službu a typický klient pomocí Windows Communication Foundation (WCF). Tato ukázka je základem pro všechny ostatní základní ukázkové technologie.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

Služba popisuje operace, které provádí v kontraktu služby, který zveřejňuje veřejně jako metadata. Služba také obsahuje kód pro implementaci operací.

Klient obsahuje definici kontraktu služby a proxy třídy pro přístup ke službě. Proxy kód se generuje z metadat služby pomocí nástroje pro nástroj pro [metadata ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).

V [!INCLUDE[wv](../../../../includes/wv-md.md)]systému je služba hostovaná v aktivační službě Windows (WAS). V [!INCLUDE[wxp](../../../../includes/wxp-md.md)] systémech [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]a je hostovaný pomocí Internetová informační služba (IIS) a ASP.NET. Hostování služby ve službě IIS nebo služba mohla být aktivována automaticky při prvním otevření.

> [!NOTE]
> Pokud byste chtěli začít s ukázkou, která hostuje službu v konzolové aplikaci namísto služby IIS, přečtěte si ukázku pro [sebe v samostatném hostiteli](../../../../docs/framework/wcf/samples/self-host.md) .

Služba a klient určují podrobnosti přístupu v nastavení konfiguračního souboru, což poskytuje flexibilitu v době nasazení. To zahrnuje definici koncového bodu, která určuje adresu, vazbu a kontrakt. Vazba určuje přenos a detaily zabezpečení pro způsob, jakým má být služba k dispozici.

Služba konfiguruje chování za běhu k publikování metadat.

Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď. Kontrakt je definován `ICalculator` rozhraním, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení). Klient provede požadavky na určitou matematickou operaci a službu s výsledkem. Služba implementuje `ICalculator` kontrakt, který je definován v následujícím kódu.

```vb
' Define a service contract.
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>
     Public Interface ICalculator
        <OperationContract()>
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
```

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
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
}
```

Implementace služby vypočítá a vrátí příslušný výsledek, jak je znázorněno v následujícím příkladu kódu.

```vb
' Service class which implements the service contract.
Public Class CalculatorService
Implements ICalculator
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
Return n1 + n2
End Function

Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
Return n1 - n2
End Function

Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
Return n1 * n2
End Function

Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
Return n1 / n2
End Function
End Class
```

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

Služba zpřístupňuje koncový bod pro komunikaci se službou, definovaný pomocí konfiguračního souboru (Web. config), jak je znázorněno v následující ukázkové konfiguraci.

```xaml
<services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
        <!-- ICalculator is exposed at the base address provided by
         host: http://localhost/servicemodelsamples/service.svc.  -->
       <endpoint address=""
              binding="wsHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
       ...
    </service>
</services>
```

Služba zpřístupňuje koncový bod na základní adrese poskytované službou IIS nebo hostitelem. Vazba je nakonfigurovaná se standardem <xref:System.ServiceModel.WSHttpBinding>, který poskytuje komunikaci HTTP a standardní protokoly webových služeb pro účely adresování a zabezpečení. Smlouva je `ICalculator` implementovaná službou.

Jak je nakonfigurováno, může být služba k `http://localhost/servicemodelsamples/service.svc` dispozici klientovi ve stejném počítači. Aby mohli klienti na vzdálených počítačích přistupovat ke službě, je třeba zadat plně kvalifikovaný název domény namísto localhost.

Rozhraní ve výchozím nastavení nevystavuje metadata. V takovém případě služba zapíná <xref:System.ServiceModel.Description.ServiceMetadataBehavior> a zpřístupňuje koncový bod výměny metadat (MEX) na adrese. `http://localhost/servicemodelsamples/service.svc/mex` Následující konfigurace to demonstruje.

```xaml
<system.serviceModel>
  <services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
      ...
      <!-- the mex endpoint is exposed at
       http://localhost/servicemodelsamples/service.svc/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>

  <!--For debugging purposes set the includeExceptionDetailInFaults
   attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True"/>
        <serviceDebug includeExceptionDetailInFaults="False" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

Klient komunikuje pomocí daného typu kontraktu pomocí třídy klienta, která je generována [nástrojem Svcutil. exe (Nástroj pro metadata ServiceModel)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Tento vygenerovaný klient je obsažen v souboru generatedClient.cs nebo generatedClient. vb. Tento nástroj načte metadata pro danou službu a vygeneruje klienta pro použití klientskou aplikací ke komunikaci pomocí daného typu kontraktu. Hostovaná služba musí být k dispozici, aby vygenerovala klientský kód, protože služba se používá k načtení aktualizovaných metadat.

 Spusťte následující příkaz z příkazového řádku sady SDK v adresáři klienta pro vygenerování typovaného proxy serveru:

```console
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

Pokud chcete vygenerovat klienta v Visual Basic zadejte z příkazového řádku sady SDK následující:

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

Pomocí vygenerovaného klienta může klient získat přístup k danému koncovému bodu služby nakonfigurováním příslušné adresy a vazby. Podobně jako u služby používá klient konfigurační soubor (App. config) k určení koncového bodu, se kterým chce komunikovat. Konfigurace koncového bodu klienta se skládá z absolutní adresy koncového bodu služby, vazby a kontraktu, jak je znázorněno v následujícím příkladu.

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

Implementace klienta vytvoří instanci klienta a používá typové rozhraní k zahájení komunikace se službou, jak je znázorněno v následujícím příkladu kódu.

```vb
' Create a client
Dim client As New CalculatorClient()

' Call the Add service operation.
            Dim value1 = 100.0R
            Dim value2 = 15.99R
            Dim result = client.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

' Call the Subtract service operation.
value1 = 145.00R
value2 = 76.54R
result = client.Subtract(value1, value2)
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

' Call the Multiply service operation.
value1 = 9.00R
value2 = 81.25R
result = client.Multiply(value1, value2)
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

' Call the Divide service operation.
value1 = 22.00R
value2 = 7.00R
result = client.Divide(value1, value2)
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

'Closing the client gracefully closes the connection and cleans up resources
```

```csharp
// Create a client.
CalculatorClient client = new CalculatorClient();

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

// Call the Subtract service operation.
value1 = 145.00D;
value2 = 76.54D;
result = client.Subtract(value1, value2);
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

// Call the Multiply service operation.
value1 = 9.00D;
value2 = 81.25D;
result = client.Multiply(value1, value2);
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

// Call the Divide service operation.
value1 = 22.00D;
value2 = 7.00D;
result = client.Divide(value1, value2);
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

//Closing the client releases all communication resources.
client.Close();
```

Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

```output
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

Ukázka Začínáme zobrazuje standardní způsob, jak vytvořit službu a klienta. Druhá [základní](../../../../docs/framework/wcf/samples/basic-sample.md) sestavení v této ukázce k předvedení specifických funkcí produktu.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Hostování služby WCF ve spravované aplikaci](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Postupy: Hostování služby WCF ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
