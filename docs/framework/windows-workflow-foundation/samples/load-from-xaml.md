---
title: Načtení z XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: e0cac1b6dfb9568ba08079cf5194b3432eea856f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637718"
---
# <a name="load-from-xaml"></a>Načtení z XAML
Tato ukázka předvádí, jak dynamicky načíst pracovní postup XAML bez nutnosti spuštění XamlBuildTask nástroj. Místo toho, ukázka zavolá <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metody. Ukázka je klientská aplikace Windows Presentation Foundation (WPF), která načte pracovní postupy XAML pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy a spustí je. Po jejich byly načteny pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy, <xref:System.Activities.DynamicActivity%601> je vrácena, které mohou být provedeny.

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1. Pomocí sady Visual Studio 2010, otevřete soubor řešení LoadFromXAML.sln.

2. Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Abyste mohli spustit řešení, stiskněte CTRL + F5.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
