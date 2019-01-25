---
title: Generování klíčů pro šifrování a dešifrování
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32f9a5f92ae580839ce46476de9f9c7edcd54685
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573397"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Generování klíčů pro šifrování a dešifrování
Vytváření a správa klíčů je důležitou součástí procesu šifrování. Symetrické algoritmy vyžadují vytvoření klíče a inicializačního vektoru (IV). Klíč musí být udržen v tajnosti před kýmkoli, kdo by neměl data dešifrovat. Vektor IV nemusí být tajný, ale měli byste jej pro jednotlivé relace změnit. Asymetrické algoritmy vyžadují vytvoření veřejného klíče a soukromého klíče. Veřejný klíč se může zveřejnit všem uživatelům, zatímco soukromý klíč smí být znám pouze osobě, která bude dešifrovat data zašifrovaná pomocí veřejného klíče. V této části je popsán způsob vytváření a správy klíčů pro symetrické i asymetrické algoritmy.  
  
## <a name="symmetric-keys"></a>Symetrické klíče  
 Třídy pro symetrické šifrování poskytované rozhraním .NET Framework vyžadují klíč a nový inicializační vektor (IV) k šifrování a dešifrování dat. Kdykoli vytvoříte novou instanci některé ze spravovaných symetrických kryptografických tříd pomocí výchozího konstruktoru, automaticky se vytvoří nový klíč a vektor IV. Jakákoli osoba s oprávněním k dešifrování dat musí mít stejný klíč a vektor IV a použít stejný algoritmus. Obecně lze říci, že nový klíč a vektor IV by měly být vytvořeny pro každou relaci a klíč ani vektor IV by neměly být ukládány pro používání v pozdější relaci.  
  
 Ke sdělení symetrického klíče a vektoru IV vzdálené straně je obvykle třeba zašifrovat symetrický klíč pomocí asymetrického šifrování. Odesílání klíče v nezabezpečené síti bez šifrování je velmi nebezpečné, jelikož jakákoli osoba, která klíč a vektor IV zachytí, může data dešifrovat. Další informace o výměně dat s využitím šifrování naleznete v tématu [vytváření šifrovacích schémat](../../../docs/standard/security/creating-a-cryptographic-scheme.md).  
  
 Následující příklad znázorňuje vytvoření nové instance třídy <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>, která implementuje algoritmus TripleDES.  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
```  
  
 Při spuštění předchozího kódu jsou nový klíč a vektor IV generovány a umístěny v **klíč** a **IV** vlastnosti, v uvedeném pořadí.  
  
 Občas bude pravděpodobně nutné generovat více klíčů. V takovém případě můžete vytvořit novou instanci třídy, která implementuje symetrický algoritmus a pak vytvořte nový klíč a vektor IV voláním **GenerateKey** a **GenerateIV** metody. Následující příklad kódu ukazuje, jak vytvářet nové klíče a vektory IV po vytvoření nové instance třídy symetrický kryptografických.  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
TDES.GenerateIV()  
TDES.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
TDES.GenerateIV();  
TDES.GenerateKey();  
```  
  
 Po spuštění předchozího kódu jsou klíč a vektor IV generovány při nové instance **TripleDESCryptoServiceProvider** tvoří. Další klíč a vektor IV se vytvoří, pokud **GenerateKey** a **GenerateIV** metody jsou volány.  
  
## <a name="asymmetric-keys"></a>Asymetrické klíče  
 Rozhraní .NET Framework poskytuje třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> a <xref:System.Security.Cryptography.DSACryptoServiceProvider> pro asymetrické šifrování. Tyto třídy vytvoří pár veřejného/soukromého klíče při vytváření nové instance pomocí výchozího konstruktoru. Asymetrické klíče mohou být buď uloženy pro použití ve více relacích, nebo generovány pouze pro jednu relaci. Zatímco veřejný klíč může být zpřístupněn veřejně, soukromý klíč by měl být přísně chráněný.  
  
 Pár veřejného/soukromého klíče je generován při každém vytvoření nové instance třídy asymetrického algoritmu. Po vytvoření nové instance třídy může být informace o klíči extrahována pomocí jedné ze dvou metod:  
  
-   <xref:System.Security.Cryptography.RSA.ToXmlString%2A> Metoda, která vrátí reprezentaci XML informace o klíči.  
  
-   Metodou <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A>, která vrátí strukturu <xref:System.Security.Cryptography.RSAParameters> s informacemi o klíči.  
  
 Obě metody přijímají logickou hodnotu, která označuje, zda vrátit informace pouze o veřejném klíči nebo zda vrátit také informace o veřejném klíči a soukromém klíči. **RSACryptoServiceProvider** třídy mohou být inicializovány na hodnotu **RSAParameters** struktury pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> metody.  
  
 Asymetrické soukromé klíče by nikdy neměly být uloženy doslovně nebo ve formátu prostého textu v místním počítači. Pokud potřebujete uložit soukromý klíč, měli byste použít kontejner klíčů. Další informace o způsobu uložení soukromého klíče v kontejneru klíčů naleznete v tématu [jak: Store asymetrického klíče v kontejneru klíčů](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Následující příklad kódu vytvoří novou instanci třídy **RSACryptoServiceProvider** třídy vytvoří pár veřejného a privátního klíče a uloží údaje o veřejném klíči do **RSAParameters** struktury.  
  
```vb  
'Generate a public/private key pair.  
Dim RSA as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim RSAKeyInfo As RSAParameters = RSA.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters RSAKeyInfo = RSA.ExportParameters(false);  
```  
  
## <a name="see-also"></a>Viz také:

- [Šifrování dat](../../../docs/standard/security/encrypting-data.md)
- [Dešifrování dat](../../../docs/standard/security/decrypting-data.md)
- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
- [Postupy: Store asymetrického klíče v kontejneru klíčů](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
