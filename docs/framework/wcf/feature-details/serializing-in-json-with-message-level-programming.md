---
title: Serializace ve formátu Json s programováním na úrovni zpráv
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 7576594f8fa694ce2d34cf38c88d2e28a00f5295
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991134"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serializace ve formátu Json s programováním na úrovni zpráv
WCF podporuje serializaci dat ve formátu JSON. Toto téma popisuje, jak dát službě WCF pokyn k serializaci vašich <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>typů pomocí.  
  
## <a name="typed-message-programming"></a>Programování typované zprávy  
 Používá se, <xref:System.ServiceModel.Web.WebGetAttribute> když se použije nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> na operaci služby. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Oba tyto atributy umožňují zadat `RequestFormat` a. `ResponseFormat` Pro použití formátu JSON pro žádosti a odpovědi. nastavte obě z obou na `WebMessageFormat.Json`.  Chcete-li použít JSON, je nutné použít <xref:System.ServiceModel.WebHttpBinding>, který automaticky <xref:System.ServiceModel.Description.WebHttpBehavior>nakonfiguruje. Další informace o serializaci WCF naleznete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). Další informace o JSON a WCF najdete v tématu [Service Station – Úvod k RESTful službám pomocí WCF](https://msdn.microsoft.com/magazine/dd315413.aspx).  
  
> [!IMPORTANT]
> Použití formátu JSON vyžaduje použití <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior> , které nepodporují komunikaci SOAP. Služby, které komunikují <xref:System.ServiceModel.WebHttpBinding> s nástrojem, nepodporují vystavování metadat služby, takže nebudete moct k vygenerování proxy na straně klienta používat funkce Přidat odkaz na službu sady Visual Studio ani nástroj příkazového řádku Svcutil. Další informace o tom, jak programově volat služby, které <xref:System.ServiceModel.WebHttpBinding>používají, najdete v tématu [jak spotřebovávat služby REST pomocí WCF](https://blogs.msdn.microsoft.com/pedram/2008/04/21/how-to-consume-rest-services-with-wcf/).  
  
## <a name="untyped-message-programming"></a>Programování netypové zprávy  
 Při práci přímo s netypovými objekty zpráv je nutné explicitně nastavit vlastnosti v netypové zprávě pro její serializaci jako JSON. Následující fragment kódu ukazuje, jak to provést.  
  
```csharp
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Viz také:

- [Integrace jazyka AJAX a podpora JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [Samostatná serializace JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [Serializace JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
