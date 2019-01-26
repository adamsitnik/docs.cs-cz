---
title: Mapování identifikátorů objektů na algoritmy šifrování
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: 000d5d94b19907dfed40ac03f3172b9b8449c6f2
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083445"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="6b94f-102">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="6b94f-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="6b94f-103">Digitální podpisy Ujistěte se, že data bez dozoru při odeslání z jedné aplikace do jiného.</span><span class="sxs-lookup"><span data-stu-id="6b94f-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="6b94f-104">Obvykle digitální podpis je vypočítán s použitím matematické funkce hash data, která mají být podepsán.</span><span class="sxs-lookup"><span data-stu-id="6b94f-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="6b94f-105">Při formátování hodnoty hash podepsat, některé algoritmy digitálního podpisu připojí ASN.1 identifikátor objektu (OID) v rámci operace formátování.</span><span class="sxs-lookup"><span data-stu-id="6b94f-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="6b94f-106">Identifikátor OID Určuje algoritmus, který byl použit pro výpočet hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="6b94f-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="6b94f-107">Algoritmy můžete namapovat na identifikátory objektů rozšířit mechanismus kryptografie na vlastní algoritmy.</span><span class="sxs-lookup"><span data-stu-id="6b94f-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="6b94f-108">Následující příklad ukazuje, jak namapovat identifikátor objektu na nový algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="6b94f-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="6b94f-109">[ \<Oidentry – > element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) obsahuje dva atributy.</span><span class="sxs-lookup"><span data-stu-id="6b94f-109">The [\<oidEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="6b94f-110">**OID** atribut je identifikátor objektu.</span><span class="sxs-lookup"><span data-stu-id="6b94f-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="6b94f-111">**Název** atribut je hodnota **název** atribut z [ \<nameEntry > element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="6b94f-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="6b94f-112">Musí existovat mapování z název algoritmu na třídu před identifikátor objektu lze mapovat na jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="6b94f-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b94f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b94f-113">See also</span></span>
- [<span data-ttu-id="6b94f-114">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="6b94f-114">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="6b94f-115">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="6b94f-115">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
