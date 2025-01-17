---
title: Vytváření služeb WCF pro ASP.NET AJAX
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 64be5c8ec0d3ee105e026794912a9820bd7892d0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045967"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Vytváření služeb WCF pro ASP.NET AJAX

Microsoft ASP.NET AJAX vám umožní rychle vytvořit webové stránky, které obsahují bohatou činnost uživatelů s reagujícími a známými prvky uživatelského rozhraní. ASP.NET AJAX poskytuje knihovny skriptu klienta, které zahrnují technologie ECMAScript (JavaScript) a Dynamic HTML (DHTML) pro různé prohlížeče a integrují je s vývojovou platformou serveru ASP.NET 2,0. Pomocí ASP.NET AJAX můžete zlepšit uživatelské prostředí a efektivitu webových aplikací.

ASP.NET AJAX sestávají z knihoven klientských skriptů a součástí serveru, které jsou integrované pro zajištění robustního vývojového prostředí. Přístup ke službě ze stránky ASP.NET: Jakmile se adresa URL služby přidá do ovládacího prvku Správce skriptů ASP.NET na stránce, mohou být operace služby vyvolány pomocí kódu jazyka JavaScript, který vypadá stejně jako běžné volání funkce JavaScriptu. Přečtěte si téma [ASP.NET AJAX](https://go.microsoft.com/fwlink/?LinkId=186475) o používání webových služeb v rámci AJAX Frameworku.

Většina služby Windows Communication Foundation (WCF) může být vystavená jako služba kompatibilní s ASP.NET AJAX přidáním příslušného koncového bodu ASP.NET AJAX.

Pokud používáte aplikaci Visual Studio, můžete použít předem vytvořenou šablonu pro služby WCF s podporou jazyka AJAX, která je k dispozici v dialogovém okně **Přidat novou položku** při práci s ASP.NET weby nebo webovými aplikacemi.

Pokud nepoužíváte šablony sady Visual Studio, existují dva způsoby, jak vytvořit koncový bod ASP.NET AJAX:

- Vytvořte koncový bod pomocí aktivace dynamického hostitele bez použití jakékoli konfigurace. Toto je nejzákladnější přístup, pokud neznáte konfigurační systém WCF. Další informace najdete v tématu [jak: Přidejte koncový bod ASP.NET AJAX bez použití konfigurace](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).

- Přidejte koncový bod s povoleným AJAX do služby WCF pomocí konfigurace. Další informace najdete v tématu [jak: Pomocí konfigurace přidejte koncový bod](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)ASP.NET AJAX.

Webový programovací model, který je popsaný v tématu [Přehled programovacího modelu Web HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) , se může používat s ASP.NET AJAX Services. Určen

- Pomocí <xref:System.ServiceModel.Web.WebGetAttribute> atributů a <xref:System.ServiceModel.Web.WebInvokeAttribute> můžete vybrat mezi příkazy HTTP GET a http post. Pokud se používá správně, může to významně zlepšit výkon vaší aplikace. Další informace najdete v tématu [jak: Vyberte mezi požadavky HTTP POST a HTTP GET pro koncové body](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)ASP.NET AJAX.

- Pomocí <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> vlastností a <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> můžete, aby služba vracela data XML místo výchozího JavaScript Object Notation (JSON). Díky tomu ASP.NET AJAX Framework způsobí, že klient jazyka JavaScript obdrží objekt XML DOM.

  > [!WARNING]
  > Aby tato operace mohla fungovat, musí být pro tuto operaci nastaven typ obsahu na text/XML. V opačném případě klient jazyka JavaScript obdrží řetězec obsahující XML namísto objektu XML DOM.

    Níže je uveden příklad operace, která vrací data XML s příslušným typem obsahu.

  ```csharp
  [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]
  public XElement GetData()
  {
      XElement x;
      //Get some data here...

      WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";
      return x;
  }
  ```

- Pokud je požadováno kompatibility s <xref:System.ServiceModel.Web.WebGetAttribute> ASP.NET <xref:System.ServiceModel.Web.WebInvokeAttribute> AJAX, nelze změnit žádné další vlastnosti na atributu a. Další aspekty webového programovacího modelu lze použít, pokud nejsou narušeny konvence volání ASP.NET AJAX.

 Pokročilejší scénáře vyžadují několik dalších podrobností o podpoře AJAX v technologii WCF:

- Pro pochopení, jak jsou přenášena data mezi klientem stránky AJAX a službou WCF pomocí JavaScriptu a podrobnosti o tom, jak .NET Framework typy mapují na typy JavaScriptu, najdete v tématu [Podpora JSON a dalších formátů přenos dat](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).

- Chcete-li využít výhod funkcí ASP.NET, například ověřování na základě adresy URL a přístup k informacím o relaci ASP.NET, můžete povolit režim kompatibility ASP.NET prostřednictvím konfigurace.

Koncové body AJAX v technologii WCF mohou být i bez rozhraní ASP.NET AJAX. K tomu je potřeba pochopit architekturu podpory podpory AJAX ve službě WCF. Diskuzi o této architektuře najdete v tématu [model objektu programování webového HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Ukázku kódu, který demonstruje tento přístup, najdete v tématu [Služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).

## <a name="see-also"></a>Viz také:

- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfigurace](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)
- [Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
- [Postupy: Výběr mezi požadavky HTTP POST a HTTP GET pro koncové body ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
