---
title: Relace
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 539d897230fc69b2c30bd2a3930b305220d8345e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007887"
---
# <a name="session"></a>Relace
Ukázková relace ukazuje, jak implementovat kontrakt, který vyžaduje relaci. Relace poskytuje kontext pro provádění více operací. To umožňuje službám přidružení stavu dané relace tak, aby následné operace můžete použít stav předchozí operace. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje Kalkulačka služby. `ICalculator` Povolit sadu aritmetické operace, které mají být provedeny, a zajistit přitom ochranu spuštěné výsledek byl změněn kontraktu. Tato funkce je definována `ICalculatorSession` kontraktu. Služba zajišťuje stav na klienty, jako jsou volány více operací služby k provedení výpočtu. Klient může načíst aktuální výsledek voláním `Result()` a zrušte zaškrtnutí výsledek, který má nulovou voláním `Clear()`.  
  
 V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Nastavení <xref:System.ServiceModel.SessionMode> smlouvy na `Required` zajistí, že pokud kontrakt je přístupná přes konkrétní vazbu, vazba podporuje relací. Pokud se vazba nepodporuje relace je vyvolána výjimka. `ICalculatorSession` Rozhraní je definován tak, že je možné volat jednu nebo více operací, který změní spuštěné výsledek, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 Služba používá <xref:System.ServiceModel.InstanceContextMode> z <xref:System.ServiceModel.InstanceContextMode.PerSession> každou příchozí relace vytvořit vazbu kontext instance dané služby. To umožňuje službě udržovat výsledku spuštěný pro každou relaci v místní členské proměnné.  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 Při spuštění ukázky klient provede několik požadavků na serveru a vyžaduje výsledek, který se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
