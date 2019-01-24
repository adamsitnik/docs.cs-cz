---
title: Kustomizace možností návrhu pracovního postupu
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 87b49b025cfb27812933511b76c5a024cde4995a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680297"
---
# <a name="customizing-the-workflow-design-experience"></a>Kustomizace možností návrhu pracovního postupu

Scénáře pro návrh vlastní aktivity a změna hostování [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] byly výrazně zjednodušené [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Vývoj a nasazení jsou teď jednodušší a flexibilnější. Změny klíče infrastruktury je, že nové návrháře programovací model aktivity je postavená na Windows Presentation Foundation (WPF). To vám dává možnost definovat deklarativně návrháři aktivit a opětovným hostováním [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v ostatních aplikacích s srovnávací snadné. Při opětovném hostování, editoru vlastních výrazů mohou být vytvořeny pro podporu technologie IntelliSense nebo doméně jednodušší výraz. Integrace s Windows Communication Foundation (WCF) se stal bezproblémové s využitím služeb pracovních postupů. Ke zvýšení návrhu v Návrháři postupu provádění se změněným hostováním prostředí čas můžete použít vlastní návrháři aktivit a položka stromu modelu.

## <a name="in-this-section"></a>V tomto oddílu

 [Použití vlastních návrhářů a šablon aktivity](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)

 Popisuje, jak vytvořit novou vlastní aktivitu návrhářů a šablon.

 [Změna hostování Návrháře postupu provádění](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)

 Popisuje, jak znovu hostovat [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] mimo aplikaci Visual Studio a jak zobrazit chyby ověření.

 [Použití editoru vlastních výrazů](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)

 Popisuje, jak implementovat editoru vlastních výrazů pomocí návrháře postupu provádění se změněným hostováním mimo sadu Visual Studio 2010.

## <a name="reference"></a>Odkaz

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>Viz také:

- [Rozšíření Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/extend.md)
- [Návrhář](../../../docs/framework/windows-workflow-foundation/samples/designer.md)
- [Návrháři vlastních aktivit](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)
- [Změna hostování návrháře](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)