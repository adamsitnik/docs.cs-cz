---
title: Kódování MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: ab8abdf79304037f2b4039407115a3f64a0afa4e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424074"
---
# <a name="mtom-encoding"></a>Kódování MTOM
Tato ukázka demonstruje použití kódování zprávy MTOM (Message Transmission Optimization Mechanism) pomocí WSHttpBinding. MTOM je mechanismus pro přenos rozsáhlých binárních příloh se zprávami SOAP jako nezpracovaných bajtů, což umožňuje menší zprávy.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Ve výchozím nastavení WSHttpBinding odesílá a přijímá zprávy jako normální text XML. Chcete-li povolit odesílání a přijímání zpráv MTOM, nastavte atribut `messageEncoding` v konfiguraci vazby (jako v následujícím příkladu kódu) nebo přímo na vazbu pomocí vlastnosti `MessageEncoding`. Služba nebo klient teď může odesílat a přijímat zprávy MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 Kodér MTOM může optimalizovat pole bajtů a datových proudů. V této ukázce operace používá parametr `Stream` a je proto možné ji optimalizovat.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 Kontrakt vybraný pro tento příklad odesílá binární data do služby a přijímá počet bajtů odeslaných jako návratovou hodnotu. Po instalaci služby a spuštění klienta se zobrazí číslo 1000, které indikuje, že byly přijaty všechny 1000 bajtů. Zbývající část výstupu obsahuje optimalizované a neoptimalizované velikosti zpráv pro různé datové části.  
  
```console
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 Účelem použití nástroje MTOM je optimalizace přenosu rozsáhlých binárních datových částí. Odeslání zprávy protokolu SOAP pomocí nástroje MTOM má znatelný nárok na malé binární datové části, ale stane se skvělým úsporou, pokud se rozrůstá o několik tisíc bajtů. Důvodem je to, že normální text XML kóduje binární data pomocí Base64, který vyžaduje čtyři znaky pro každé tři bajty a zvětšuje velikost dat o jednu třetinu. MTOM dokáže přenášet binární data jako nezpracované bajty, ušetřit čas kódování a dekódování a výsledkem je menší počet zpráv. V porovnání s dnešními obchodními dokumenty a digitálními fotografiemi je malá prahová hodnota několika tisíc bajtů.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
