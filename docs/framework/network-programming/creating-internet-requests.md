---
title: Vytváření internetových žádostí
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 07c15614f22409f427c6f75cd4ddb8cfa218beba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706946"
---
# <a name="creating-internet-requests"></a>Vytváření internetových žádostí
Vytvoření aplikace <xref:System.Net.WebRequest> instance prostřednictvím <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody. Toto je statická metoda, která vytvoří třídu odvozenou z **WebRequest** podle do něho předaný schéma identifikátoru URI.  
  
## <a name="web-file-and-ftp-requests"></a>Webový server, souboru a požadavky protokolu FTP  
 Rozhraní .NET Framework poskytuje <xref:System.Net.HttpWebRequest> třídu, která je odvozena od **WebRequest**, pro zpracování požadavků HTTP a HTTPS. Ve většině případů **WebRequest** třída poskytuje všechny vlastnosti, je třeba provést požadavek, ale v případě potřeby můžete přetypovat **WebRequest** objekty vytvořené **WebRequest.Create**  metodu **HttpWebRequest** typ, který má přístup k vlastnostem specifickým pro HTTP žádosti. Podobně **HttpWebResponse** objekt zpracovává odpovědi z požadavků HTTP a HTTPS. Pro přístup k vlastnostem specifickým pro HTTP **HttpWebResponse** objektu, je třeba přetypovat **WebResponse** objektů **HttpWebResponse** typu.  
  
 Také poskytuje rozhraní .NET Framework <xref:System.Net.FileWebRequest> a <xref:System.Net.FileWebResponse> třídy, které zpracovávají požadavky na prostředky, které používají "file:" Schéma identifikátoru URI. Podobně <xref:System.Net.FtpWebRequest> a <xref:System.Net.FtpWebResponse> třídy jsou k dispozici pro zpracování požadavků pro prostředky, které používají "ftp:" schéma. Pokud je váš požadavek pro prostředek, který používá některou z těchto režimů, můžete použít **WebRequest.Create** metodu k získání objektu, pomocí kterého se má podat žádost.  
  
 Pro zpracování požadavků, které používají jiné protokoly na úrovni aplikace, budete muset implementovat konkrétní třídy odvozené od **WebRequest** a **WebResponse**. Další informace najdete v tématu [programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Žádost o Data pomocí třídy WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
- [Žádosti o data](../../../docs/framework/network-programming/requesting-data.md)
