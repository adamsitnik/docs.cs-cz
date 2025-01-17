---
title: <add> z <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: dee2cd482efc841b7320ed2114a05000255466f3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850518"
---
# <a name="add-of-baseaddressprefixfilter"></a>\<add> of \<baseAddressPrefixFilter>
Představuje prvek konfigurace, který určuje předávací filtr, který poskytuje mechanismus pro výběr příslušných vazeb Internetová informační služba (IIS) při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<baseAddressPrefixFilters >** ](baseaddressprefixfilters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|prefix|Identifikátor URI, který se používá k vyhledání části základní adresy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|Kolekce elementů konfigurace, které určují předávací filtry, které poskytují mechanismus pro výběr příslušných vazeb služby IIS při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.|  
  
## <a name="remarks"></a>Poznámky  
 Filtr předpon poskytuje způsob, jak sdíleným poskytovatelům hostingu určit, které identifikátory URI bude služba používat. Umožňuje sdíleným hostitelům hostovat více aplikací s různými základními adresami pro stejné schéma ve stejné lokalitě.  
  
 Webové stránky služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře. Aplikace v lokalitě je k dispozici prostřednictvím jedné nebo více vazeb služby IIS. Vazby služby IIS poskytují dvě informace: vazby protokolu a informace o vazbě. Protokol vazby (například HTTP) definuje schéma, přes které probíhá komunikace, a informace o vazbě (například IP adresa, port, hostheader) obsahuje data, která se používají pro přístup k webu.  
  
 Služba IIS podporuje zadání více vazeb služby IIS pro každou lokalitu, což má za následek více základních adres pro každé schéma. Vzhledem k tomu, že služba WCF hostovaná v rámci lokality umožňuje vytvořit vazbu pouze na jednu základní adresu pro každé schéma, můžete pomocí funkce filtru předpon vybrat požadovanou základní adresu hostované služby. Příchozí základní adresy, které poskytuje služba IIS, se filtrují na základě volitelného filtru seznamu předpon.  
  
 Například váš web může obsahovat následující základní adresy.  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Následující konfigurační soubor můžete použít k určení filtru předpony na úrovni domény AppDomain.  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 V tomto příkladu `http://test2.fabrikam.com:9000` jsou `net.tcp://test1.fabrikam.com:8000` jedinými základními adresami pro jejich příslušné systémy, které mohou být předány.  
  
 Ve výchozím nastavení, pokud není zadána předpona, jsou předány všechny adresy. Zadání předpony umožňuje předávat odpovídající základní adresu pro toto schéma.  
  
> [!NOTE]
> Filtr nepodporuje žádné zástupné znaky. Kromě toho adres BaseAddresses poskytované službou IIS může mít adresy svázané s jinými schématy, která nejsou přítomna `baseAddressPrefixFilters` v seznamu. Tyto adresy nejsou vyfiltrovány.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hostování](../../../wcf/feature-details/hosting.md)
