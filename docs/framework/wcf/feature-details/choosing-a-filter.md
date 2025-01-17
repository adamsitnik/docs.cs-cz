---
title: Výběr filtru
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 908e905b4196409b00abccccae03436640cbe986
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045981"
---
# <a name="choosing-a-filter"></a>Výběr filtru
Při konfiguraci směrovací služby je důležité vybrat správné filtry zpráv a nakonfigurovat je tak, aby vám umožnily přesně odpovídat na zprávy, které obdržíte. Pokud jsou filtry, které vyberete, příliš široké v jejich shodách nebo jsou nesprávně nakonfigurované, zprávy se nesprávně směrují. Pokud jsou filtry příliš omezující, nemusí být pro některé z vašich zpráv k dispozici žádné platné trasy.

## <a name="filter-types"></a>Typy filtrů

Když vyberete filtry, které služba Směrování používá, je důležité pochopit, jak každý filtr funguje, a jaké informace jsou k dispozici jako součást příchozích zpráv. Pokud jsou například všechny zprávy přijímány přes stejný koncový bod, nejsou filtry adresa a koncový bod užitečné, protože všechny zprávy odpovídají těmto filtrům.

### <a name="action"></a>Akce

Filtr akcí kontroluje <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> vlastnost. Pokud se obsah záhlaví akce ve zprávě shoduje s hodnotou dat filtru zadanou v konfiguraci filtru, pak tento filtr vrátí `true`. Následující příklad definuje `FilterElement` , který používá filtr akcí, aby odpovídal zprávám s hlavičkou akce, která obsahuje `http://namespace/contract/operation/`hodnotu.

```xml
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />
```

```csharp
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
```

Tento filtr by měl být použit při směrování zpráv, které obsahují jedinečnou hlavičku akce.

### <a name="endpointaddress"></a>Parametry

Filtr EndpointAddress zkontroluje adresu EndpointAddress, na které byla zpráva přijata. Pokud adresa, kterou zpráva dorazí, přesně odpovídá adrese filtru zadané v konfiguraci filtru, pak tento filtr vrátí `true`. Následující příklad definuje `FilterElement` , který používá filtr adres, aby odpovídal všem zprávám, které jsou adresovány "http://\<hostname >/vdir/s.svc/b".

```xml
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> Je důležité si uvědomit, že část s názvem hostitele v adrese se může lišit v závislosti na tom, zda klient používá plně kvalifikovaný název domény, název rozhraní NetBIOS, IP adresu nebo jiný název. Vzhledem k tomu, že rozdílné hodnoty mohou odkazovat na stejného hostitele, výchozí chování pro toto porovnání není použití části názvu hostitele v této adrese při provádění shody.
>
> Toto chování je možné upravit, aby při programové konfiguraci směrovací služby bylo porovnání vyhodnoceno jako název hostitele.

Tento filtr by měl být použit při adresování příchozích zpráv na jedinečnou adresu.

### <a name="endpointaddressprefix"></a>EndpointAddressPrefix

Filtr EndpointAddressPrefix se podobá filtru EndpointAddress. Filtr EndpointAddressPrefix zkontroluje adresu EndpointAddress, na které byla zpráva přijata. Filtr EndpointAddressPrefix ale funguje jako zástupný znak odpovídajícími adresami, které začínají hodnotou zadanou v konfiguraci filtru. Následující příklad definuje `FilterElement` , který používá filtr EndpointAddressPrefix k vyhledání všech zpráv, které jsou `http://<hostname>/vdir*`adresovány.

```xml
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />
```

```csharp
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> Je důležité si uvědomit, že část s názvem hostitele v adrese se může lišit v závislosti na tom, zda klient používá plně kvalifikovaný název domény, název rozhraní NetBIOS, IP adresu nebo jiný název. Vzhledem k tomu, že rozdílné hodnoty mohou odkazovat na stejného hostitele, výchozí chování pro toto porovnání není použití části názvu hostitele v této adrese při provádění shody.

Tento filtr by měl být použit při směrování příchozích zpráv, které sdílejí společnou předponu adresy.

### <a name="and"></a>AND

Filtr and přímo nefiltruje na hodnotu v rámci zprávy, ale umožňuje zkombinovat dva další filtry a vytvořit `AND` tak podmínku, že oba filtry musí odpovídat zprávě předtím, než se filtr a vyhodnotí. `true` To vám umožňuje vytvářet komplexní filtry, které se shodují jenom v případě, že se všechny dílčí filtry shodují. Následující příklad definuje filtr adresy a filtr akcí a pak definuje filtr a, který vyhodnocuje zprávu proti filtrům adresa a akce. Pokud adresa i filtr akce souhlasí, pak vrátí `true`filtr a.

```xml
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);
```

Tento filtr by měl být použit v případě, že je nutné zkombinovat logiku z více filtrů, aby bylo možné určit, kdy má být provedeno porovnávání. Například pokud máte více cílů, které musí přijímat pouze určité kombinace akcí a zpráv pro konkrétní adresy, můžete použít filtr a ke kombinování potřebných filtrů akcí a adres.

### <a name="custom"></a>Vlastní

Při výběru vlastního typu filtru je nutné zadat hodnotu customType, která obsahuje typ sestavení, které obsahuje implementaci **MessageFilter** , která se má použít pro tento filtr. Kromě toho musí fulltextových obsahovat všechny hodnoty, které může vlastní filtr vyžadovat při vyhodnocování zpráv. Následující příklad definuje `FilterElement` , který `CustomAssembly.MyCustomMsgFilter` používá implementaci MessageFilter.

```xml
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />
```

```csharp
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");
```

Pokud potřebujete provést vlastní odpovídající logiku proti zprávě, která není pokryta filtry poskytnutými pomocí [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], je nutné vytvořit vlastní filtr, který je implementací třídy **MessageFilter** . Můžete například vytvořit vlastní filtr, který porovná pole v příchozí zprávě se seznamem známých hodnot poskytnutým filtru jako konfigurací, nebo, který určí hodnotu hash konkrétního prvku zprávy, a pak prověřuje tuto hodnotu, abyste zjistili, zda filtr měla by `true` vracet `false`nebo.

### <a name="endpointname"></a>EndpointName

Filtr koncového bodu kontroluje název koncového bodu, který zprávu přijal. Následující příklad definuje `FilterElement` , který používá filtr koncového bodu ke směrování zpráv přijatých na "SvcEndpoint".

```xml
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />
```

```csharp
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");
```

Tento filtr je užitečný, když směrovací služba zveřejňuje více než jeden pojmenovaný koncový bod služby. Můžete například vystavit dva koncové body, které služba Směrování používá pro příjem zpráv. jednu používá přednostní zákazníci, kteří vyžadují zpracování svých zpráv v reálném čase, zatímco druhý koncový bod přijímá zprávy, které nejsou citlivé na čas.

I když můžete často použít úplnou spárování adres k určení, který koncový bod přijal zprávu, je místo toho pohodlný zástupce, který je často méně náchylné k chybám, zejména při konfiguraci směrovací služby s použitím konfigurace. soubor (kde jsou požadovány názvy koncových bodů).

### <a name="matchall"></a>MatchAll

Filtr MatchAll odpovídá jakékoli přijaté zprávě. To je užitečné v případě, že musíte vždy směrovat všechny přijaté zprávy do konkrétního koncového bodu, například protokolovací služby, která ukládá kopii všech přijatých zpráv. Následující příklad definuje `FilterElement` , který používá filtr MatchAll.

```xml
<filter name="matchAll1" filterType="MatchAll" />
```

```csharp
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();
```

### <a name="xpath"></a>XPath

Filtr XPath umožňuje zadat dotaz XPath, který se používá ke kontrole konkrétního prvku v rámci zprávy. Filtrování XPath je výkonné možnosti filtrování, které vám umožní přímo zkontrolovat v rámci zprávy jakoukoli položku, která je schopná adresovat kód XML. vyžaduje ale, abyste měli konkrétní znalosti struktury zpráv, které přijímáte. Následující příklad definuje `FilterElement` , který používá filtr XPath ke kontrole zprávy pro element s názvem "element" v oboru názvů, na který odkazuje předpona oboru názvů "NS".

```xml
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />
```

```csharp
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");
```

Tento filtr je užitečný, pokud víte, že zprávy, které přijímáte, obsahují konkrétní hodnotu. Pokud například používáte dvě verze stejné služby a víte, že zprávy adresované do novější verze služby obsahují ve vlastní hlavičce jedinečnou hodnotu, můžete vytvořit filtr, který používá XPath k přechodu na tuto hlavičku a porovná hodnotu pres. k určení, zda filtr odpovídá, můžete v hlavičce k druhému uvedenému v konfiguraci filtru.

Vzhledem k tomu, že dotazy XPath často obsahují jedinečné obory názvů, které jsou často dlouhé nebo složité řetězcové hodnoty, umožňuje filtr XPath definovat jedinečné předpony pro vaše obory názvů. Další informace o tabulce oboru názvů najdete v tématu [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).

Další informace o návrhu dotazů XPath naleznete v tématu [syntax XPath](https://go.microsoft.com/fwlink/?LinkId=164592).

## <a name="see-also"></a>Viz také:

- [Filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md)
- [Postupy: Použití filtrů](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
