---
title: Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 4150d2f9634045351cb52e02c4f4807e55d118e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717891"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)
`My.Resources` Objekt poskytuje přístup k prostředkům vaší aplikace a vám umožní dynamicky načíst prostředky pro vaši aplikaci.  
  
## <a name="retrieving-resources"></a>Načítání prostředků  
 Počet prostředků, jako jsou zvukové soubory, ikony, obrázky a řetězce lze získat pomocí `My.Resources` objektu. Například můžete přistupovat soubory prostředků specifické pro jazykovou verzi aplikace. Následující příklad nastaví ikony ve formuláři na ikonu s názvem `Form1Icon` uložené v souboru prostředků aplikace.  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 `My.Resources` Zpřístupňuje pouze globální prostředky. Neposkytuje přístup k prostředku soubory spojené s formuláři. Musí přístup k prostředkům formuláře z formuláře.  
  
 Podobně platí `My.Settings` objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci. Další informace najdete v tématu [My.resources – objekt](../../../visual-basic/language-reference/objects/my-resources-object.md) a [My.Settings – objekt](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Viz také:
- [Objekt My.Resources](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [Objekt My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Přístup k nastavení aplikace](../../../visual-basic/developing-apps/programming/app-settings/index.md)
