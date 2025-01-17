---
title: Jak gRPC přistupuje k RPC – gRPC pro vývojáře WCF
description: Porovnání klíčových funkcí WCF a gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 3da28968f8c8bd6c4fdba7432ffc8458d8340457
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846691"
---
# <a name="how-grpc-approaches-rpc"></a>Přístup gRPC k RPC

Windows Communication Foundation (WCF) a gRPC jsou implementace vzoru *vzdáleného volání procedur* (RPC), jehož cílem je volat služby běžící na jiném počítači nebo v jiném procesu bez problémů pracovat, jako kdyby byly jen volání metod v klientské aplikaci. I když jsou cíle WCF a gRPC stejné, podrobnosti implementace se poměrně liší.

Následující tabulka obsahuje informace o tom, jak se klíčové funkce WCF vztahují k gRPC a kde najdete podrobnější vysvětlení ve zbývající části knihy.

| Funkce | WCF | gRPC |
| -------- | --- | ---- |
| Cíle | Oddělení podnikového kódu od implementace sítě | Oddělení obchodních kódů od definice rozhraní a implementace sítě |
| Definování služeb a zpráv (kapitola 3-4)  | Kontrakt služby, kontrakt operace a data kontraktu | K deklarování služeb a zpráv používá soubor. |
| Jazyk (kapitola 3-5) | Smlouvy napsané C# nebo Visual Basic | Jazyk vyrovnávací paměti protokolu |
| Formát vedení (kapitola 3) | Konfigurovatelné, včetně SOAP/XML, prostého formátu XML, JSON, .NET binary a tak dále. | Binární formát vyrovnávací paměti protokolu (i když je možné použít jiné formáty).
| Interoperabilita (kapitola 4) | Při použití protokolu SOAP přes protokol HTTP | Oficiální podpora: .NET, Java, Python, JavaScript, C/C++, přejít, Rust, Ruby, SWIFT, DART, php. Neoficiální podpora jiných jazyků od komunity. |
| Sítě (kapitola 4) | Nakonfigurováno za běhu. Přepínejte mezi NetTCP, HTTP, MSMQ a tak dále. | HTTP/2, aktuálně přes protokol TCP, s ASP.NET Core gRPC. |
| Přístup (kapitola 4) | Generování/Deserialization serializace a kódu sítě v základních třídách za běhu | Generování serializace/Deserialization a kódu sítě v základních třídách během sestavení |
| Zabezpečení (kapitola 6) | Ověřování, WS-Security, šifrování zpráv | Přihlašovací údaje, ASP.NET Core zabezpečení, sítě TLS |

>[!div class="step-by-step"]
>[Předchozí](grpc-overview.md)
>[Další](interface-definition-language.md)
