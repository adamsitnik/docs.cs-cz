---
title: Certmgr.exe (nástroj Certificate Manager)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14dc09ff8ceaa5e754c2a8ee64846fbcac55e37f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779935"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="8110a-102">Certmgr.exe (nástroj Certificate Manager)</span><span class="sxs-lookup"><span data-stu-id="8110a-102">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="8110a-103">Nástroj Správce certifikátů (Certmgr.exe) spravuje certifikáty, seznamy důvěryhodných certifikátů (CTL) a seznamy odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="8110a-103">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="8110a-104">Správce certifikátů je automaticky nainstalován při instalaci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8110a-104">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="8110a-105">Chcete-li spustit nástroj, použijte [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8110a-105">To start the tool, use the [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8110a-106">Správce certifikátů (Certmgr.exe) je nástroj příkazového řádku, zatímco Certifikáty (Certmgr.msc) jsou modulem snap-in konzoly MMC (Microsoft Management Console).</span><span class="sxs-lookup"><span data-stu-id="8110a-106">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="8110a-107">Protože Certmgr.msc obvykle nachází v adresáři systému Windows, zadávání `certmgr` na příkazovém řádku se může načíst modul snap-in Certifikáty konzoly MMC i v případě, že jste otevřeli Developer Command Prompt pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8110a-107">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="8110a-108">K tomuto případu může dojít, protože cesta k modulu snap-in předchází cestě nástroje Správce certifikátů v proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="8110a-108">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="8110a-109">Setkáte-li se s tímto problémem, můžete zadáním cesty ke spustitelnému souboru spustit příkazy Certmgr.exe.</span><span class="sxs-lookup"><span data-stu-id="8110a-109">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="8110a-110">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8110a-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="8110a-111">Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7).</span><span class="sxs-lookup"><span data-stu-id="8110a-111">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="8110a-112">Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8110a-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="8110a-113">Přehled certifikátů X.509 naleznete v tématu [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8110a-113">For an overview of X.509 certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="8110a-114">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="8110a-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8110a-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8110a-115">Syntax</span></span>  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="8110a-116">Parametry</span><span class="sxs-lookup"><span data-stu-id="8110a-116">Parameters</span></span>  
  
|<span data-ttu-id="8110a-117">Argument</span><span class="sxs-lookup"><span data-stu-id="8110a-117">Argument</span></span>|<span data-ttu-id="8110a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8110a-118">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="8110a-119">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="8110a-119">*sourceStorename*</span></span>|<span data-ttu-id="8110a-120">Úložiště certifikátů obsahuje aktuální certifikáty, soubory CTL nebo CRL, které lze přidat, odstranit, uložit nebo zobrazit.</span><span class="sxs-lookup"><span data-stu-id="8110a-120">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="8110a-121">To může představovat soubor úložiště nebo systémové úložiště.</span><span class="sxs-lookup"><span data-stu-id="8110a-121">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="8110a-122">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="8110a-122">*destinationStorename*</span></span>|<span data-ttu-id="8110a-123">Výstupní úložiště certifikátů nebo soubor.</span><span class="sxs-lookup"><span data-stu-id="8110a-123">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="8110a-124">Možnost</span><span class="sxs-lookup"><span data-stu-id="8110a-124">Option</span></span>|<span data-ttu-id="8110a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="8110a-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8110a-126">**/ add**</span><span class="sxs-lookup"><span data-stu-id="8110a-126">**/add**</span></span>|<span data-ttu-id="8110a-127">Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8110a-127">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="8110a-128">**/ all**</span><span class="sxs-lookup"><span data-stu-id="8110a-128">**/all**</span></span>|<span data-ttu-id="8110a-129">Přidá všechny záznamy zadáním možnosti **/ add**.</span><span class="sxs-lookup"><span data-stu-id="8110a-129">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="8110a-130">Odstraní všechny záznamy zadáním možnosti **/del**. Zobrazí všechny záznamy zadáním bez **/ add** nebo **/del** možnosti.</span><span class="sxs-lookup"><span data-stu-id="8110a-130">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="8110a-131">**/All** možnost nelze použít s **/put**.</span><span class="sxs-lookup"><span data-stu-id="8110a-131">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="8110a-132">**/c**</span><span class="sxs-lookup"><span data-stu-id="8110a-132">**/c**</span></span>|<span data-ttu-id="8110a-133">Přidá certifikáty zadáním **/ add**.</span><span class="sxs-lookup"><span data-stu-id="8110a-133">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="8110a-134">Odstraní certifikáty zadáním **/del**. Uloží certifikáty zadáním **/put**.</span><span class="sxs-lookup"><span data-stu-id="8110a-134">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="8110a-135">Zobrazí certifikáty při použití bez **/ add**, **/del**, nebo **/put** možnost.</span><span class="sxs-lookup"><span data-stu-id="8110a-135">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="8110a-136">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="8110a-136">**/CRL**</span></span>|<span data-ttu-id="8110a-137">Přidá soubory CRL zadáním pomocí možnosti **/ add**.</span><span class="sxs-lookup"><span data-stu-id="8110a-137">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="8110a-138">Odstraní soubory CRL zadáním pomocí možnosti **/del**. Uloží soubory CRL zadáním pomocí možnosti **/put**.</span><span class="sxs-lookup"><span data-stu-id="8110a-138">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="8110a-139">Zobrazí soubory CRL zadáním bez možnosti **/ add**, **/del**, nebo **/put** možnost.</span><span class="sxs-lookup"><span data-stu-id="8110a-139">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="8110a-140">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="8110a-140">**/CTL**</span></span>|<span data-ttu-id="8110a-141">Přidá soubory CTL zadáním **/ add**.</span><span class="sxs-lookup"><span data-stu-id="8110a-141">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="8110a-142">Odstraní soubory CTL zadáním **/del**. Uloží soubory CTL zadáním **/put**.</span><span class="sxs-lookup"><span data-stu-id="8110a-142">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="8110a-143">Zobrazí soubory CTL zadáním bez **/ add**, **/del**, nebo **/put** možnost.</span><span class="sxs-lookup"><span data-stu-id="8110a-143">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="8110a-144">**/del**</span><span class="sxs-lookup"><span data-stu-id="8110a-144">**/del**</span></span>|<span data-ttu-id="8110a-145">Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8110a-145">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="8110a-146">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="8110a-146">**/e** *encodingType*</span></span>|<span data-ttu-id="8110a-147">Určuje typ kódování certifikátu.</span><span class="sxs-lookup"><span data-stu-id="8110a-147">Specifies the certificate encoding type.</span></span> <span data-ttu-id="8110a-148">Výchozí hodnota je `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="8110a-148">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="8110a-149">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="8110a-149">**/f** *dwFlags*</span></span>|<span data-ttu-id="8110a-150">Určuje příznak pro otevření úložiště.</span><span class="sxs-lookup"><span data-stu-id="8110a-150">Specifies the store open flag.</span></span> <span data-ttu-id="8110a-151">Toto je *dwFlags* byl předán parametr **CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="8110a-151">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="8110a-152">Výchozí hodnota je CERT_SYSTEM_STORE_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="8110a-152">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="8110a-153">Tato možnost je zvážena pouze v případě, **/y** možnost se používá.</span><span class="sxs-lookup"><span data-stu-id="8110a-153">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="8110a-154">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="8110a-154">**/h**[**elp**]</span></span>|<span data-ttu-id="8110a-155">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="8110a-155">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="8110a-156">**/n** *název*</span><span class="sxs-lookup"><span data-stu-id="8110a-156">**/n** *nam*</span></span>|<span data-ttu-id="8110a-157">Určuje obecný název certifikátu, který se má přidat, odstranit nebo uložit.</span><span class="sxs-lookup"><span data-stu-id="8110a-157">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="8110a-158">Tuto možnost lze použít u certifikátů. Nelze ji použít u souborů CTL nebo u CRL.</span><span class="sxs-lookup"><span data-stu-id="8110a-158">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="8110a-159">**/ put**</span><span class="sxs-lookup"><span data-stu-id="8110a-159">**/put**</span></span>|<span data-ttu-id="8110a-160">Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8110a-160">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="8110a-161">Soubor je uložen ve formátu X.509.</span><span class="sxs-lookup"><span data-stu-id="8110a-161">The file is saved in X.509 format.</span></span> <span data-ttu-id="8110a-162">Můžete použít **/7** spolu s možností **/put** uložit soubor ve formátu PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="8110a-162">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="8110a-163">**/Put** možnost musí být následována buď **/c**, **/CTL**, nebo **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="8110a-163">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="8110a-164">**/All** možnost nelze použít s **/put**.</span><span class="sxs-lookup"><span data-stu-id="8110a-164">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="8110a-165">**/r** *umístění*</span><span class="sxs-lookup"><span data-stu-id="8110a-165">**/r** *location*</span></span>|<span data-ttu-id="8110a-166">Určuje umístění registru v rámci systémového úložiště.</span><span class="sxs-lookup"><span data-stu-id="8110a-166">Identifies the registry location of the system store.</span></span> <span data-ttu-id="8110a-167">Tato možnost je zvážena pouze v případě, že zadáte **/s** možnost.</span><span class="sxs-lookup"><span data-stu-id="8110a-167">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="8110a-168">*umístění* musí být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="8110a-168">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="8110a-169">-   `currentUser` Označuje, že se úložiště certifikátů nachází pod klíčem HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="8110a-169">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="8110a-170">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="8110a-170">This is the default.</span></span><br /><span data-ttu-id="8110a-171">-   `localMachine` Označuje, že se úložiště certifikátů nachází pod klíčem HKEY_LOCAL_MACHINE.</span><span class="sxs-lookup"><span data-stu-id="8110a-171">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="8110a-172">**/s**</span><span class="sxs-lookup"><span data-stu-id="8110a-172">**/s**</span></span>|<span data-ttu-id="8110a-173">Určuje, že je úložiště certifikátů systémovým úložištěm.</span><span class="sxs-lookup"><span data-stu-id="8110a-173">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="8110a-174">Pokud tuto možnost nezadáte, bude považován za úložiště **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="8110a-174">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="8110a-175">**/sha1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="8110a-175">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="8110a-176">Určuje hodnotu hash SHA1 certifikátu, souboru CTl nebo CRl, který se má přidat, odstranit nebo uložit.</span><span class="sxs-lookup"><span data-stu-id="8110a-176">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="8110a-177">**/v**</span><span class="sxs-lookup"><span data-stu-id="8110a-177">**/v**</span></span>|<span data-ttu-id="8110a-178">Určuje podrobný režim. Zobrazí detailní informace o certifikátech, souborech CTL a CRL.</span><span class="sxs-lookup"><span data-stu-id="8110a-178">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="8110a-179">Tento parametr nelze použít s **/ add**, **/del**, nebo **/put** možnosti.</span><span class="sxs-lookup"><span data-stu-id="8110a-179">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="8110a-180">**/y** *zprostředkovatele*</span><span class="sxs-lookup"><span data-stu-id="8110a-180">**/y** *provider*</span></span>|<span data-ttu-id="8110a-181">Určuje název poskytovatele úložiště.</span><span class="sxs-lookup"><span data-stu-id="8110a-181">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="8110a-182">**/7**</span><span class="sxs-lookup"><span data-stu-id="8110a-182">**/7**</span></span>|<span data-ttu-id="8110a-183">Ukládá cílové úložiště jako objekt PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="8110a-183">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="8110a-184">**/?**</span><span class="sxs-lookup"><span data-stu-id="8110a-184">**/?**</span></span>|<span data-ttu-id="8110a-185">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="8110a-185">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8110a-186">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8110a-186">Remarks</span></span>  
 <span data-ttu-id="8110a-187">Nástroj Certmgr.exe vykonává následující základní funkce:</span><span class="sxs-lookup"><span data-stu-id="8110a-187">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="8110a-188">Zobrazí certifikáty, soubory CTL a CRL do konzoly.</span><span class="sxs-lookup"><span data-stu-id="8110a-188">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="8110a-189">Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8110a-189">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="8110a-190">Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8110a-190">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="8110a-191">Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8110a-191">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="8110a-192">Certmgr.exe pracuje se dvěma typy úložišť certifikátů: **StoreFile** a systémové úložiště.</span><span class="sxs-lookup"><span data-stu-id="8110a-192">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="8110a-193">Není nutné zadávat typ úložiště certifikátů. Certmgr.exe dokáže rozpoznat typ úložiště a vykonat příslušné operace.</span><span class="sxs-lookup"><span data-stu-id="8110a-193">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="8110a-194">Spuštěním nástroje Certmgr.exe bez určení jakýchkoli možností dojde ke spuštění modulu snap-in certmgr.msc, který obsahuje uživatelské rozhraní, které pomáhá s úlohami správy certifikátů, které jsou dostupné také z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="8110a-194">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="8110a-195">Uživatelské rozhraní poskytuje průvodce importováním, který zkopíruje certifikáty, soubory CTL a CRL z disku do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8110a-195">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="8110a-196">Název úložiště certifikátu x 509 pro můžete najít `sourceStorename` a `destinationStorename` parametry zkompilováním a spuštěním následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="8110a-196">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="8110a-197">Další informace o certifikátech najdete v tématu [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8110a-197">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8110a-198">Příklady</span><span class="sxs-lookup"><span data-stu-id="8110a-198">Examples</span></span>  
 <span data-ttu-id="8110a-199">Následující příkaz zobrazí výchozí systémové úložiště s názvem `my` s podrobným výstupem.</span><span class="sxs-lookup"><span data-stu-id="8110a-199">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```  
certmgr /v /s my  
```  
  
 <span data-ttu-id="8110a-200">Následující příkaz přidá všechny certifikáty do souboru s názvem `myFile.ext` nový soubor s názvem `newFile.ext`.</span><span class="sxs-lookup"><span data-stu-id="8110a-200">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="8110a-201">Následující příkaz přidá certifikát do souboru s názvem `testcert.cer` k `my` systémového úložiště.</span><span class="sxs-lookup"><span data-stu-id="8110a-201">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="8110a-202">Následující příkaz přidá certifikát do souboru s názvem `TrustedCert.cer` do kořenového úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8110a-202">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="8110a-203">Následující příkaz uloží certifikát s běžným názvem `myCert` v `my` názvem systémového úložiště do souboru `newCert.cer`.</span><span class="sxs-lookup"><span data-stu-id="8110a-203">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="8110a-204">Následující příkaz odstraní všechny soubory CTL `my` úložiště systému a uloží výsledné úložiště do souboru volá `newStore.str`.</span><span class="sxs-lookup"><span data-stu-id="8110a-204">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="8110a-205">Následující příkaz uloží certifikát do `my` systémového úložiště v souboru `newFile`.</span><span class="sxs-lookup"><span data-stu-id="8110a-205">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="8110a-206">Zobrazí se výzva k zadání číslo certifikátu z `my` vložit `newFile`.</span><span class="sxs-lookup"><span data-stu-id="8110a-206">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="8110a-207">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8110a-207">See also</span></span>

- [<span data-ttu-id="8110a-208">Nástroje</span><span class="sxs-lookup"><span data-stu-id="8110a-208">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="8110a-209">MakeCert.exe (nástroj pro vytvoření certifikátu)</span><span class="sxs-lookup"><span data-stu-id="8110a-209">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="8110a-210">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="8110a-210">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
