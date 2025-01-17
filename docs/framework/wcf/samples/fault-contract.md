---
title: Chyba – kontrakt
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 907497101c13e1f62ff2abb5da563178c9643c6c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039662"
---
# <a name="fault-contract"></a>Chyba – kontrakt
Ukázka smlouvy o selhání ukazuje, jak sdělit informace o chybě ze služby klientovi. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)s nějakým dalším kódem přidaným do služby pro převod vnitřní výjimky na chybu. Klient se pokusí provést dělení nulou, aby vynutil chybový stav služby.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Smlouva kalkulačky byla upravena tak, aby <xref:System.ServiceModel.FaultContractAttribute> obsahovala, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 Atribut označuje, že operace může vracet chybu typu `MathFault`. `Divide` <xref:System.ServiceModel.FaultContractAttribute> Chyba může být libovolného typu, který lze serializovat. V tomto případě `MathFault` je to kontrakt dat, jak je znázorněno níže:  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 `Divide` Metoda<xref:System.ServiceModel.FaultException%601> vyvolá výjimku, pokud dojde k výjimce nulou, jak je znázorněno v následujícím ukázkovém kódu. Tato výjimka vede k odeslání chyby klientovi.  
  
```csharp
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 Kód klienta vynutí chybu tím, že si vyžádá dělení nulou. Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. Uvidíte, že dělení nulou se hlásí jako chyba. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 Klient to provede zachycením příslušné `FaultException<MathFault>` výjimky:  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Ve výchozím nastavení se klientovi neodesílají podrobnosti o neočekávaných výjimkách, aby se předešlo podrobnostem implementace služby z řídicího panelu zabezpečené hranice služby. `FaultContract`poskytuje způsob, jak popsat chyby ve smlouvě a označovat určité typy výjimek, které jsou vhodné pro přenos klientovi. `FaultException<T>`poskytuje mechanizmus běhu pro posílání chyb příjemcům.  
  
 Je však vhodné zobrazit interní podrobnosti o selhání služby při ladění. Chcete-li vypnout zabezpečené chování popsané výše, můžete určit, že podrobnosti o každé neošetřené výjimce na serveru by měly být zahrnuty do chyby, která je odeslána klientovi. To je provedeno nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> na. `true` Můžete ho buď nastavit v kódu, nebo v konfiguraci, jak je znázorněno v následující ukázce.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Kromě toho musí být chování přidruženo ke službě `behaviorConfiguration` nastavením atributu služby v konfiguračním souboru na hodnotu "CalculatorServiceBehavior".  
  
 Chcete-li zachytit taková selhání klienta, musí být zachycena neobecná <xref:System.ServiceModel.FaultException> .  
  
 Toto chování by se mělo používat jenom pro účely ladění a nikdy by nemělo být povolené v produkčním prostředí.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
