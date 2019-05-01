---
title: Zprostředkovatel tokenu
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: 9c10d67093fb09cb97f2010926ebaa6176df86c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965656"
---
# <a name="token-provider"></a><span data-ttu-id="134dc-102">Zprostředkovatel tokenu</span><span class="sxs-lookup"><span data-stu-id="134dc-102">Token Provider</span></span>
<span data-ttu-id="134dc-103">Tento příklad ukazuje, jak implementovat vlastní zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="134dc-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="134dc-104">Poskytovatel tokenu ve Windows Communication Foundation (WCF) slouží k poskytnutí přihlašovacích údajů k zabezpečení infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="134dc-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="134dc-105">Poskytovatel tokenu obecně zkontroluje cíl a problémů příslušné přihlašovací údaje tak, aby infrastruktura zabezpečení se dají zabezpečit zprávy.</span><span class="sxs-lookup"><span data-stu-id="134dc-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="134dc-106">WCF se dodává s výchozí poskytovatel tokenu přihlašovacích údajů správce.</span><span class="sxs-lookup"><span data-stu-id="134dc-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="134dc-107">WCF se také dodává se [!INCLUDE[infocard](../../../../includes/infocard-md.md)] zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="134dc-107">WCF also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="134dc-108">Vlastní poskytovatele tokenů jsou užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="134dc-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="134dc-109">Pokud máte úložiště přihlašovacích údajů, které tyto poskytovatele tokenů nemůže pracovat s.</span><span class="sxs-lookup"><span data-stu-id="134dc-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="134dc-110">Pokud chcete poskytnout vlastní vlastní mechanismus pro transformaci přihlašovacích údajů z bodu, když uživatel zadá podrobnosti, které chcete při Architektura klienta WCF používá přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="134dc-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="134dc-111">Pokud vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="134dc-111">If you are building a custom token.</span></span>

 <span data-ttu-id="134dc-112">Tento příklad ukazuje, jak vytvořit vlastního zprostředkovatele tokenů, který transformuje vstup od uživatele do jiného formátu.</span><span class="sxs-lookup"><span data-stu-id="134dc-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>

 <span data-ttu-id="134dc-113">Souhrnně řečeno, tento příklad znázorňuje následující:</span><span class="sxs-lookup"><span data-stu-id="134dc-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="134dc-114">Jak klient může ověřit pomocí dvojice uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="134dc-114">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="134dc-115">Jak klienta lze nakonfigurovat pomocí vlastního zprostředkovatele tokenů.</span><span class="sxs-lookup"><span data-stu-id="134dc-115">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="134dc-116">Jak na serveru můžete ověřit pomocí hesla s vlastní přihlašovací údaje klienta <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , který ověří, že uživatelské jméno a heslo odpovídat.</span><span class="sxs-lookup"><span data-stu-id="134dc-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>

- <span data-ttu-id="134dc-117">Jak ověření serveru klientem pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="134dc-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="134dc-118">Tento příklad také ukazuje, jak identitu volajícího, jež je přístupné po dokončení procesu vlastních tokenů ověřování.</span><span class="sxs-lookup"><span data-stu-id="134dc-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>

 <span data-ttu-id="134dc-119">Služba poskytuje jeden koncový bod pro komunikaci se službou, definované pomocí konfiguračního souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="134dc-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="134dc-120">Koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="134dc-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="134dc-121">Je vazba konfigurována se standardní `wsHttpBinding`, který používá zabezpečení zpráv ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="134dc-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="134dc-122">Tato ukázka nastaví standardní `wsHttpBinding` používat uživatelské jméno ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="134dc-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="134dc-123">Služba nakonfiguruje taky certifikát služby pomocí chování serviceCredentials.</span><span class="sxs-lookup"><span data-stu-id="134dc-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="134dc-124">Chování serviceCredentials umožňuje nakonfigurovat certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="134dc-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="134dc-125">Certifikát služby se používá pro klienta k ověření služby a zajistit ochranu zprávy.</span><span class="sxs-lookup"><span data-stu-id="134dc-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="134dc-126">Následující konfigurace odkazuje nainstalovat během instalace ukázka, jak je popsáno v následující pokyny k instalaci certifikátu localhost.</span><span class="sxs-lookup"><span data-stu-id="134dc-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
        The serviceCredentials behavior allows one to define a service certificate.
        A service certificate is used by a client to authenticate the service and provide message protection.
        This configuration references the "localhost" certificate installed during the setup instructions.
        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
```

 <span data-ttu-id="134dc-127">Konfigurace koncového bodu klienta se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazba a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="134dc-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="134dc-128">Klient vazby je nakonfigurovaný s příslušnou `Mode` a zpráva `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="134dc-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
              address="http://localhost:8000/servicemodelsamples/service"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator">
    </endpoint>
  </client>

  <bindings>
    <wsHttpBinding>
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
</system.serviceModel>
```

 <span data-ttu-id="134dc-129">Následující kroky ukazují, jak vytvořit vlastního zprostředkovatele tokenů a integrovat architektury WCF zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="134dc-129">The following steps show how to develop a custom token provider and integrate it with the WCF security framework:</span></span>

1. <span data-ttu-id="134dc-130">Napište vlastního zprostředkovatele tokenů.</span><span class="sxs-lookup"><span data-stu-id="134dc-130">Write a custom token provider.</span></span>

     <span data-ttu-id="134dc-131">Ukázka implementuje vlastního zprostředkovatele tokenů, který získá uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="134dc-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="134dc-132">Heslo musí odpovídat toto uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="134dc-132">The password must match this username.</span></span> <span data-ttu-id="134dc-133">Tento vlastní zprostředkovatel tokenu je pouze pro demonstrační účely a nedoporučuje se používat pro reálné nasazení.</span><span class="sxs-lookup"><span data-stu-id="134dc-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>

     <span data-ttu-id="134dc-134">K provedení této úlohy je odvozen vlastního zprostředkovatele tokenů <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy a přepsání <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metody.</span><span class="sxs-lookup"><span data-stu-id="134dc-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="134dc-135">Tato metoda vytvoří a vrátí nový `UserNameSecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="134dc-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>

    ```
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
        // obtain username and password from the user using console window
        string username = GetUserName();
        string password = GetPassword();
        Console.WriteLine("username: {0}", username);

        // return new UserNameSecurityToken containing information obtained from user
        return new UserNameSecurityToken(username, password);
    }
    ```

2. <span data-ttu-id="134dc-136">Správce tokenů zabezpečení vlastního zápisu.</span><span class="sxs-lookup"><span data-stu-id="134dc-136">Write custom security token manager.</span></span>

     <span data-ttu-id="134dc-137"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , který je do ní předán v `CreateSecurityTokenProvider` metody.</span><span class="sxs-lookup"><span data-stu-id="134dc-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="134dc-138">Správce tokenů zabezpečení se také používá k vytvoření ověřovací data tokenu a serializátor, ale nejsou uvedené v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="134dc-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="134dc-139">V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenProvider` požadovaná metoda vracet poskytovatele tokenu, kterého vlastní uživatelské jméno předané požadavky tokenu určit uživatelské jméno zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="134dc-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>

    ```
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        MyUserNameClientCredentials myUserNameClientCredentials;

        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)
            : base(myUserNameClientCredentials)
        {
            this.myUserNameClientCredentials = myUserNameClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // if token requirement matches username token return custom username token provider
            // otherwise use base implementation
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)
            {
                return new MyUserNameTokenProvider();
            }
            else
            {
                return base.CreateSecurityTokenProvider(tokenRequirement);
            }
        }
    }
    ```

3. <span data-ttu-id="134dc-140">Zápis vlastních klientských přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="134dc-140">Write a custom client credential.</span></span>

     <span data-ttu-id="134dc-141">Třída přihlašovacích údajů klienta se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro proxy serveru klienta a vytvoří token správce, který se používá k získání ověřovací data tokenu, poskytovatele tokenů a serializátoru tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="134dc-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>

    ```
    public class MyUserNameClientCredentials : ClientCredentials
    {
        public MyUserNameClientCredentials()
            : base()
        {
        }

        protected override ClientCredentials CloneCore()
        {
            return new MyUserNameClientCredentials();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            // return custom security token manager
            return new MyUserNameSecurityTokenManager(this);
        }
    }
    ```

4. <span data-ttu-id="134dc-142">Konfigurace klienta pro použití vlastního klienta přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="134dc-142">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="134dc-143">Aby klienti měli používat přihlašovací údaje, které vlastní vzorek odstraní výchozí třídu přihlašovacích údajů klienta a poskytuje novou třídu přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="134dc-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>

    ```
    static void Main()
    {
        // ...
           // Create a client with given client endpoint configuration
          CalculatorClient client = new CalculatorClient();

          // set new credentials
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());
       // ...
    }
    ```

 <span data-ttu-id="134dc-144">Na službu, použijte k zobrazení informací volajícího, <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="134dc-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="134dc-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Obsahuje deklarace identity informace o aktuální volajícím.</span><span class="sxs-lookup"><span data-stu-id="134dc-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 <span data-ttu-id="134dc-146">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="134dc-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="134dc-147">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="134dc-147">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="134dc-148">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="134dc-148">Setup Batch File</span></span>
 <span data-ttu-id="134dc-149">Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušný certifikát ke spuštění aplikace v místním prostředí, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="134dc-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="134dc-150">Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.</span><span class="sxs-lookup"><span data-stu-id="134dc-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="134dc-151">Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="134dc-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="134dc-152">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="134dc-152">Creating the server certificate.</span></span>

     <span data-ttu-id="134dc-153">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="134dc-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="134dc-154">`%SERVER_NAME%` Proměnné Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="134dc-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="134dc-155">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="134dc-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="134dc-156">Výchozí hodnota v tomto souboru služby batch je localhost.</span><span class="sxs-lookup"><span data-stu-id="134dc-156">The default value in this batch file is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="134dc-157">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="134dc-157">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="134dc-158">Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="134dc-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="134dc-159">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="134dc-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="134dc-160">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="134dc-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
>  <span data-ttu-id="134dc-161">Dávkový soubor Setup.bat je navržena pro spouštění na příkazovém řádku sady SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="134dc-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="134dc-162">To vyžaduje, aby proměnné prostředí MSSDK bodu do adresáře, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="134dc-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="134dc-163">Tato proměnná prostředí je nastavena automaticky v příkazovém řádku Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="134dc-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="134dc-164">K nastavení a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="134dc-164">To set up and build the sample</span></span>

1. <span data-ttu-id="134dc-165">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="134dc-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="134dc-166">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="134dc-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="134dc-167">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="134dc-167">To run the sample on the same computer</span></span>

1. <span data-ttu-id="134dc-168">Spusťte Setup.bat z instalační složky s ukázkou v příkazovém řádku aplikace Visual Studio 2012 otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="134dc-168">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="134dc-169">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="134dc-169">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="134dc-170">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="134dc-170">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="134dc-171">Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="134dc-171">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="134dc-172">Spusťte service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="134dc-172">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="134dc-173">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="134dc-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="134dc-174">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="134dc-174">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="134dc-175">Do příkazového řádku uživatelské jméno zadejte uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="134dc-175">At the username prompt, type a user name.</span></span>  
  
5. <span data-ttu-id="134dc-176">Na výzvu k zadání hesla použijte stejný řetězec, který byl zadán pro řádek uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="134dc-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6. <span data-ttu-id="134dc-177">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="134dc-177">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="134dc-178">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="134dc-178">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="134dc-179">Vytvoření adresáře na počítači se službou pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="134dc-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="134dc-180">Programové soubory nástroje služby zkopírujte do adresáře služby na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="134dc-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="134dc-181">Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="134dc-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="134dc-182">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="134dc-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="134dc-183">Soubor Service.exe.config musí aktualizovat tak, aby odrážely tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="134dc-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="134dc-184">Certifikát serveru můžete vytvořit tak, že upravíte dávkový soubor Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="134dc-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="134dc-185">Všimněte si, že se soubor setup.bat musí spustit na příkazovém řádku pro vývojáře pro sadu Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="134dc-185">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="134dc-186">Je nutné nastavit `%SERVER_NAME%` proměnných hostitele plně kvalifikovaný název počítače, který se používá k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="134dc-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="134dc-187">Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="134dc-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="134dc-188">Nemusíte to dělat, když certifikátu serveru vydanému klienta důvěryhodného vystavitele.</span><span class="sxs-lookup"><span data-stu-id="134dc-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="134dc-189">V souboru Service.exe.config na počítači se službou změňte hodnotu z bázové adresy pro zadejte název počítače plně kvalifikovaný, místo localhost.</span><span class="sxs-lookup"><span data-stu-id="134dc-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="134dc-190">Na počítači se službou spusťte z příkazového řádku service.exe.</span><span class="sxs-lookup"><span data-stu-id="134dc-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="134dc-191">Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="134dc-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="134dc-192">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="134dc-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="134dc-193">Na klientském počítači spusťte `Client.exe` z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="134dc-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="134dc-194">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="134dc-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="134dc-195">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="134dc-195">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="134dc-196">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="134dc-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
