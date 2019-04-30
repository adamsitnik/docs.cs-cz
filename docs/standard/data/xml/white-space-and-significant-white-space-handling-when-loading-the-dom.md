---
title: Zpracování mezer a významných mezer při načítání modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d9bbb14320b84a6d417c5c28026b169092de219
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799330"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Zpracování mezer a významných mezer při načítání modelu DOM
Při načítání dokumentu, můžete nastavit možnost zachovat mezer a vytvořit **XmlWhitespace** uzlů ve stromu dokumentu. Chcete-li vytvořit prázdné znaky uzly, nastavte **PreserveWhitespace** vlastnost na hodnotu true. Pokud je nastavena na **false**, což je výchozí, nejsou vytvořeny uzly mezer. Významné prázdné znaky uzly se vždy zachovají, a **XmlSignificantWhitespace** v paměti, která bude představovat tato data, bez ohledu na nastavení se vždy vytvářejí uzly **PreserveWhitespace** příznak.  
  
 Pokud dokument je načtena z čtečky, potom nastavení z **PreserveWhitespace** příznaku vlastnost **XmlDocument** třída má vliv na vytváření **XmlWhitespace** uzly pouze tehdy, když **WhitespaceHandling** vlastnost **XmlTextReader** není nastavená na **: WhitespaceHandling.None**. Je hodnota **WhitespaceHandling** vlastnost čtecího zařízení, která má přednost před nastavením tohoto příznaku na **XmlDocument**. Další informace o **XmlSignificantWhitespace**, naleznete v tématu <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
