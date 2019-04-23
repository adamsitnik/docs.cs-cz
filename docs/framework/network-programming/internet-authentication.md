---
title: Ověřování v internetu
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
ms.openlocfilehash: 8b17f5a7167eb539e04a19db797bc1b0cc6c5eaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295455"
---
# <a name="internet-authentication"></a>Ověřování v internetu
<xref:System.Net> Třídy podporu různých mechanismů ověřování klienta, včetně standardní Internet metody ověřování basic, digest, negotiate, NTLM a ověřování protokolu Kerberos, jakož i vlastních metod, které můžete vytvořit.  
  
 Přihlašovací údaje pro ověření jsou uloženy v <xref:System.Net.NetworkCredential> a <xref:System.Net.CredentialCache> třídy, které implementují <xref:System.Net.ICredentials> rozhraní. Při jedné z těchto tříd je dotazován na přihlašovací údaje, vrátí instanci **NetworkCredential** třídy. Spravuje proces ověřování <xref:System.Net.AuthenticationManager> třídy a procesu skutečné ověřování se provádí pomocí třídy modulu ověřování, který implementuje <xref:System.Net.IAuthenticationModule> rozhraní. Je nutné zaregistrovat vlastní ověřovací modul s **správce AuthenticationManager** předtím, než je možné ho; moduly pro úroveň basic, digest, negotiate, NTLM, a ve výchozím nastavení jsou registrované metody ověřování protokolu Kerberos.  
  
 **NetworkCredential** ukládá sadu přihlašovacích údajů, které jsou přidružené k jedné Internet zdroje identifikovaného identifikátorem URI a vrátí odpověď na kterémkoli volání <xref:System.Net.NetworkCredential.GetCredential%2A> metody. **NetworkCredential** třídy se obvykle používá u aplikací, které přistupují k omezený počet internetové prostředky nebo aplikace, které používají stejnou sadu přihlašovacích údajů ve všech případech.  
  
 **CredentialCache** třídy ukládá kolekce přihlašovací údaje pro různé webové prostředky. Když <xref:System.Net.CredentialCache.GetCredential%2A> metoda je volána, **CredentialCache** vrátí správné přihlašovací údaje, podle identifikátoru URI webového prostředku a schéma požadovaný ověřování. Aplikace, které používají různé druhy prostředků Internetu pomocí různých ověřovacích schémat s výhodou využít **CredentialCache** třídy, protože ukládá všechny přihlašovací údaje a poskytuje je podle požadavku.  
  
 Když internetových prostředků o ověření, <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> metoda odešle <xref:System.Net.WebRequest> k **správce AuthenticationManager** spolu s požadavkem na pověření. Pak je požadavek ověřen podle následujícího postupu:  
  
1. **Správce AuthenticationManager** volání <xref:System.Net.IAuthenticationModule.Authenticate%2A> metodu na každý registrovaný ověřovací moduly v pořadí, které jste zaregistrovali. **Správce AuthenticationManager** použije první modul, který nevrací **null** provádět v procesu ověřování. Podrobnosti o procesu se liší v závislosti na typu zahrnutých ověřovací modul.  
  
2. Po dokončení procesu ověřování ověřovací modul vrátí <xref:System.Net.Authorization> k **WebRequest** , který obsahuje informace potřebné pro přístup k internetového zdroji.  
  
 Některá schémata ověřování můžete ověřovat uživatele bez provedení první požadavek pro prostředek. Aplikace můžete ušetřit čas tím preauthenticating uživatele s prostředkem, čímž se zmenšuje alespoň jednu výměnu zpráv pro server. Nebo, aby bylo možné později se více přizpůsobovat uživateli může provést ověření při spuštění programu. Schémata ověřování, které můžete použít sadu předběžné ověření <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> vlastnost **true**.  
  
## <a name="see-also"></a>Viz také:

- [Základní ověřování a ověřování algoritmem Digest](../../../docs/framework/network-programming/basic-and-digest-authentication.md)
- [Ověřování NTLM a Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)
- [Zabezpečení v síťovém programování](../../../docs/framework/network-programming/security-in-network-programming.md)
