---
title: Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: 74ef2f3f3505125f8720695e218617817fcae82d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548375"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů
Webových služeb ASP.NET s vyvinutý pro vytváření aplikací, které odesílání a příjem zpráv pomocí jednoduchý objekt přístup protokolu (SOAP) přes protokol HTTP. Lze definovat strukturu zpráv pomocí schématu XML a poskytuje nástroje k usnadnění serializace zprávy do a z objektů v rozhraní .NET Framework. Tato technologie může automaticky generovat metadata pro popis webových služeb v na webové služby WSDL (Description Language) a druhý nástroj je k dispozici pro generování klientů pro webové služby z jazyka WSDL.  
  
 WCF slouží k povolení aplikace rozhraní .NET Framework umožňuje výměnu zpráv s jinými entitami softwaru. Ve výchozím nastavení se používá protokol SOAP, ale zprávy může být v libovolném formátu a pomocí libovolného protokolu pro přenos vyjádřeným. Lze definovat strukturu zpráv pomocí schématu XML a existují různé možnosti pro serializaci zprávy do a z objektů v rozhraní .NET Framework. WCF může automaticky generovat metadata popisující aplikací vytvořených pomocí technologie v jazyce WSDL a také poskytuje nástroj pro generování klientů pro tyto aplikace z rozhraní jazyka WSDL.  
  
 Standardy, které podporuje webových služeb ASP.NET jsou dokumentovány v článku [XML webové služby vytvořené pomocí ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94872). Rozsáhlejší seznam standardů podporovaných WCF jsou uvedeny v tématu [webové služby protokoly podporované vazbami Interoperability System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## <a name="see-also"></a>Viz také:
- [Porovnání webových služeb ASP.NET s technologií WCF z hlediska vývojových požadavků](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
