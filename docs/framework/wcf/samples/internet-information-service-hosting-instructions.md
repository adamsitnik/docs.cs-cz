---
title: Pokyny k hostování služby IIS
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: a537f37132e5014901d415cd96bc72a55ae0b750
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600253"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="5b78c-102">Pokyny k hostování služby IIS</span><span class="sxs-lookup"><span data-stu-id="5b78c-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="5b78c-103">Ke spuštění ukázky, které jsou hostované v Internetové informační služby (IIS), musí se ujistěte, že IIS je správně nainstalován a běží.</span><span class="sxs-lookup"><span data-stu-id="5b78c-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="5b78c-104">Chcete-li nainstalovat službu IIS verze 7.5 na Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="5b78c-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="5b78c-105">Z **správce serveru**vyberte **role.**</span><span class="sxs-lookup"><span data-stu-id="5b78c-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="5b78c-106">V části **Souhrn rolí**, klikněte na tlačítko **přidat role**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="5b78c-107">Klikněte na tlačítko **Další** zobrazíte **vybrat role serveru** dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="5b78c-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="5b78c-108">Vyberte **aplikační Server** z **role** seznamu a potom klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro Role aplikačního serveru.</span><span class="sxs-lookup"><span data-stu-id="5b78c-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="5b78c-109">Vyberte **webového serveru (IIS)** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="5b78c-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="5b78c-110">Pokud se zobrazí výzva k instalaci služeb rolí a funkcí, klikněte na tlačítko **přidat požadované funkce**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="5b78c-111">Klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro roli webového serveru (IIS).</span><span class="sxs-lookup"><span data-stu-id="5b78c-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="5b78c-112">Rozbalte **nástroje pro správu**a potom rozbalte **IIS 6 Management Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="5b78c-113">Vyberte **IIS 6 Scripting Tools**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="5b78c-114">Pokud se zobrazí výzva k instalaci služeb rolí a funkcí, klikněte na tlačítko **přidat požadované služby rolí**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="5b78c-115">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-115">Click **Next**.</span></span>  
  
6. <span data-ttu-id="5b78c-116">Pokud správnost souhrn výběry, klikněte na tlačítko **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="5b78c-117">Po dokončení instalace klikněte na tlačítko **Zavřít**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="5b78c-118">Chcete-li nainstalovat službu IIS verze 7.5 na Windows 7</span><span class="sxs-lookup"><span data-stu-id="5b78c-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="5b78c-119">Klikněte na tlačítko **Start**a potom klikněte na tlačítko **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="5b78c-120">Otevřít **programy** skupiny.</span><span class="sxs-lookup"><span data-stu-id="5b78c-120">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="5b78c-121">V části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce Windows**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="5b78c-122">**Řízení uživatelských účtů** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="5b78c-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="5b78c-123">Klikněte na **Pokračovat**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-123">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="5b78c-124">**Funkce Windows** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="5b78c-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="5b78c-125">Rozbalte položky označené **Internetová informační služba**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="5b78c-126">Rozbalte položky označené **webové služby**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="5b78c-127">Rozbalte položky označené **funkce pro vývoj aplikací**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="5b78c-128">Ujistěte se, zda že jsou vybrány následující položky:</span><span class="sxs-lookup"><span data-stu-id="5b78c-128">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="5b78c-129">**Rozšiřitelnost rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="5b78c-129">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="5b78c-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="5b78c-130">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="5b78c-131">**Rozšíření ISAPI**</span><span class="sxs-lookup"><span data-stu-id="5b78c-131">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="5b78c-132">**Filtry ISAPI**</span><span class="sxs-lookup"><span data-stu-id="5b78c-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="5b78c-133">V části položky označené **webové služby**, rozbalte **společné funkce protokolu Http**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="5b78c-134">Ujistěte se, že **statický obsah** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="5b78c-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="5b78c-135">V části položky označené **webové služby**, rozbalte **zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="5b78c-136">Ujistěte se, že **ověřování Windows** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="5b78c-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="5b78c-137">V části **Internetová informační služba** adresáře, rozbalte položku s popiskem **nástroje webové správy**a pak vyberte **Konzola pro správu služby IIS**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="5b78c-138">Rozbalte položky označené **IIS 6 Management Compatibility**a pak vyberte **IIS 6 Scripting Tools**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="5b78c-139">V části **Internetová informační služba** adresáře, rozbalte položku s popiskem **rozhraní Microsoft .NET Framework 3.5.1**a pak vyberte **aktivace Windows Communication Foundation Http**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="5b78c-140">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="5b78c-141">Chcete-li nainstalovat službu IIS verze 7.0 ve Windows serveru 2008</span><span class="sxs-lookup"><span data-stu-id="5b78c-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="5b78c-142">Z **správce serveru**vyberte **role**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="5b78c-143">V části **Souhrn rolí**, klikněte na tlačítko **přidat role**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="5b78c-144">Klikněte na tlačítko **Další** zobrazíte **vybrat role serveru** dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="5b78c-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="5b78c-145">Vyberte **aplikační Server** z **role** seznamu a potom klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro Role aplikačního serveru.</span><span class="sxs-lookup"><span data-stu-id="5b78c-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="5b78c-146">Vyberte **webového serveru (IIS)** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="5b78c-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="5b78c-147">Pokud se zobrazí výzva k instalaci služeb rolí a funkcí, klikněte na tlačítko **přidat požadované funkce**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="5b78c-148">Klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro roli webového serveru (IIS).</span><span class="sxs-lookup"><span data-stu-id="5b78c-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="5b78c-149">Rozbalte **nástroje pro správu**a potom rozbalte **IIS 6 Management Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="5b78c-150">Vyberte **IIS 6 Scripting Tools**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="5b78c-151">Pokud se zobrazí výzva k instalaci služeb rolí a funkcí, klikněte na tlačítko **přidat požadované služby rolí**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="5b78c-152">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-152">Click **Next**.</span></span>  
  
6. <span data-ttu-id="5b78c-153">Pokud správnost souhrn výběry, klikněte na tlačítko **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="5b78c-154">Po dokončení instalace klikněte na tlačítko **Zavřít**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="5b78c-155">Chcete-li nainstalovat službu IIS verze 7.0 v systému Windows Vista</span><span class="sxs-lookup"><span data-stu-id="5b78c-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="5b78c-156">Klikněte na tlačítko Start a potom klikněte na ovládacích panelech.</span><span class="sxs-lookup"><span data-stu-id="5b78c-156">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="5b78c-157">Vyberte **programy** skupiny.</span><span class="sxs-lookup"><span data-stu-id="5b78c-157">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="5b78c-158">V části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce Windows**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="5b78c-159">**Řízení uživatelských účtů** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="5b78c-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="5b78c-160">Klikněte na **Pokračovat**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-160">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="5b78c-161">**Funkce Windows** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="5b78c-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="5b78c-162">Rozbalte položky označené **Internetová informační služba**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="5b78c-163">Rozbalte položky označené **webové služby**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="5b78c-164">Rozbalte položky označené **funkce pro vývoj aplikací**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="5b78c-165">Ujistěte se, zda že jsou vybrány následující položky:</span><span class="sxs-lookup"><span data-stu-id="5b78c-165">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="5b78c-166">**Rozšiřitelnost rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="5b78c-166">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="5b78c-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="5b78c-167">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="5b78c-168">**Rozšíření ISAPI**</span><span class="sxs-lookup"><span data-stu-id="5b78c-168">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="5b78c-169">**Filtry ISAPI**</span><span class="sxs-lookup"><span data-stu-id="5b78c-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="5b78c-170">Rozbalte položky označené **nástroje webové správy**a pak vyberte **konzolu pro správu IIS**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="5b78c-171">V části položky označené **webové služby**, rozbalte **společné funkce protokolu Http**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="5b78c-172">Ujistěte se, že **statický obsah** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="5b78c-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="5b78c-173">V části položky označené **webové služby**, rozbalte **zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="5b78c-174">Ujistěte se, že **ověřování Windows** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="5b78c-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="5b78c-175">Rozbalte položky označené **IIS 6 Management Compatibility**a pak vyberte **IIS 6 Scripting Tools**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="5b78c-176">Rozbalte položky označené **rozhraní Microsoft .NET Framework 3.0**a pak vyberte **aktivace Windows Communication Foundation Http**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="5b78c-177">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="5b78c-178">Chcete-li nainstalovat službu IIS verze 6.0 v systému Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="5b78c-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="5b78c-179">Z **Správa serveru**, klikněte na tlačítko **přidat nebo odebrat roli**a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="5b78c-180">Vyberte **aplikační server (IIS, ASP.NET)** z **Role serveru** seznamu a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="5b78c-181">Vyberte **povolit technologii ASP.NET** zaškrtněte políčko a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="5b78c-182">Pokud správnost souhrn výběry, klikněte na tlačítko Další.</span><span class="sxs-lookup"><span data-stu-id="5b78c-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="5b78c-183">Chcete-li nainstalovat službu IIS verze 5.1 na Windows XP s aktualizací Service Pack 2 a aktualizací Service Pack 3 nainstalovat</span><span class="sxs-lookup"><span data-stu-id="5b78c-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="5b78c-184">V Ovládacích panelech klikněte na tlačítko **přidat nebo odebrat programy**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="5b78c-185">V **přidat nebo odebrat programy** dialogové okno, klikněte na tlačítko **přidat nebo odebrat součásti Windows**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="5b78c-186">V **Průvodce součásti Windows**, vyberte **Internetové informační služby (IIS)** zaškrtněte políčko a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="5b78c-187">Pokud **soubory potřebné** dialogové okno se zobrazí, vložte instalační disk operačního systému, přejděte do složky i386 a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="5b78c-188">Po dokončení instalace klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-188">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="5b78c-189">Zavřete **přidat nebo odebrat programy** dialogové okno a potom zavřete **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="5b78c-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="5b78c-190">Ověření instalace služby IIS a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b78c-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="5b78c-191">Uložte soubor HTML najdete na konci tohoto tématu v kořenovém adresáři \InetPub\wwwroot a pojmenujte ho Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="5b78c-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="5b78c-192">Otevřete okno prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="5b78c-192">Open a browser window.</span></span>  
  
3. <span data-ttu-id="5b78c-193">Typ `http://localhost/Default.aspx` do pole adresy a potom stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="5b78c-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="5b78c-194">By se zobrazit webovou stránku s textem "Hello World".</span><span class="sxs-lookup"><span data-stu-id="5b78c-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b78c-195">Pokaždé, když instalujete novou verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], je nutné znovu zaregistrovat aspnet_isapi jako rozšíření webové služby pro službu IIS.</span><span class="sxs-lookup"><span data-stu-id="5b78c-195">Each time you install a new version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="5b78c-196">Uděláte to tak, vydávat `aspnet_regiis –I –enable` příkazu.</span><span class="sxs-lookup"><span data-stu-id="5b78c-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="5b78c-197">Vzorový kód</span><span class="sxs-lookup"><span data-stu-id="5b78c-197">Sample Code</span></span>  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
