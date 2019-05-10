---
title: Překlad externích prostředků během zpracování XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bcd45a97ab0f0b0ac462d50c18fb68f9d7bd386
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590027"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="5fc43-102">Překlad externích prostředků během zpracování XSLT</span><span class="sxs-lookup"><span data-stu-id="5fc43-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="5fc43-103">Existují několikrát během transformace XSLT, kdy budete muset vyřešit externím prostředkům.</span><span class="sxs-lookup"><span data-stu-id="5fc43-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="5fc43-104">Pomocí třídy objekt XmlResolver</span><span class="sxs-lookup"><span data-stu-id="5fc43-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="5fc43-105"><xref:System.Xml.XmlResolver> Třída se používá k překladu externích prostředků.</span><span class="sxs-lookup"><span data-stu-id="5fc43-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="5fc43-106">Následující tabulka popisuje, kdy <xref:System.Xml.XmlResolver> stane používané během zpracování XSLT.</span><span class="sxs-lookup"><span data-stu-id="5fc43-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="5fc43-107">Úloha XSLT</span><span class="sxs-lookup"><span data-stu-id="5fc43-107">XSLT task</span></span>|<span data-ttu-id="5fc43-108">Co objekt XmlResolver slouží</span><span class="sxs-lookup"><span data-stu-id="5fc43-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="5fc43-109">Zkompilujte šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="5fc43-109">Compile the style sheet.</span></span>|<span data-ttu-id="5fc43-110">Rozpoznat identifikátor URI šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="5fc43-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="5fc43-111">- a -</span><span class="sxs-lookup"><span data-stu-id="5fc43-111">-and-</span></span><br /><br /> <span data-ttu-id="5fc43-112">Identifikátor URI odkazy v libovolném `xsl:import` nebo `xsl:include` elementy.</span><span class="sxs-lookup"><span data-stu-id="5fc43-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="5fc43-113">Spuštění šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="5fc43-113">Execute the style sheet.</span></span>|<span data-ttu-id="5fc43-114">Identifikátor URI dokumentu kontextu přeložit.</span><span class="sxs-lookup"><span data-stu-id="5fc43-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="5fc43-115">- a -</span><span class="sxs-lookup"><span data-stu-id="5fc43-115">-and-</span></span><br /><br /> <span data-ttu-id="5fc43-116">Identifikátor URI odkazy v jakékoli XSLT `document()` funkce.</span><span class="sxs-lookup"><span data-stu-id="5fc43-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="5fc43-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> a <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody přetížení, která přijímají patří <xref:System.Xml.XmlResolver> objektu jako jeden z jejích argumentů.</span><span class="sxs-lookup"><span data-stu-id="5fc43-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="5fc43-118">Pokud <xref:System.Xml.XmlResolver> nezadá, výchozí <xref:System.Xml.XmlUrlResolver> se používá bez pověření.</span><span class="sxs-lookup"><span data-stu-id="5fc43-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="5fc43-119">Následující seznam popisuje, kdy je vhodné zadat <xref:System.Xml.XmlResolver> objektu:</span><span class="sxs-lookup"><span data-stu-id="5fc43-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="5fc43-120">Pokud XSLT procesu potřebuje přístup k síťovému prostředku, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebné přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="5fc43-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="5fc43-121">Pokud chcete omezit prostředky, které můžete přistupovat k procesu XSLT, můžete použít <xref:System.Xml.XmlSecureResolver> nastavte správné oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5fc43-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="5fc43-122">Použití <xref:System.Xml.XmlSecureResolver> třídy, pokud je potřeba otevřít prostředek, který není pod kontrolou, nebo, který není důvěryhodný.</span><span class="sxs-lookup"><span data-stu-id="5fc43-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="5fc43-123">Pokud chcete přizpůsobit chování, můžete implementovat vlastní <xref:System.Xml.XmlResolver> třídy a použít ho k vyřešení zdroje.</span><span class="sxs-lookup"><span data-stu-id="5fc43-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="5fc43-124">Pokud chcete zajistit, že jsou přístupné žádné externí prostředky, můžete zadat `null` pro <xref:System.Xml.XmlResolver> argument.</span><span class="sxs-lookup"><span data-stu-id="5fc43-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fc43-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fc43-125">Example</span></span>  
 <span data-ttu-id="5fc43-126">Následující příklad se zkompiluje šablony stylů, která je uložená na síťovém prostředku.</span><span class="sxs-lookup"><span data-stu-id="5fc43-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="5fc43-127"><xref:System.Xml.XmlUrlResolver> Objekt Určuje přihlašovací údaje potřebné pro přístup k šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="5fc43-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="5fc43-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fc43-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="5fc43-129">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="5fc43-129">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
