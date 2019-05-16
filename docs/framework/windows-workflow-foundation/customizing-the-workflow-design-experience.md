---
title: Přizpůsobení prostředí pro návrh pracovního postupu
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 926edb4478551affa03619f44ee886d5eb591e4d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637281"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="3d55d-102">Přizpůsobení prostředí pro návrh pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3d55d-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="3d55d-103">Scénáře pro návrh vlastní aktivity a změna hostování [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] byly výrazně zjednodušené [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d55d-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="3d55d-104">Vývoj a nasazení jsou teď jednodušší a flexibilnější.</span><span class="sxs-lookup"><span data-stu-id="3d55d-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="3d55d-105">Změny klíče infrastruktury je, že nové návrháře programovací model aktivity je postavená na Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="3d55d-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="3d55d-106">To vám dává možnost definovat deklarativně návrháři aktivit a opětovným hostováním [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v ostatních aplikacích s srovnávací snadné.</span><span class="sxs-lookup"><span data-stu-id="3d55d-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="3d55d-107">Při opětovném hostování, editoru vlastních výrazů mohou být vytvořeny pro podporu technologie IntelliSense nebo doméně jednodušší výraz.</span><span class="sxs-lookup"><span data-stu-id="3d55d-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="3d55d-108">Integrace s Windows Communication Foundation (WCF) se stal bezproblémové s využitím služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="3d55d-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="3d55d-109">Ke zvýšení návrhu v Návrháři postupu provádění se změněným hostováním prostředí čas můžete použít vlastní návrháři aktivit a položka stromu modelu.</span><span class="sxs-lookup"><span data-stu-id="3d55d-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3d55d-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3d55d-110">In This Section</span></span>

 [<span data-ttu-id="3d55d-111">Použití vlastních návrhářů a šablon aktivity</span><span class="sxs-lookup"><span data-stu-id="3d55d-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="3d55d-112">Popisuje, jak vytvořit novou vlastní aktivitu návrhářů a šablon.</span><span class="sxs-lookup"><span data-stu-id="3d55d-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="3d55d-113">Změna hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="3d55d-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="3d55d-114">Popisuje, jak znovu hostovat [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] mimo aplikaci Visual Studio a jak zobrazit chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="3d55d-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="3d55d-115">Použití editoru vlastních výrazů</span><span class="sxs-lookup"><span data-stu-id="3d55d-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="3d55d-116">Popisuje, jak implementovat editoru vlastních výrazů pomocí návrháře postupu provádění se změněným hostováním mimo sadu Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="3d55d-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="3d55d-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="3d55d-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="3d55d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d55d-118">See also</span></span>

- [<span data-ttu-id="3d55d-119">Rozšíření Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="3d55d-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="3d55d-120">Návrhář</span><span class="sxs-lookup"><span data-stu-id="3d55d-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="3d55d-121">Návrháři vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="3d55d-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="3d55d-122">Změna hostování návrháře</span><span class="sxs-lookup"><span data-stu-id="3d55d-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
