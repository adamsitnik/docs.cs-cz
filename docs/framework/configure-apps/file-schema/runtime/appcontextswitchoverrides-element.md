---
title: Element <AppContextSwitchOverrides>
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39060d503a006ab292818b58a6fa71f44dee68a0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423334"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides> Element
Definuje jeden nebo více přepínačů používané <xref:System.AppContext> třídě poskytnout mechanismus výslovného nesouhlasu pro nové funkce.  
  
 \<Konfigurace >  
 \<modul runtime >  
\<AppContextSwitchOverrides>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`value`|Požadovaný atribut.<br /><br /> Definuje jeden nebo více názvů switchů a jejich přidružené logické hodnoty.|  
  
### <a name="value-attribute"></a>Hodnota atributu  
  
|Value|Popis|  
|-----------|-----------------|  
|"název = hodnota"|Název předdefinované přepínače spolu s hodnotou (`true` nebo `false`). Více dvojice název/hodnota přepínače jsou odděleny středníky (";"). Seznam názvů předdefinované přepínač podporuje rozhraní .NET Framework naleznete v části poznámky.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze rozhraní .NET Framework 4.6 `<AppContextSwitchOverrides>` element v konfiguračním souboru umožňuje volajícím určit, jestli můžete své aplikace mohli využívat nové funkce nebo zachování kompatibility s předchozími verzemi knihovny rozhraní API. Například, pokud došlo ke změně chování rozhraní API mezi dvěma verzemi knihovny `<AppContextSwitchOverrides>` element umožňuje volající toto rozhraní API můžete kdykoliv zrušit nové chování ve verzích knihovny, které podporují nové funkce. Pro aplikace, které volají rozhraní API v rozhraní .NET Framework `<AppContextSwitchOverrides>` element můžete také povolit volající, jejichž aplikace cílí na starší verzi rozhraní .NET Framework pro přidání do nové funkce, pokud jejich aplikace běží na verzi rozhraní .NET Framework, která zahrnuje funkce.  
  
 `value` Atribut `<AppContextSwitchOverrides>` element se skládá z jednoho řetězce, který se skládá z jednoho nebo více dvojice název hodnota oddělené středníky.  Každý název identifikuje přepínač kompatibility a jeho odpovídající hodnota je logická hodnota (`true` nebo `false`), která označuje, zda je nastaven přepínač. Ve výchozím nastavení, je v přepínači `false`, a knihoven poskytuje nové funkce. Předchozí funkce poskytují pouze pokud přepínač nastavený (to znamená, je jeho hodnota `true`). To umožňuje knihovny k poskytnutí nové chování pro existující rozhraní API zároveň umožní volajícím, které závisí na předchozím chování chcete vyjádřit výslovný nesouhlas nové funkce.  
  
 Rozhraní .NET Framework podporuje následující přepínače:  
  
|Název přepínače|Popis|Zavedena|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Určuje, zda Windows Presentation Foundation používá starší verze algoritmu pro rozložení ovládacích prvků. Další informace najdete v tématu [omezení rizik: Rozložení WPF](../../../migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Určuje, zda je výchozí algoritmus používaný k podepisování součástí balíčku PackageDigitalSignatureManager SHA1 nebo SHA256.<br>Společnost Microsoft doporučuje způsobeny problémy kolizí se SHA1, SHA256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Pokud je nastavena na `false`, umožňuje ladění projektů pracovních postupů založených na XAML pomocí sady Visual Studio, když je povolený standard FIPS. Bez něj <xref:System.NullReferenceException> je vyvolána výjimka ve voláních metod v sestavení System.Activities.|Rozhraní .NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Určuje, zda kontrolního součtu pro instanci pracovního postupu v ladicím programu, používá algoritmus MD5 nebo SHA1. | Rozhraní .NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Určuje, zda pracovní postup kontrolní součet hash používá algoritmus SHA1 jako výchozí hodnotou v rozhraní .NET Framework 4.7 (`true`), nebo zda použije výchozí algoritmus SHA256 zavedeny jako výchozí hodnotou v rozhraní .NET Framework 4.8 (`false`).<br>Společnost Microsoft doporučuje způsobeny problémy kolizí se SHA1, SHA256.|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Určuje, zda získat trasování zásobníku při použití přenosných souborů PDB může zahrnovat informace o zdrojovém souboru a řádku. `false` informace zdrojového souboru a řádku; v opačném případě `true`.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Ovládací prvky, zda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda vyvolá výjimku při <xref:System.Drawing.Icon> objekt má snímky PNG. Další informace najdete v tématu [omezení rizik: PNG rámce v objektech ikonu](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Určuje, zda <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> objekty jsou správně odstraněn, když se přidá do kolekce podle <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> metody. `true` Chcete-li zachovat starší chování; `false` k uvolnění všech objektů privátní písma. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Ovládací prvky, zda výkon <xref:System.Windows.Forms.PrintPreviewDialog> je optimalizovaná pro síťové tiskárny. Další informace najdete v tématu [printpreviewdialog – Přehled ovládacího prvku](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Určuje, zda rozmezí let vyhledává japonský kalendář, který se vynucují větší počet období. `true` k vynucení rozmezí let vrací, a `false` zakázat je (výchozí chování). Další informace najdete v tématu [práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Určuje, zda pouze "1" je rozpoznán jako první rok japonský kalendář období v operacích analýzy. `true` rozpoznání pouze "1"; `false` rozpoznat "1" nebo Gannen (výchozí chování). Další informace najdete v tématu [práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Určuje, zda je první rok japonský kalendář období vyjádřena jako "1" nebo Gannen v operacích formátování. `true` k formátování éry. první rok jako "1"; `false` formátovat jako Gannen (výchozí chování). Další informace najdete v tématu [práce s kalendáři](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Určuje, zda asynchronní operace nejsou tok z kontextu volajícího vlákna. Další informace najdete v tématu [CurrentCulture a CurrentUICulture téct přes úlohy](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Ovládací prvky, zda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí shodovat s typem deklarace identity jenom s poslední položky DNS. Další informace najdete v tématu [omezení rizik: X509CertificateClaimSet.FindClaims Method](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Určuje, jestli se má povolit AuthorizationContext.Empty vrátit měnitelný objekt.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Ovládací prvky, zda cesty delší než `MAX_PATH` throw (260 znaků) <xref:System.IO.PathTooLongException>. Další informace najdete v tématu [dlouhá cesta podporu](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Určuje, zda nativní rutiny operačního systému se používají pro dekompresi podle <xref:System.IO.Compression.DeflateStream> třídy. `false` použití nativních rozhraní API; `true` používat <xref:System.IO.Compression.DeflateStream> implementace.|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Používá zpětné lomítko ("\\") namísto dopředného lomítka ("/") jako oddělovač cesty v <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnost. Další informace najdete v tématu [omezení rizik: Oddělovač cesty ZipArchiveEntry.FullName](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Určuje, jestli operační systém výjimky, které jsou vyvolány na pozadí podprocesů, které jsou vytvořené pomocí <xref:System.IO.Ports.SerialPort> datové proudy ukončit proces.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Určuje, zda se používá starší verzi cesta normalizace a cesty identifikátorů URI jsou podporovány <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody. Další informace najdete v tématu [omezení rizik: Cesta k normalizaci](../../../migration-guide/mitigation-path-normalization.md) a [omezení rizik: Cesta dvojtečka kontroly](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Určuje, jestli testu pro porovná rovnost <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> vlastností jednoho objektu s <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> vlastnost druhého objektu. Další informace najdete v tématu [nesprávná implementace MemberDescriptor.Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Zakáže rozšířené použití klíče (EKU) objektu (OID) identifikátor ověření certifikátu. Kolekce identifikátorů objektu (OID), které označují aplikace, které používají klíč je rozšíření rozšířené použití klíče (EKU).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Zakáže zmírnění protokol TLS 1.0 prohlížeče zneužít proti protokolu SSL/TLS (TOUCHDOWN) tím, že zakážete použití SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Ovládací prvky, zda <xref:System.Net.ServicePointManager?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> tříd můžete použít protokol SSL 3.0. Další informace najdete v tématu [omezení rizik: Protokoly TLS](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Zakáže SystemDefault TLS verze návrat zpět k výchozímu nastavení Tls12, Tls11, Tls.|Rozhraní .NET framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Zakáže upozornění SslStream TLS na straně serveru.|Rozhraní .NET framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Určuje, zda parametry ByRef SafeArray událostí modelu COM interop zařazování zpět do nativního kódu (`false`), nebo zda je zakázána zařazování zpět do nativního kódu (`true`).|.NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Ovládací prvky, zda [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializuje některé řídicí znaky na základě standardů ECMAScript V6 a V8. Další informace najdete v tématu [omezení rizik: Serializace ovládacího prvku znaků s vlastností objektu DataContractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| Rozhraní .NET framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Ovládací prvky, zda <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje víc úpravy nebo pouze jediné úpravy pro časové pásmo. Pokud `true`, použije <xref:System.TimeZoneInfo> typ k serializaci a deserializaci data a času; v opačném případě se použije <xref:System.TimeZone> typ, který nepodporuje víc úpravy pravidel.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Ovládací prvky, zda <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> používá větší velikost pole během objekt serializace a deserializace. Nastavte na tento přepínač `true` ke zlepšení výkonu serializace a deserializace velkých grafů objektů podle typů, jako <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Ovládací prvky, zda <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> konstruktor nastaví nový objekt <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> vlastnost s existující odkaz na objekt. Další informace najdete v tématu [omezení rizik: Konstruktor ClaimsIdentity](../../../migration-guide/mitigation-claimsidentity-constructor.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Ovládací prvky, zda pokus o opakované použití <xref:System.Security.Cryptography.AesCryptoServiceProvider> vyvolá modul pro dešifrování <xref:System.Security.Cryptography.CryptographicException>. Další informace najdete v tématu [AesCryptoServiceProvider modul pro dešifrování. nabízí opakovaně použitelné transformace](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Ovládací prvky, zda hodnota [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) vlastnost je [IntPtr](xref:System.IntPtr) , že zpracování představuje umístění okna v paměti, nebo zda je popisovač okna (popisovačem HWND). Další informace najdete v tématu [omezení rizik: CspParameters.ParentWindowHandle očekává, že popisovačem HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |Rozhraní .NET framework 4.7|   
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Určuje, zda použijte spravované kryptografie třídy v režimu FIPS vyvolá výjimku <xref:System.Security.Cryptography.CryptographicException> (`true`) nebo závisí na implementaci systémových knihoven (`false`).|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí nastavení pro některé operace SignedCMS SHA1 nebo SHA256.<br>Společnost Microsoft doporučuje způsobeny problémy kolizí se SHA1, SHA256.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Ovládací prvky, zda <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> metoda správně zpracovává všechny pojmenované křivky podporuje operační systém (`false`) nebo se vrátí ke starší verzi chování.|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Určuje, zda je výchozí nastavení pro některé operace SignedXML SHA1 nebo SHA256.<br>Společnost Microsoft doporučuje způsobeny problémy kolizí se SHA1, SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Určuje, zda `TransportWithMessageCredential` umožňuje režim zabezpečení zpráv pomocí bez znaménka "na" záhlaví. To je přepínač opt-in. Další informace najdete v tématu [změny v modulu Runtime v rozhraní .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Ovládací prvky, zda <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> vyvolá konstruktor <xref:System.ArgumentException> Pokud jeden z elementů je `null`.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Určuje, že zda pokus o použití X509 certifikáty pomocí zprostředkovatele úložiště klíčů CSG vyvolá výjimku. Další informace najdete v tématu [zabezpečení přenosu WCF podporuje certifikáty na Uložit pomocí CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Při použití přenosového protokolu HTTP s využitím služby v místním prostředí, pokud tuto hodnotu nastavíte `true` způsobí, že WCF ignorovat přidávání aplikací `Connection: close` záhlaví hlavičky odpovědi pro požadavek. Tuto hodnotu nastavíte na `false` umožňuje přidání `Connection: close` záhlaví hlavičky odpovědi, což vede k uzavření žádosti o soketu po odeslání odpovědi.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Zablokování obslužné rutiny, které jsou výsledkem omezení instance vícenásobné služby na jedno vlákno provádění v čase.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Spolu s `Switch.System.Net.DontEnableSchUseStrongCrypto`, určuje, jestli používá zabezpečení zpráv WCF TLS 1.1 a TLS 1.2.|Rozhraní .NET framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Hodnota `false` nastaví výchozí konfigurace umožňuje zvolit protokol operačního systému. Hodnota `true` nastaví výchozí nejvyšší protokolu, které jsou k dispozici. (K dispozici také v obslužná větev z předchozí verze rozhraní framework)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Určuje, zda je výchozí zprávu podpisový algoritmus pro zprávy služby MSMQ ve službě WCF SHA1 nebo SHA256.<br>Společnost Microsoft doporučuje způsobeny problémy kolizí se SHA1, SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Určuje, zda WCF používá ke generování náhodných názvů u pojmenovaných kanálů SHA1 nebo hodnotu hash SHA256.<br>Společnost Microsoft doporučuje způsobeny problémy kolizí se SHA1, SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Určuje, zda má být vyvolána [NullReferenceException](xref:System.NullReferenceException) při zpráva výjimky je null.|Rozhraní .NET framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Určuje, zda výjimky vyvolané při spuštění služby se rozšíří do volajícího <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> metody.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Ovládací prvky, zda <xref:System.Threading.Timer> vylepšení výkonu pro zajištění vysoce škálovatelné prostředí výhod instancí. Pokud `true`, vylepšení výkonu jsou povolené; Pokud `false` (výchozí hodnota), jsou zakázané.|.NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Určuje, zda některých procentuálně zakódovaný, které byly někdy dekódovat nyní konzistentně vlevo kódování znaků. Pokud `true`, jsou dekódovaný; v opačném případě `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Určuje zpracování obousměrné znaky Unicode v identifikátorech URI. `true` pro odstranění z identifikátorů URI; `false` zachovat a procent kódovat.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Určuje, zda Windows Presentation Foundation použije původní algoritmus (`true`) nebo nový algoritmus (`false`) v přidělování prostoru pro \*– sloupce. Další informace najdete v tématu [omezení rizik: Ovládací prvek mřížky přidělování místa na hvězdičku sloupce](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |Rozhraní .NET framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Určuje, zda selektor nebo na kartě řízení vždy aktualizuje hodnotu vlastností vybranou hodnotu před vyvoláním výběru ovládacích prvků událost změněné.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Určuje, zda je k dispozici pro vykreslování – doplněk pro úpravy na základě výběru <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.PasswordBox> ovládací prvky, aby se zabránilo occluded text (`false`), nebo zda text je vykreslen pouze ve vrstvě doplněk pro úpravy (`true`).|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Určuje, zda jsou nesprávně používá vlastní rozhraní IList indexery (`false`) nebo správně (`true`) podle <xref:System.Windows.Data.Binding?displayProperty=nameWithType> třídy.|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Určuje, zda DPI změnách na jednotlivé systému (hodnota `false`) nebo na monitorování jednotlivých (hodnotu `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Ovládací prvky, zda vylepšení v nastavení velikosti ovládacích prvků v <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> kdy WPF se spustí v režimu přehledu o za monitorování jsou zakázána (`true`) nebo povolené (`false`).|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Určuje, zda vývojář potřebuje pro zpracování speciálně <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akci, když je k dispozici text ovládacího prvku. `true` zpracování <xref:System.Windows.Forms.DomainUpDown.UpButton> akce; `false` pro <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> a <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akce, které byly správně synchronizované.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Požádá o mimo kód, který umožňuje vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace bezpečně filtrovat zprávy bez vyvolání výjimky při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda je volána. Další informace najdete v tématu [omezení rizik: Implementace vlastního IMessageFilter.PreFilterMessage](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Určuje, zda <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> vlastnost vrací správy zdrojového kódu, když uživatel otevře v nabídce vnořeném <xref:System.Windows.Forms.ToolStripMenuItem> ovládacího prvku. `true` Chcete-li vrátit `null`, starší chování; `false` vrátit správy zdrojového kódu.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Určuje, jestli je popisek volání podpory zakázaná (`true`) nebo povolené (`false`). Povolení podpory vyvolání popisku také vyžaduje funkce starší verze usnadnění určené `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`, a `Switch.UseLegacyAccessibilityFeatures.3` všechny deaktivuje (nastavena na `false`).|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Určuje, zda je volitelný `WM_POINTER`– na základě touch/stylus zásobníku je povolená v aplikaci WPF. Další informace najdete v tématu [omezení rizik: Dotykové ovládání založená na ukazatelích a podpora pera](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|Rozhraní .NET framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Určuje, zda je výchozí algoritmus hash používá pro kontrolní součty SHA256 (`false`) nebo SHA1 (`true`).<br>Společnost Microsoft doporučuje způsobeny problémy kolizí se SHA1, SHA256.|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Určuje, jestli starší verze [NullReferenceException](xref:System.NullReferenceException) dojde místo výjimku, přesněji řečeno určuje příčina výjimky (například [DirectoryNotFoundException –](xref:System.IO.DirectoryNotFoundException) nebo [ FileNotFoundException](xref:System.IO.FileNotFoundException). Je určena pro použití kódem, který závisí na zpracování [NullReferenceException](xref:System.NullReferenceException). | Rozhraní .NET framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Ovládací prvky, zda kontrolní součet hash XOML souborů v projektu pracovního postupu sestavení použít algoritmus MD5 (`true`), nebo jestli použít jako výchozí hodnotou v rozhraní .NET Framework 4.8 algoritmus SHA256.<br>Způsobeny problémy kolizí se MD5 společnost Microsoft doporučuje SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Určuje, zda kontrolní součet hash službou SqlTrackingService používá algoritmus MD5 (`true`) uložená v mezipaměti řetězců, nebo zda použije jako výchozí hodnotou v rozhraní .NET Framework 4.8 algoritmus SHA256.<br>Způsobeny problémy kolizí se MD5 společnost Microsoft doporučuje SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Určuje, zda kontrolní součet hash modulem Runtime pracovního postupu používá algoritmus MD5 (`true`) pro definice pracovního postupu v mezipaměti, nebo zda použije jako výchozí hodnotou v rozhraní .NET Framework 4.8 algoritmus SHA256.<br>Způsobeny problémy kolizí se MD5 společnost Microsoft doporučuje SHA256.|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Ovládací prvky, zda funkce usnadnění je k dispozici od verze rozhraní .NET Framework 4.7.1 jsou zapnutá nebo vypnutá. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Určuje, zda funkce usnadnění v rozhraní .NET Framework 4.7.2 k dispozici jsou povolené ovládacích prvků (`false`) nebo je zakázaný (`true`). Pokud `true`, `Switch.UseLegacyAccessibilityFeatures` musí také být `true` povolit funkce usnadnění v rozhraní .NET Framework 4.7.1.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Určuje, zda funkce pro usnadnění přístupu zavedena v rozhraní .NET Framework 4.8 jsou povolené ovládacích prvků (`false`) nebo je zakázaný (`true`). Pokud `true`, `Switch.UseLegacyAccessibilityFeatures` a `Switch.UseLegacyAccessibilityFeatures.2` musí také být `true`.|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Ovládací prvky, zda popisy tlačítek se zobrazí, když uživatel najede myší do myší na ovládací prvek WPF (`true`), nebo zda jsou zobrazeny na fokus klávesnice a pomocí klávesové zkratky (`false`, výchozí chování). Pro aplikace běžící na rozhraní .NET Framework 4.8 ale bude cílit předchozích verzích rozhraní .NET Framework, povolíte i klávesnice fokus a místní klíč podpora vyžaduje, aby `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`, a `Switch.UseLegacyAccessibilityFeatures.3` všechny být nastaveny na `false`.|.NET Framework 4.8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Určuje, zda jsou ignorovány prázdná pořadí klíčů v složených klíčů pomocí ověření schématu XSD. Další informace najdete v tématu [omezení rizik: Ověření schématu XML](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Nepřidávat `AppContextSwitchOverrides` prvku do konfiguračního souboru aplikace, můžete také nastavit přepínače programově zavoláním `static` (v jazyce C#) nebo `Shared` (v jazyce Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.  
  
 Vývojáři knihoven můžete také definovat vlastní přepínače pro povolení volajícím chcete vyjádřit výslovný nesouhlas změněné funkce zavedeny v pozdějších verzích jejich knihoven. Další informace najdete v tématu <xref:System.AppContext> třídy.  
  
## <a name="switches-in-aspnet-applications"></a>Přepínače v aplikacích ASP.NET

Můžete nakonfigurovat pomocí nastavení kompatibility tak, že přidáte aplikace ASP.NET [ \<Přidat >](../../../configure-apps/file-schema/appsettings/add-element-for-appsettings.md) elementu [ \<appSettings >](../../../configure-apps/file-schema/appsettings/index.md) část souboru web.config. 

V následujícím příkladu `<add>` prvek a přidat dvě nastavení `<appSettings>` část souboru web.config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Příklad

 V následujícím příkladu `AppContextSwitchOverrides` elementu k definování přepínače kompatibility jednu aplikaci, `Switch.System.Globalization.NoAsyncCurrentCulture`, jazykovou verzi, který brání z toku napříč vlákny v volání asynchronní metody.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 V následujícím příkladu `AppContextSwitchOverrides` element definovat dvě přepínače kompatibility aplikací, `Switch.System.Globalization.NoAsyncCurrentCulture` a `Switch.System.IO.BlockLongPaths`. Všimněte si, že odděluje středníky dvě dvojice název/hodnota.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AppContext?displayProperty=nameWithType>
- [\<modul runtime > – Element](runtime-element.md)
- [\<Konfigurace > – Element](../configuration-element.md)
