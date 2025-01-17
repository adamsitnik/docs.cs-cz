---
title: Řazení událostí ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 28eb451c7edd740664f80f8ec35c60192764043c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949867"
---
# <a name="order-of-events-in-windows-forms"></a>Řazení událostí ve Windows Forms
Pořadí, ve kterém jsou události vyvolány v aplikacích model Windows Forms, jsou zvláštním zájmem vývojářů, kteří mají obavy, že se jednotlivé události zpracovávají. Když se situace zavolá na nejpreciznější zpracování událostí, jako je třeba při překreslení částí formuláře, je nutné určit přesné pořadí, ve kterém jsou události vyvolány v době běhu. V tomto tématu jsou uvedeny některé podrobnosti o pořadí událostí během několika důležitých fází životního cyklu aplikací a ovládacích prvků. Konkrétní podrobnosti o pořadí událostí vstupu myši naleznete [v tématu události myši v model Windows Forms](mouse-events-in-windows-forms.md). Přehled událostí v model Windows Forms najdete v tématu věnovaném [událostem Overview](events-overview-windows-forms.md). Podrobnosti o strukturu obslužných rutin událostí najdete v tématu [Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Události spuštění a vypnutí aplikace  
 Třídy <xref:System.Windows.Forms.Form> a<xref:System.Windows.Forms.Control> zveřejňují sadu událostí souvisejících s spuštěním a vypnutím aplikace. Při spuštění aplikace model Windows Forms se události spuštění hlavního formuláře vyvolají v tomto pořadí:  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 Po zavření aplikace se události vypnutí hlavního formuláře vyvolají v tomto pořadí:  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <xref:System.Windows.Forms.Application.ApplicationExit> Událost<xref:System.Windows.Forms.Application> třídy je vyvolána po událostech vypnutí hlavního formuláře.  
  
> [!NOTE]
> Visual Basic 2005 obsahuje další události aplikace, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> jako například a. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>  
  
## <a name="focus-and-validation-events"></a>Události fokusu a ověření  
 Když změníte fokus pomocí klávesnice (karta, SHIFT + TAB atd.), <xref:System.Windows.Forms.Control.Select%2A> voláním metody <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> nebo <xref:System.Windows.Forms.Control.SelectNextControl%2A> nebo nastavením vlastnosti na aktuální formulář, události <xref:System.Windows.Forms.Control> fokusu třídy dojde v následujícím pořadí. :  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 Když změníte fokus pomocí myši nebo voláním <xref:System.Windows.Forms.Control.Focus%2A> metody, dojde k události <xref:System.Windows.Forms.Control> třídy v následujícím pořadí:  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Viz také:

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
