---
title: Odebrání obsahu uzlu v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 737766586ee920a87c25dd42896bdfb14ae69d98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698704"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="d06b6-102">Odebrání obsahu uzlu v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="d06b6-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="d06b6-103">Pro typy uzlů, které dědí z <xref:System.Xml.XmlCharacterData>, které jsou <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, a <xref:System.Xml.XmlSignificantWhitespace> typy uzlů, můžete odebrat pomocí znaků <xref:System.Xml.XmlCharacterData.DeleteData%2A> metodu, která odebere rozsah znaky z uzlu.</span><span class="sxs-lookup"><span data-stu-id="d06b6-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="d06b6-104">Pokud chcete úplně odebrat obsah, můžete odebrat uzel, který obsahuje obsah.</span><span class="sxs-lookup"><span data-stu-id="d06b6-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="d06b6-105">Pokud chcete zachovat uzlu, ale obsah je nesprávná, změňte obsah.</span><span class="sxs-lookup"><span data-stu-id="d06b6-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="d06b6-106">Informace o úpravě obsahu uzlu najdete v tématu [úprava uzlů, obsahu a hodnot v dokumentu XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="d06b6-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06b6-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d06b6-107">See also</span></span>

- [<span data-ttu-id="d06b6-108">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="d06b6-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
