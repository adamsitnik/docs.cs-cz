---
title: Rozšíření zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 798a1d1cd21fd9a0bc21c6ccaa42c478379cc7a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511534"
---
# <a name="extending-security"></a><span data-ttu-id="2de6c-102">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2de6c-102">Extending Security</span></span>
<span data-ttu-id="2de6c-103">Tak, aby vyhovovaly nové typy deklarací identity a vlastní tokeny, můžete rozšířit Infrastruktura zabezpečení Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2de6c-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="2de6c-104">Témata v této části ukazují, jak to lze provést.</span><span class="sxs-lookup"><span data-stu-id="2de6c-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2de6c-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2de6c-105">In This Section</span></span>  
 [<span data-ttu-id="2de6c-106">Architektura zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2de6c-106">Security Architecture</span></span>](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)  
 <span data-ttu-id="2de6c-107">Provede architekturu jako systém zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="2de6c-107">Walks through the architecture of the WCF security system.</span></span>  
  
 [<span data-ttu-id="2de6c-108">Vlastní přihlašovací údaje a jejich ověřování</span><span class="sxs-lookup"><span data-stu-id="2de6c-108">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="2de6c-109">Vysvětluje, jak modelem Identity se používá při ověřování vlastní přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="2de6c-109">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="2de6c-110">Vlastní tokeny</span><span class="sxs-lookup"><span data-stu-id="2de6c-110">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="2de6c-111">Vystavené tokeny z tokenu služby zabezpečení (STS) jsou obvykle tokeny SAML.</span><span class="sxs-lookup"><span data-stu-id="2de6c-111">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="2de6c-112">Toto téma vysvětluje, jak vytvořit vlastní typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="2de6c-112">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="2de6c-113">Vlastní autorizace</span><span class="sxs-lookup"><span data-stu-id="2de6c-113">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="2de6c-114">Vysvětluje, jak implementovat vlastní autorizace.</span><span class="sxs-lookup"><span data-stu-id="2de6c-114">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="2de6c-115">Přepsání identity služby kvůli ověřování</span><span class="sxs-lookup"><span data-stu-id="2de6c-115">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="2de6c-116">Popisuje přepsání identity služby kvůli ověřování.</span><span class="sxs-lookup"><span data-stu-id="2de6c-116">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="2de6c-117">Postupy: Vytvoření vlastního ověřovatele Identity</span><span class="sxs-lookup"><span data-stu-id="2de6c-117">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="2de6c-118">Ukazuje, jak se ověřit identitu vlastní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="2de6c-118">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="2de6c-119">Postupy: Použití samostatných certifikátů X.509 pro přihlašování a šifrování</span><span class="sxs-lookup"><span data-stu-id="2de6c-119">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="2de6c-120">Zprávy jsou obvykle podepsaný a zašifrovaný s jedním certifikátem.</span><span class="sxs-lookup"><span data-stu-id="2de6c-120">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="2de6c-121">Toto téma vysvětluje, jak dva certifikáty je možné, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="2de6c-121">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="2de6c-122">Postupy: Změna zprostředkovatele kryptografických služeb pro privátní klíč certifikátu X.509</span><span class="sxs-lookup"><span data-stu-id="2de6c-122">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="2de6c-123">Vysvětluje, jak změnit zprostředkovatele kryptografických služeb používají k zajištění privátní klíč certifikátu X.509 a jak integrovat zprostředkovatele do rozhraní Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2de6c-123">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2de6c-124">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2de6c-124">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="2de6c-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2de6c-125">Related Sections</span></span>  
 [<span data-ttu-id="2de6c-126">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2de6c-126">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="2de6c-127">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="2de6c-127">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="2de6c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2de6c-128">See also</span></span>
- [<span data-ttu-id="2de6c-129">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2de6c-129">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
