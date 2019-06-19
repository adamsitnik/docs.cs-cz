---
title: Podpora pro funkci msxsl:node-set()
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7310d70aa695043a935f9bd74af8e8475eda73d4
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170883"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="ee69e-102">Podpora pro funkci msxsl:node-set()</span><span class="sxs-lookup"><span data-stu-id="ee69e-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="ee69e-103">`msxsl:node-set` Funkce lze převést na sadu uzlu fragment stromu výsledek.</span><span class="sxs-lookup"><span data-stu-id="ee69e-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="ee69e-104">Výsledný uzel vždy nastavit obsahuje jeden uzel a je kořenový uzel stromu.</span><span class="sxs-lookup"><span data-stu-id="ee69e-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee69e-105"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralé v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="ee69e-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="ee69e-106">Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="ee69e-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="ee69e-107">Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="ee69e-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="ee69e-108">`msxsl:node-set` Funkce lze převést na sadu uzlu fragment stromu výsledek.</span><span class="sxs-lookup"><span data-stu-id="ee69e-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="ee69e-109">Výsledný uzel vždy nastavit obsahuje jeden uzel a je kořenový uzel stromu.</span><span class="sxs-lookup"><span data-stu-id="ee69e-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee69e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee69e-110">Example</span></span>  
 <span data-ttu-id="ee69e-111">V následujícím příkladu `$var` je proměnná, která je uzel stromu v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="ee69e-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="ee69e-112">Pro každý příkaz v kombinaci s `node-set` funkce umožňuje uživateli k iteraci přes tento uzel stromu jako sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="ee69e-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="ee69e-113">nodeset.xsl</span><span class="sxs-lookup"><span data-stu-id="ee69e-113">nodeset.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">   
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="ee69e-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="ee69e-114">Output</span></span>  
 <span data-ttu-id="ee69e-115">Výstup této transformace je</span><span class="sxs-lookup"><span data-stu-id="ee69e-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee69e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee69e-116">See also</span></span>

- [<span data-ttu-id="ee69e-117">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="ee69e-117">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
