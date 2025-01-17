---
title: Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 655e8807a78d542cd7fa586eca3750507891f74b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988770"
---
# <a name="caching-support-for-wcf-web-http-services"></a>Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]umožňuje použít deklarativní mechanizmus ukládání do mezipaměti, který je již k dispozici v ASP.NET ve webových službách HTTP služby WCF. To vám umožní ukládat odpovědi z operací služby HTTP webu WCF do mezipaměti. Když uživatel odešle službě požadavek HTTP GET, která je nakonfigurovaná pro ukládání do mezipaměti, ASP.NET odešle zpět odpověď uloženou v mezipaměti a metoda služby se nevolá. Až mezipaměť vyprší, při příštím odeslání HTTP GET se vaše metoda služby zavolá a odpověď se znovu uloží do mezipaměti. Další informace o ukládání do mezipaměti ASP.NET najdete v tématu [Přehled ukládání do mezipaměti ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152534) .  
  
## <a name="basic-web-http-service-caching"></a>Mezipaměť základní webové služby HTTP  
 Pokud chcete povolit ukládání webové služby HTTP do mezipaměti, musíte nejdřív povolit kompatibilitu s <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ASP.NET, a to tak <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> , <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>že použijete nastavení <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> služby na nebo.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]zavádí nový atribut s názvem <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> , který umožňuje zadat název profilu mezipaměti. Tento atribut se aplikuje na operaci služby. Následující příklad aplikuje <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> na službu pro povolení kompatibility ASP.NET a `GetCustomer` nakonfiguruje operaci pro ukládání do mezipaměti. <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Atribut určuje profil mezipaměti, který obsahuje nastavení mezipaměti, která se mají použít.  
  
```csharp
[ServiceContract] 
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
 Také je nutné zapnout režim kompatibility ASP.NET v souboru Web. config, jak je znázorněno v následujícím příkladu.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> Pokud není režim kompatibility ASP.NET zapnutý a <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> použije se výjimka, je vyvolána výjimka.  
  
 Název profilu mezipaměti určený parametrem <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifikuje profil mezipaměti, který je přidán do konfiguračního souboru Web. config. Profil mezipaměti je definován v prvku <`outputCacheSetting`>, jak je znázorněno v následujícím příkladu konfigurace.  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 Jedná se o stejný prvek konfigurace, který je k dispozici pro ASP.NET aplikace. Další informace o profilech mezipaměti ASP.NET najdete v <xref:System.Web.Configuration.OutputCacheProfile>tématu. U webových služeb HTTP jsou nejdůležitější atributy v profilu mezipaměti: `cacheDuration` a. `varyByParam` Oba tyto atributy jsou povinné. `cacheDuration`nastaví dobu, po kterou by měla být odpověď uložená v mezipaměti v sekundách. `varyByParam`umožňuje zadat parametr řetězce dotazu, který se používá k ukládání odpovědí do mezipaměti. Všechny požadavky vytvořené pomocí různých hodnot parametrů řetězce dotazu jsou ukládány do mezipaměti odděleně. Například po provedení `http://MyServer/MyHttpService/MyOperation?param=10`prvotní žádosti budou všechny následné požadavky vytvořené se stejným identifikátorem URI vracet odpověď v mezipaměti (Pokud doba trvání mezipaměti neuplynula). Odpovědi na podobný požadavek, který je stejný, ale má jinou hodnotu parametru řetězce dotazu parametru, jsou ukládány do mezipaměti odděleně. Pokud nechcete toto oddělené chování ukládání do mezipaměti, nastavte `varyByParam` na "none".  
  
## <a name="sql-cache-dependency"></a>Závislost mezipaměti SQL  
 Odpovědi na webové HTTP služby můžou být také uloženy v mezipaměti se závislostí mezipaměti SQL. Je-li služba WCF Web HTTP závislá na datech uložených v databázi SQL, může být vhodné uložit odpověď služby do mezipaměti a zrušit platnost odpovědi uložené v mezipaměti, když dojde ke změně dat v tabulce databáze SQL. Toto chování je zcela nakonfigurované v souboru Web. config. Je nutné nejprve definovat připojovací řetězec v prvku <`connectionStrings`>.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Pak je nutné povolit funkci závislosti mezipaměti SQL v rámci`caching`elementu < > v rámci`system.web`elementu < >, jak je znázorněno v následujícím příkladu konfigurace.  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 V tomto případě je povolena závislost mezipaměti SQL a je nastavena doba cyklického dotazování 1000 milisekund. Pokaždé, když uplyne doba dotazování v tabulce databáze, bude kontrolována aktualizace. Pokud se zjistí změny, obsah mezipaměti se odstraní a při příštím vyvolání operace služby se nová odpověď uloží do mezipaměti. V rámci elementu`sqlCacheDependency`< > přidejte databáze a odkazujte na připojovací řetězce v rámci elementu`databases`< >, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 Dále je nutné nakonfigurovat nastavení výstupní mezipaměti v rámci prvku <`caching`>, jak je znázorněno v následujícím příkladu.  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 V tomto případě je doba trvání mezipaměti nastavená na `varyByParam` 60 sekund, je nastavená na None (žádné) a `sqlDependency` je nastavená na seznam dvojic název databáze/tabulka oddělený středníkem. Když dojde ke `MyTable` změně dat v mezipaměti, je odebrána odpověď uložená v mezipaměti pro operaci služby a při vyvolání operace je vygenerována nová odpověď (voláním operace služby), uloženou v mezipaměti a vrácena klientovi.  
  
> [!IMPORTANT]
> Aby ASP.NET mohl získat přístup ke službě SQL Database, je nutné použít [Nástroj pro registraci nástroje ASP.NET SQL Server](https://go.microsoft.com/fwlink/?LinkId=152536). Kromě toho je nutné, aby měl příslušný uživatelský účet přístup k databázi a tabulce. Další informace najdete v tématu [přístup k SQL Server z webové aplikace](https://go.microsoft.com/fwlink/?LinkId=178988).  
  
## <a name="conditional-http-get-based-caching"></a>Podmíněné ukládání do mezipaměti založené na protokolu HTTP  
 Ve scénářích webového protokolu HTTP často využívají podmíněné HTTP GET služby k implementaci inteligentního ukládání do mezipaměti protokolu HTTP, jak je popsáno ve [specifikaci http](https://go.microsoft.com/fwlink/?LinkId=165800). Aby bylo možné tuto službu provést, musí být v odpovědi HTTP nastavena hodnota hlavičky ETag. Také musí v požadavku HTTP zaškrtnout hlavičku If-None-Match, aby bylo možné zjistit, zda některý ze zadaných značek ETag odpovídá aktuálnímu ETag.  
  
 V případě požadavků <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Get a Head přebírá hodnotu ETag a kontroluje ji v hlavičce If-None-Match žádosti. Pokud je hlavička k dispozici a existuje shoda, <xref:System.ServiceModel.Web.WebFaultException> je vyvolána a se stavovým kódem HTTP 304 (nezměněno) a hlavička ETag je přidána do odpovědi s odpovídající značkou ETag.  
  
 Jedno přetížení <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metody přijímá datum poslední změny a kontroluje je proti hlavičce Request-Modified-od hlavičky žádosti. Pokud se hlavička nachází a prostředek se od chvíle nezměnil, <xref:System.ServiceModel.Web.WebFaultException> je vyvolána se stavovým kódem HTTP 304 (nezměněno).  
  
 Pro žádosti <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> o vložení, odeslání a odstranění převezme aktuální hodnotu ETag prostředku. Pokud je aktuální hodnota ETag null, metoda zkontroluje, zda má hlavička If-None-Match hodnotu "*".  Pokud aktuální hodnota ETag není výchozí hodnotou, pak metoda zkontroluje aktuální hodnotu ETag v hlavičce If-Match žádosti. V obou případech metoda vyvolá <xref:System.ServiceModel.Web.WebFaultException> se stavovým kódem HTTP 412 (Předběžná podmínka se nezdařila), pokud očekávaná hlavička není v požadavku k dispozici, nebo její hodnota nevyhovuje podmíněné kontrole a nastavuje hlavičku etag odpovědi na aktuální značku ETag. osa.  
  
 `CheckConditional` Jak metody <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> , tak metoda zajišťují, že hodnota ETag nastavená v hlavičce Response je platný ETag podle specifikace HTTP. To zahrnuje okolí hodnoty ETag v dvojitých uvozovkách, pokud již nejsou přítomny, a správně uvozovací znaky všech vnitřních dvojitých uvozovek. Slabé porovnání ETag není podporováno.  
  
 Následující příklad ukazuje, jak použít tyto metody.  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;
        
        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Žádosti, které vyžadují autorizaci, by neměly mít své odpovědi uložené v mezipaměti, protože autorizace se neprovádí, pokud je odpověď obsluhována z mezipaměti.  Ukládání takových odpovědí do mezipaměti by vedlo k závažné chybě zabezpečení.  Obvykle požadavky vyžadující autorizaci poskytují data specifická pro uživatele, a proto ukládání do mezipaměti na straně serveru není ještě výhodné.  V takových situacích bude vhodné ukládat do mezipaměti na straně klienta nebo jednoduše ukládat do mezipaměti.
