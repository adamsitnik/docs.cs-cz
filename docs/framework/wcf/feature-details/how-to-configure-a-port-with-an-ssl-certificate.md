---
title: 'Postupy: Konfigurace portu s certifikátem SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: d709123895f361c1d2268a218b4163c8d195e1b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345583"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="a3c1f-102">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="a3c1f-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="a3c1f-103">Při vytváření služby Windows Communication Foundation (WCF) v místním prostředí s <xref:System.ServiceModel.WSHttpBinding> třídy zabezpečení přenosu používá, musíte také nakonfigurovat port pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="a3c1f-104">Pokud vytváříte nejsou v místním prostředí služby, můžete hostovat vaše služba v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="a3c1f-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="a3c1f-105">Další informace najdete v tématu [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="a3c1f-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="a3c1f-106">Konfigurace portu, nástroj, který můžete použít závisí na operační systém, který běží na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="a3c1f-107">Pokud používáte [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj HttpCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-107">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool.</span></span> <span data-ttu-id="a3c1f-108">S [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] tento nástroj je nainstalován.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-108">With [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] this tool is installed.</span></span> <span data-ttu-id="a3c1f-109">S [!INCLUDE[wxp](../../../../includes/wxp-md.md)], si můžete stáhnout nástroj na [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606).</span><span class="sxs-lookup"><span data-stu-id="a3c1f-109">With [!INCLUDE[wxp](../../../../includes/wxp-md.md)], you can download the tool at [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606).</span></span> <span data-ttu-id="a3c1f-110">Další informace najdete v tématu [Httpcfg přehled](https://go.microsoft.com/fwlink/?LinkId=88605).</span><span class="sxs-lookup"><span data-stu-id="a3c1f-110">For more information, see [Httpcfg Overview](https://go.microsoft.com/fwlink/?LinkId=88605).</span></span> <span data-ttu-id="a3c1f-111">[Dokumentace nástrojů podpory Windows Support Tools](https://go.microsoft.com/fwlink/?LinkId=94840) popisuje syntaxe pro nástroj Httpcfg.exe.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-111">The [Windows Support Tools documentation](https://go.microsoft.com/fwlink/?LinkId=94840) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="a3c1f-112">Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí nástroje Netsh.exe, který je už nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-112">If you are running [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="a3c1f-113">Toto téma popisuje, jak provádět několik postupů:</span><span class="sxs-lookup"><span data-stu-id="a3c1f-113">This topic describes how to accomplish several procedures:</span></span>  
  
-   <span data-ttu-id="a3c1f-114">Určení počítače aktuální konfiguraci portů.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-114">Determining a computer's current port configuration.</span></span>  
  
-   <span data-ttu-id="a3c1f-115">Načtení kryptografického otisku certifikátu (nezbytné pro následující dva postupy).</span><span class="sxs-lookup"><span data-stu-id="a3c1f-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
-   <span data-ttu-id="a3c1f-116">Vytvoření vazby certifikátu SSL na konfiguraci portu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-116">Binding an SSL certificate to a port configuration.</span></span>  
  
-   <span data-ttu-id="a3c1f-117">Vytvoření vazby certifikátu SSL na konfigurace portů a podpůrné klientské certifikáty.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
-   <span data-ttu-id="a3c1f-118">Odstraňuje se certifikát SSL od číslo portu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="a3c1f-119">Všimněte si, že změna certifikáty uložené v počítači vyžaduje oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="a3c1f-120">Chcete-li zjistit, jak jsou nakonfigurované porty</span><span class="sxs-lookup"><span data-stu-id="a3c1f-120">To determine how ports are configured</span></span>  
  
1. <span data-ttu-id="a3c1f-121">V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj HttpCfg.exe zobrazíte aktuální konfiguraci portů pomocí **dotazu** a **ssl** přepne, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-121">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```  
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="a3c1f-122">V [!INCLUDE[wv](../../../../includes/wv-md.md)], chcete-li zobrazit aktuální konfigurací portů, pomocí nástroje Netsh.exe, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-122">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="a3c1f-123">Chcete-li získat kryptografický otisk certifikátu</span><span class="sxs-lookup"><span data-stu-id="a3c1f-123">To get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="a3c1f-124">Pomocí modulu snap-in Certifikáty konzoly MMC se najít certifikát X.509, který má zamýšleným účelem ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="a3c1f-125">Další informace najdete v tématu [jak: Zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="a3c1f-125">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="a3c1f-126">Přístup k kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-126">Access the certificate's thumbprint.</span></span> <span data-ttu-id="a3c1f-127">Další informace najdete v tématu [jak: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="a3c1f-127">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="a3c1f-128">Zkopírujte kryptografický otisk certifikátu do textového editoru, jako je například Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="a3c1f-129">Odebere všechny mezery mezi hexadecimálních znaků.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="a3c1f-130">Jedním ze způsobů jak toho dosáhnout, je použít funkci Najít a nahradit text editoru a nahraďte každou mezeru znakem null.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="a3c1f-131">K vytvoření vazby certifikátu SSL na číslo portu</span><span class="sxs-lookup"><span data-stu-id="a3c1f-131">To bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="a3c1f-132">V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj HttpCfg.exe v režimu "set" v úložišti vrstvy SSL (Secure Sockets) k vytvoření vazby certifikátu na číslo portu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-132">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="a3c1f-133">Nástroj používá k identifikaci certifikátu a kryptografický otisk, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    -   <span data-ttu-id="a3c1f-134">**-I** přepínač je syntaxe `IP`:`port` a dává pokyn nástroji a nastavte certifikát na port 8012 počítače.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="a3c1f-135">Volitelně můžete čtyři nuly, které předcházet číslo můžete také nahrazuje skutečné IP adresu počítače.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    -   <span data-ttu-id="a3c1f-136">**-H** přepínač určuje kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="a3c1f-137">V [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí nástroje Netsh.exe, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-137">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    -   <span data-ttu-id="a3c1f-138">**Certhash** parametr určuje kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    -   <span data-ttu-id="a3c1f-139">**Ipport** parametr určuje IP adresu a port, a funguje stejně jako **-i** přepínač nástroj Httpcfg.exe popsané.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    -   <span data-ttu-id="a3c1f-140">**Appid** parametr je identifikátor GUID, který slouží k identifikaci vlastnící aplikace.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="a3c1f-141">Vytvoření vazby certifikátu SSL na číslo portu a podpoře klientské certifikáty</span><span class="sxs-lookup"><span data-stu-id="a3c1f-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="a3c1f-142">V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aby podporovaly klienty, které ověřování pomocí certifikátů X.509 na transportní vrstvě, postupujte podle předchozího postupu, ale další parametr příkazového řádku předat HttpCfg.exe, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-142">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="a3c1f-143">**-F** přepínač je syntaxe `n` kde n je číslo v rozsahu od 1 do 7.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="a3c1f-144">Hodnota 2, jak je znázorněno v předchozím příkladu povolí klientské certifikáty na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="a3c1f-145">Hodnota 3 umožňuje klientské certifikáty a tyto certifikáty se mapuje na účet Windows.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="a3c1f-146">Pro chování ostatních hodnot naleznete v nápovědě HttpCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="a3c1f-147">V [!INCLUDE[wv](../../../../includes/wv-md.md)], klientům podporu ověřování pomocí certifikátů X.509 na transportní vrstvě, postupujte podle předchozího postupu, ale s dalším parametrem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-147">In [!INCLUDE[wv](../../../../includes/wv-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="a3c1f-148">Odstranit certifikát SSL od číslo portu</span><span class="sxs-lookup"><span data-stu-id="a3c1f-148">To delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="a3c1f-149">Použijte nástroj HttpCfg.exe nebo Netsh.exe zobrazíte portů a kryptografické otisky všechny vazby v počítači.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="a3c1f-150">Tisknout informace na disk, použijte znak přesměrování ">", jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2. <span data-ttu-id="a3c1f-151">V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj HttpCfg.exe s **odstranit** a **ssl** klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-151">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="a3c1f-152">Použití **-i** přepínač k určení `IP`:`port` číslo a **-h** přepínač k určení kryptografického otisku.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="a3c1f-153">V [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí nástroje Netsh.exe, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-153">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="a3c1f-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3c1f-154">Example</span></span>  
 <span data-ttu-id="a3c1f-155">Následující kód ukazuje, jak vytvořit v místním prostředí pomocí <xref:System.ServiceModel.WSHttpBinding> třídy nastavenou na zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="a3c1f-156">Při vytváření aplikace, zadejte číslo portu adresy.</span><span class="sxs-lookup"><span data-stu-id="a3c1f-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a3c1f-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3c1f-157">See also</span></span>

- [<span data-ttu-id="a3c1f-158">Zabezpečení přenosu HTTP</span><span class="sxs-lookup"><span data-stu-id="a3c1f-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
