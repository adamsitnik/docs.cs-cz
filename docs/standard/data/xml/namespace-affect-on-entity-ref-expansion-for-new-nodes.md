---
title: Vliv oboru názvů na rozšíření odkazu na entitu pro nové uzly, který obsahují elementy a atributy
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4231516848cc50212a3a6a03d101907b2f6b3920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027105"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="c3c6c-102">Vliv oboru názvů na rozšíření odkazu na entitu pro nové uzly, který obsahují elementy a atributy</span><span class="sxs-lookup"><span data-stu-id="c3c6c-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="c3c6c-103">Protože obsah entity deklarace může obsahovat prakticky cokoli, je možné, že obsah by mohl obsahovat prvky jako `<!ENTITY aname "<elem>test</elem>">`.</span><span class="sxs-lookup"><span data-stu-id="c3c6c-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="c3c6c-104">Když je analyzovat kód XML, `&aname;` není rozbalen jeho nahrazení obsahu při analýze.</span><span class="sxs-lookup"><span data-stu-id="c3c6c-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="c3c6c-105">Rozšíření XML není provést, protože rozlišení oboru názvů pro element nelze provést, dokud se uzel je umístěn v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c3c6c-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="c3c6c-106">Do té doby není k dispozici žádné znalosti z jaké obor názvů je v oboru.</span><span class="sxs-lookup"><span data-stu-id="c3c6c-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="c3c6c-107">Pokud uzel přejde do dokumentu, pak dojde k rozlišení oboru názvů a výsledné entity obsahu je analyzován do jeho odpovídající uzly.</span><span class="sxs-lookup"><span data-stu-id="c3c6c-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3c6c-108">Jakmile dojde k rozšíření v uzlu odkaz na nově vytvořenou entitu, se nikdy bude vyskytovat i nadále.</span><span class="sxs-lookup"><span data-stu-id="c3c6c-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="c3c6c-109">Proto jsou obory názvů používané v náhradní text pro prvek vázány v době, který je nastaven na nadřazený uzel.</span><span class="sxs-lookup"><span data-stu-id="c3c6c-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="c3c6c-110">Ale oboru názvů lze změnit pro existující uzly odkaz na entitu když odeberete a vložit je někde jinde, nebo odkaz na uzlech entity, které se klonují se **CloneNode** metody.</span><span class="sxs-lookup"><span data-stu-id="c3c6c-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3c6c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3c6c-111">See also</span></span>

- [<span data-ttu-id="c3c6c-112">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="c3c6c-112">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
