---
ms.openlocfilehash: 8b41e3234c00059ecb5088bbf2597611d7f139b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981904"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a>RSACng a DSACng lze znovu použít v situacích částečné důvěryhodnosti

|   |   |
|---|---|
|Podrobnosti|CngLightup (používá v několika crypto vyšší úrovně rozhraní API, jako například <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) a <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> v některých případech Spolehněte se na úplný vztah důvěryhodnosti. Patří mezi ně volání nespravovaných kódů bez uplatnění <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> oprávnění a cesty kódu kde <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> má požadavky na oprávnění pro <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>. Od verze rozhraní .NET Framework 4.6.2, CngLightup byla použita k přepnutí do <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> kdykoli je to možné. V důsledku toho částečným vztahem důvěryhodnosti aplikací, které úspěšně použity <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> začal služeb při selhání a vyvolat <xref:System.Security.SecurityException> výjimky. Tato změna přidá že požadované nepodmíněné výrazy, tak, aby všechny funkce pomocí CngLightup nemá požadovaná oprávnění.|
|Doporučení|Pokud se tato změna v rozhraní .NET Framework 4.6.2 má negativně ovlivněn částečným vztahem důvěryhodnosti aplikací, upgradujte na rozhraní .NET Framework 4.7.1.|
|Rozsah|Edge|
|Version|4.6.2|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
