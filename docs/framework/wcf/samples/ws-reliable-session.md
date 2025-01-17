---
title: Spolehlivá relace WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 38eef85446568dd6cac09c4fdc3fb76d958f423c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424492"
---
# <a name="ws-reliable-session"></a>Spolehlivá relace WS
Tato ukázka demonstruje použití spolehlivých relací. Spolehlivé relace poskytují podporu pro spolehlivé zasílání zpráv a relací. Spolehlivé zasílání zpráv zopakuje komunikaci při selhání a umožňuje zadat záruky doručování, například doručení zpráv v daném pořadí. Relace uchovávají stav pro klienty mezi voláními. Ukázka implementuje relace pro udržování stavu klienta a určuje záruku doručení v daném pořadí.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky. Funkce spolehlivé relace jsou povolené a nakonfigurované v konfiguračních souborech aplikací pro klienta a službu.  
  
 V této ukázce je služba hostovaná ve službě Internetová informační služba (IIS) a klient je Konzolová aplikace (. exe).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Ukázka používá `wsHttpBinding`. Vazba je určena v konfiguračních souborech pro klienta i službu. Typ vazby je zadán v atributu `binding` elementu koncového bodu, jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Koncový bod obsahuje atribut `bindingConfiguration`, který odkazuje na konfiguraci vazby s názvem "Binding1". Konfigurace vazby umožňuje spolehlivé relace nastavením atributu `enabled` [\<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) na `true`. Záruky doručení pro seřazené relace jsou ovládány nastavením seřazeného atributu na `true` nebo `false`. Výchozí hodnota je `true`.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Třída implementace služby implementuje <xref:System.ServiceModel.InstanceContextMode.PerSession> vytváření instancí pro udržování samostatné instance třídy pro každého klienta, jak je znázorněno v následujícím ukázkovém kódu.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
