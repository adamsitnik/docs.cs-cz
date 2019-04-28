---
title: 'Postupy: Konfigurace sady Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: dcaabf9ecd47bc88095e92aa8ed28ad5f13fd1dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757027"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="52423-102">Postupy: Konfigurace sady Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby</span><span class="sxs-lookup"><span data-stu-id="52423-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] <span data-ttu-id="52423-103">Spusťte v sandboxu částečným vztahem důvěryhodnosti zabezpečení, který je omezena na sadu oprávnění pro zónu Internetu.</span><span class="sxs-lookup"><span data-stu-id="52423-103">run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="52423-104">Tato sada oprávnění omezuje pouze webové služby, které se nacházejí ve volání webové služby [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] aplikace webovou stránku původu.</span><span class="sxs-lookup"><span data-stu-id="52423-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="52423-105">Když [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ladění ze sady Visual Studio 2005, ale není považováno za používat webová služba odkazy na stejné místo původu.</span><span class="sxs-lookup"><span data-stu-id="52423-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="52423-106">Výjimky zabezpečení Toto způsobí, že při vyvolání [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pokusí o volání webové služby.</span><span class="sxs-lookup"><span data-stu-id="52423-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="52423-107">Nicméně Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projektu lze nastavit pro simulaci s původu stejné lokalitě jako webové služby, které volá při ladění.</span><span class="sxs-lookup"><span data-stu-id="52423-107">However, a Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="52423-108">Díky tomu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpečně volat webovou službu bez způsobení výjimky zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="52423-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="52423-109">Konfigurování sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="52423-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="52423-110">Konfigurace sady Visual Studio 2005 pro ladění [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , která volá webové služby:</span><span class="sxs-lookup"><span data-stu-id="52423-110">To configure Visual Studio 2005 to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>

1. <span data-ttu-id="52423-111">S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="52423-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="52423-112">V **Návrháře projektu**, klikněte na tlačítko **ladění** kartu.</span><span class="sxs-lookup"><span data-stu-id="52423-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="52423-113">V **spustit akci** vyberte **externí program Start** a zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="52423-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="52423-114">V **možnosti spuštění** části, zadejte následující kód do **argumenty příkazového řádku** textové pole:</span><span class="sxs-lookup"><span data-stu-id="52423-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="52423-115">`-debug`  *Název souboru*</span><span class="sxs-lookup"><span data-stu-id="52423-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="52423-116">*Filename* hodnota **– ladění** parametr je název souboru .xbap; například:</span><span class="sxs-lookup"><span data-stu-id="52423-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
>  <span data-ttu-id="52423-117">Toto je výchozí konfigurace pro řešení, které jsou vytvořeny pomocí Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="52423-117">This is the default configuration for solutions that are created with the Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>

1. <span data-ttu-id="52423-118">S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="52423-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="52423-119">V **Návrháře projektu**, klikněte na tlačítko **ladění** kartu.</span><span class="sxs-lookup"><span data-stu-id="52423-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="52423-120">V **možnosti spuštění** části, přidejte následující parametr příkazového řádku **argumenty příkazového řádku** textové pole:</span><span class="sxs-lookup"><span data-stu-id="52423-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="52423-121">`-debugSecurityZoneURL`  *URL*</span><span class="sxs-lookup"><span data-stu-id="52423-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="52423-122">*Adresy URL* hodnota **- debugSecurityZoneURL** parametr je [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] pro umístění, které chcete simulovat jako místo původu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="52423-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="52423-123">Jako příklad, vezměte v úvahu [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] webovou službu, která používá následující [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="52423-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="52423-124">Umístění původních [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] pro tento Web service je:</span><span class="sxs-lookup"><span data-stu-id="52423-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="52423-125">V důsledku toho kompletní **- debugSecurityZoneURL** parametr příkazového řádku a hodnota je:</span><span class="sxs-lookup"><span data-stu-id="52423-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="52423-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52423-126">See also</span></span>

- [<span data-ttu-id="52423-127">Hostitel WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="52423-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
