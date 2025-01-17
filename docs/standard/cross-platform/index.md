---
title: Vývoj pro různé platformy s .NET Frameworkem
ms.date: 07/18/2018
ms.technology: dotnet-standard
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2167f74c5d1dd9f49995b6407e65feb474084dc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641448"
---
# <a name="developing-for-multiple-platforms-with-the-net-framework"></a>Vývoj pro různé platformy s .NET Frameworkem

Můžete vyvíjet aplikace pro Microsoft i jiných společností než Microsoft platformy pomocí rozhraní .NET Framework a sady Visual Studio.
  
## <a name="options-for-cross-platform-development"></a>Možnosti pro vývoj pro různé platformy

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]
  
 Vývoj pro různé platformy, můžete sdílet zdrojový kód nebo binární soubory a mohl provádět volání mezi kódu rozhraní .NET Framework a rozhraní API Windows Runtime.  
  
|Pokud chcete...|Použití...|  
|-----------------------|------------|  
|Sdílet zdrojový kód mezi aplikacemi pro Windows Phone 8.1 a Windows 8.1|**Sdílené projekty** (univerzální aplikace pro šablony sady Visual Studio 2013 Update 2).<br /><br /> -Aktuálně nepodporuje jazyka Visual Basic.<br />-Můžete oddělit kód specifický pro platformu s využitím #`if` příkazy.<br /><br /> Podrobnosti najdete v tématu:<br /><br /> -   [Pusťte se do programování](/windows/uwp/get-started/create-uwp-apps)<br />-   [Pomocí sady Visual Studio pro vytváření univerzálních aplikací XAML](https://devblogs.microsoft.com/visualstudio/using-visual-studio-to-build-universal-xaml-apps/) (příspěvek na blogu)<br />-   [Pomocí sady Visual Studio k vytváření aplikací XAML Konvergované](https://channel9.msdn.com/Events/Build/2014/3-591) (video)|  
|Sdílet binární soubory mezi aplikacemi, které jsou určené pro různé platformy|**Přenosné knihovny tříd projektů** pro kód, který je nezávislý na platformě.<br /><br /> – Tento přístup se obvykle používá pro kód, který implementuje obchodní logiku.<br />– Můžete použít Visual Basic nebo C#.<br />– Podpora rozhraní API se liší podle platformy.<br />-Přenosné knihovny tříd projektů, které se zaměřují na Windows 8.1 a Windows Phone 8.1 podporují rozhraní API Windows Runtime a XAML. Tyto funkce nejsou k dispozici ve starších verzích přenosné knihovny tříd.<br />– Pokud je nepotřebujete, můžete s použitím rozhraní nebo abstraktní třídy abstraktní si kód specifický pro platformu.<br /><br /> Podrobnosti najdete v tématu:<br /><br /> -   [Knihovny přenosných tříd](cross-platform-development-with-the-portable-class-library.md)<br />-   [Jak provést přenosné třídy knihovny pracovní za vás](https://blogs.msdn.microsoft.com/dsplaisted/2012/08/27/how-to-make-portable-class-libraries-work-for-you/) (příspěvek na blogu)<br />-   [Používání knihovny přenosných tříd spolu s modelem MVVM](using-portable-class-library-with-model-view-view-model.md) <br />-   [Prostředky aplikací pro knihovny cílené na více platforem](app-resources-for-libraries-that-target-multiple-platforms.md) <br />-   [.NET portability Analyzeru](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) (rozšíření sady Visual Studio)|  
|Sdílet zdrojový kód mezi aplikacemi pro jiné platformy než Windows 8.1 a Windows Phone 8.1|**Přidat jako odkaz** funkce.<br /><br /> – Tento přístup je vhodný pro aplikaci logiky, která je společná pro obě aplikace, ale není přenosný z nějakého důvodu. Tato funkce slouží pro C# nebo kódu jazyka Visual Basic.<br />     Například Windows Phone 8 a Windows 8 sdílejí rozhraní API Windows Runtime, ale knihovny přenosných tříd nepodporují Windows Runtime pro tyto platformy. Můžete použít `Add as link` sdílet společný kód prostředí Windows Runtime mezi aplikací Windows Phone 8 a Windows Store aplikace, které cílí na systém Windows 8.<br /><br /> Podrobnosti najdete v tématu:<br /><br /> -   [Sdílení kódu pomocí přidat jako odkaz](https://docs.microsoft.com/previous-versions/windows/apps/jj714082(v=vs.105))<br />-   [Jak: Přidání existující položky do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))|  
|Zápis Windows Store apps pomocí rozhraní .NET Framework nebo volání rozhraní API Windows Runtime z kódu rozhraní .NET Framework|**Rozhraní API Windows Runtime** z kódu rozhraní .NET Framework C# nebo Visual Basic a pomocí rozhraní .NET Framework vytvářet aplikace pro Windows Store. Je třeba vědět, rozhraní API rozdíly mezi dvěma platformami. Existují však třídy, které vám pomohou při práci s těmito rozdíly.<br /><br /> Podrobnosti najdete v tématu:<br /><br /> -   [Podpora rozhraní .NET framework pro aplikace Windows Store a prostředí Windows Runtime](support-for-windows-store-apps-and-windows-runtime.md) <br />-   [Předávání identifikátorů URI pro Windows Runtime](passing-a-uri-to-the-windows-runtime.md) <br />-   <xref:System.IO.WindowsRuntimeStreamExtensions><br />-    <xref:System.WindowsRuntimeSystemExtensions>|  
|Vytvářejte aplikace rozhraní .NET Framework pro jiné platformy než Microsoft|**Odkaz na přenosné knihovny tříd sestavení** v rozhraní .NET Framework a nástroje, jako je Xamarin rozšíření nebo jiných výrobců Visual Studio.<br /><br /> Podrobnosti najdete v tématu:<br /><br /> -   [Přenosná knihovna tříd nyní k dispozici na všech platformách.](https://devblogs.microsoft.com/dotnet/portable-class-library-pcl-now-available-on-all-platforms/) (příspěvek na blogu)<br />-   [Dokumentace k Xamarinu](/xamarin)|  
|Pro vývoj multiplatformních aplikací pomocí JavaScriptu a HTML|**Šablony aplikací pro univerzální** v sadě Visual Studio 2013 Update 2 na vývoj proti rozhraní API Windows Runtime pro Windows 8.1 a Windows Phone 8.1. V současné době nelze použít jazyka JavaScript a HTML pomocí rozhraní API .NET Framework, pro vývoj aplikací pro různé platformy.<br /><br /> Podrobnosti najdete v tématu:<br /><br /> -   [Šablony projektů jazyka JavaScript](https://docs.microsoft.com/previous-versions/windows/apps/hh758331%28v=win.10%29)<br />-   [Přenesení aplikace v jazyce prostředí Windows Runtime pomocí jazyka JavaScript pro Windows Phone](https://docs.microsoft.com/previous-versions/windows/apps/dn636144%28v=win.10%29)|
