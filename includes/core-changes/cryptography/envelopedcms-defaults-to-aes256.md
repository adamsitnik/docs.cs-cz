---
ms.openlocfilehash: f9000b19997201c2d3de0643669f9029ff1ca31c
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237326"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnvelopedCms ve výchozím nastavení šifrování AES-256

Výchozí algoritmus symetrického šifrování používaný `EnvelopedCms` se změnil z TripleDES na AES-256.

#### <a name="change-description"></a>Změnit popis

V rozhraní .NET Core Preview 7 a starších verzích, když <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> slouží k šifrování dat bez určení symetrického šifrovacího algoritmu prostřednictvím přetížení konstruktoru, byla data zašifrována pomocí algoritmu TripleDES/3DES/3DEA/DES3-EDE.

Počínaje rozhraním .NET Core 3,0 Preview 8 (přes 4.6.0 verze balíčku [System. Security. Cryptography. PKCS](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) ) se výchozí algoritmus změnil na AES-256 pro modernizaci algoritmu a pro zlepšení zabezpečení výchozích možností. Pokud certifikát příjemce zprávy obsahuje veřejný klíč Diffie-Hellman (jiný než EC), může operace šifrování selhat s <xref:System.Security.Cryptography.CryptographicException> v důsledku omezení v základní platformě.

V následujícím ukázkovém kódu jsou data při použití v rozhraní .NET Core 3,0 Preview 7 nebo starší zašifrovaná pomocí TripleDES. Pokud používáte .NET Core 3,0 Preview 8 nebo novější, je zašifrovaný pomocí AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 8

#### <a name="recommended-action"></a>Doporučená akce

Pokud se změnou negativně neovlivní změna, můžete šifrování TripleDES obnovit explicitním zadáním identifikátoru šifrovacího algoritmu v konstruktoru <xref:System.Security.Cryptography.Pkcs.EnvelopedCms>, který obsahuje parametr typu <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, například:

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>Category

Kryptografie

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
