---
title: Zabezpečení zpráv s uživatelským jménem
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 791c77999b246c1a63767a937189fc6cb970e08f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607969"
---
# <a name="message-security-user-name"></a>Zabezpečení zpráv s uživatelským jménem
Tento příklad ukazuje, jak implementovat aplikaci, která používá WS-Security s ověřením uživatelské jméno pro klienta a vyžaduje server ověřování pomocí certifikátu x.509 v3 serveru. Všechny zprávy aplikace mezi klientem a serverem jsou podepsaný a zašifrovaný. Ve výchozím nastavení, uživatelské jméno a heslo, které poskytl klient, slouží k přihlášení k platný účet Windows. Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md). Tento příklad se skládá z programu konzoly klienta (Client.exe) a knihovna služby (Service.dll) hostované v Internetové informační služby (IIS). Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tento příklad také znázorňuje:  
  
-   Výchozí mapování na účty Windows tak, že lze provést další ověření.  
  
-   Jak získat přístup k identity volajícího z kódu služby.  
  
 Služba poskytuje jeden koncový bod pro komunikaci se službou, která je definována je používán konfigurační soubor Web.config. Koncový bod se skládá z adresy, vazby a kontrakt. Je vazba konfigurována se standardní [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), která ve výchozím nastavení používá zabezpečení zpráv. Tato ukázka nastaví standardní [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) používat uživatelské jméno ověřování klientů. Chování Určuje, že má být použit pro ověřování služby jsou přihlašovací údaje uživatele. Certifikát serveru musí obsahovat stejnou hodnotu pro název subjektu, jako `findValue` atribut [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Konfigurace koncového bodu klienta se skládá z absolutní adresu pro koncový bod služby, vazba a kontrakt. Klient vazby je nakonfigurovaný s příslušnou `securityMode` a `authenticationMode`. Při spuštění ve scénáři mezi počítači, musíte změnit adresu koncového bodu služby odpovídajícím způsobem.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Implementace klienta nastaví uživatelské jméno a heslo pro použití.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Dávkový soubor Setup.bat součástí ukázky MessageSecurity umožňuje nakonfigurovat server se příslušný certifikát ke spuštění prostředí aplikace, které vyžadují zabezpečení na základě certifikátů. Dávkový soubor může běžet ve dvou režimech. Pokud chcete spustit dávkový soubor v režimu jednoho počítače, zadejte `setup.bat` na příkazovém řádku. Ke spuštění v režimu typ služby `setup.bat service`. Tento režim se použijte při spuštění ukázky na počítačích. Zobrazit postup nastavení na konci tohoto tématu, kde podrobnosti.  
  
 Následující body nabízí stručný přehled o různých částech dávkové soubory.  
  
-   Vytváří se certifikát serveru  
  
     Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     % Proměnná % název_serveru Určuje název serveru. Certifikát je uložen v úložišti LocalMachine. Pokud Setup.bat dávkový soubor se spustí s parametrem služby (například `setup.bat service`) název_serveru % obsahuje název plně kvalifikované domény počítače.  Jinak je výchozí hodnota je localhost.  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta  
  
     Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Udělení oprávnění pro privátní klíč certifikátu  
  
     Následující řádky do dávkový soubor Setup.bat uložené v úložišti LocalMachine přístupné pro certifikát serveru Ujistěte se, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    >  Pokud používáte mimo USA Anglickou verzi Windows, musíte upravit soubor Setup.bat a nahraďte `NT AUTHORITY\NETWORK SERVICE` název účtu se místní ekvivalent.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Ujistěte se, že cesta obsahuje složku, ve kterém jsou umístěny Makecert.exe a FindPrivateKey.exe.  
  
2.  Spusťte Setup.bat z instalační složky s ukázkou v příkazovém řádku pro vývojáře pro sadu Visual Studio otevřeného s oprávněními správce. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat je navržena pro spouštění na příkazovém řádku pro vývojáře pro sadu Visual Studio. To vyžaduje, aby proměnné prostředí path v bodu do adresáře, ve kterém je nainstalována sada SDK. Tato proměnná prostředí je nastavena automaticky v rámci příkazového řádku pro vývojáře pro sadu Visual Studio.  
  
3.  Ověření přístupu ke službě pomocí prohlížeče tak, že zadáte adresu `http://localhost/servicemodelsamples/service.svc`.
  
4.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
5.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1.  Vytvoření adresáře na počítači se službou. Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby.  
  
2.  Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3.  Vytvoření adresáře v klientském počítači pro binární soubory klienta.  
  
4.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.  
  
5.  Na serveru, spusťte `setup.bat service` otevřeného v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6.  Upravit soubor Web.config tak, aby odrážely nový název certifikátu (u atributu findValue v aplikaci prvku serviceCertificate) která je stejná jako plně kvalifikovaný název domény počítače`.`  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.  
  
9. Na straně klienta spouštění ImportServiceCert.bat v příkazovém řádku pro vývojáře pro sadu Visual Studio otevřeného s oprávněními správce. To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
10. Na klientském počítači spusťte Client.exe z příkazového řádku. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
-   Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích. Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Viz také:
