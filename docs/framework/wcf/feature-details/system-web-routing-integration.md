---
title: System.Web.Routing Integration
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 3d5c3d7586189e0939fd52bc2b5feac51ae00613
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933884"
---
# <a name="systemwebrouting-integration"></a>System.Web.Routing Integration
Při hostování služby Windows Communication Foundation (WCF) v Internetové informační služby (IIS) umístíte souborů .svc ve virtuálním adresáři. Tento soubor SVC určuje vytváření hostitele služby používat stejně jako třídy, která implementuje služby. Při zasílání požadavků na službu zadáte souboru SVC v identifikátoru URI, například: `http://contoso.com/EmployeeServce.svc`. Tento typ identifikátoru URI pro programátory, kteří vytvářejí služby REST není ideální. Identifikátory URI pro služby REST zadejte konkrétní prostředek a obvykle nemají žádná rozšíření. <xref:System.Web.Routing> Funkci integrace umožňuje, můžete použít k hostování služby WCF REST, která bude reagovat na identifikátory URI bez přípony. Další informace o směrování najdete v tématu [směrování ASP.NET](https://go.microsoft.com/fwlink/?LinkId=184660).  
  
## <a name="using-systemwebrouting-integration"></a>Pomocí integrace System.Web.Routing  
 Použít <xref:System.Web.Routing> funkci integrace, je použít <xref:System.ServiceModel.Activation.ServiceRoute> třídy k vytvoření jednoho nebo více tras a přidat je do <xref:System.Web.Routing.RouteTable> v souboru Global.asax. Tyto trasy zadejte relativní identifikátory URI, které služby jsou reaguje na. Následující příklad ukazuje, jak to provést.  
  
```  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));   
   }  
</script>  
```  
  
 Ten přesměruje všechny požadavky s relativní identifikátor URI, který začíná s zákazníkům `Service` služby.  
  
 V souboru Web.config musíte přidat `System.Web.Routing.UrlRoutingModule` modul, nastavte `runAllManagedModulesForAllRequests` atribut `true`a přidejte `UrlRoutingHandler` obslužná rutina `<system.webServer>` elementu, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 Tento kód načte modul a obslužná rutina vyžaduje pro směrování. Další informace najdete v tématu [směrování](../../../../docs/framework/wcf/feature-details/routing.md). Musíte taky nastavit `aspNetCompatibilityEnabled` atribut `true` v `<serviceHostingEnvironment>` elementu, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 Třídy, která implementuje službu musíte povolit požadavky kompatibility ASP.NET, jak je znázorněno v následujícím příkladu.  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Viz také:

- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [ASP.NET Routing](https://go.microsoft.com/fwlink/?LinkId=184660)
