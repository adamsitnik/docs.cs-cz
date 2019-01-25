---
title: 'Postupy: Použití víc tokenů zabezpečení stejného typu'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 40fc95c905f8923b8aaf2c97fb9dc2b937dfb06f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691344"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="d8c8d-102">Postupy: Použití víc tokenů zabezpečení stejného typu</span><span class="sxs-lookup"><span data-stu-id="d8c8d-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
-   <span data-ttu-id="d8c8d-103">V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, klienta zprávy pouze omezením jeden token daného typu.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-103">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="d8c8d-104">Zprávy klienta teď může obsahovat více tokenů typu.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="d8c8d-105">Toto téma ukazuje, jak zahrnout více tokenů stejného typu zprávy klienta.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
-   <span data-ttu-id="d8c8d-106">Poznámka: službu nelze nakonfigurovat tímto způsobem: Služba může obsahovat pouze jeden podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="d8c8d-107">Použití víc tokenů zabezpečení stejného typu</span><span class="sxs-lookup"><span data-stu-id="d8c8d-107">To use multiple security tokens of the same type</span></span>  
  
1.  <span data-ttu-id="d8c8d-108">Vytvořte kolekci elementů prázdný vazby který se má naplnit.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  <span data-ttu-id="d8c8d-109">Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> voláním <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  <span data-ttu-id="d8c8d-110">Vytvoření <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> kolekce.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  <span data-ttu-id="d8c8d-111">Tokeny SAML přidáte do kolekce.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  <span data-ttu-id="d8c8d-112">Kolekce, kterou chcete přidat <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  <span data-ttu-id="d8c8d-113">Přidání elementů vazby do kolekce elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  <span data-ttu-id="d8c8d-114">Vrátí novou vlastní vazbu vytvořené z kolekce elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="d8c8d-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8c8d-115">Example</span></span>  
 <span data-ttu-id="d8c8d-116">Níže je celý metody popsané v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="d8c8d-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="d8c8d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8c8d-117">See also</span></span>
- [<span data-ttu-id="d8c8d-118">Architektura zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d8c8d-118">Security Architecture</span></span>](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
