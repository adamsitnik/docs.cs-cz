---
title: 'Postupy: Definování konstant v jazyce C#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: ba5bc3d03dcaf5c8be94936a453a439670e8dc1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924478"
---
# <a name="how-to-define-constants-in-c"></a>Postupy: Definování konstant v jazyce C\#
Konstanty jsou pole, jejichž hodnoty jsou nastaveny v době kompilace a nelze je nikdy změnit. Použijte konstanty k poskytnutí smysluplných názvů namísto číselných literálů ("Magic Numbers") pro speciální hodnoty.  
  
> [!NOTE]
> V C# direktivě preprocesoru [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) nelze použít k definování konstant způsobem, který se obvykle používá v C a C++.  
  
 Pro definování konstantních hodnot integrálních typů`int`( `byte`, a tak dále) použijte Výčtový typ. Další informace naleznete v tématu [Enum](../../language-reference/keywords/enum.md).  
  
 Chcete-li definovat Neceločíselné konstanty, jedním z přístupů je seskupit do jedné statické třídy `Constants`s názvem. To bude vyžadovat, aby všechny odkazy na konstanty byly uvozeny názvem třídy, jak je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 Použití kvalifikátoru názvu třídy pomáhá zajistit, aby vy a ostatní uživatelé používali konstantu, což znamená, že je konstantní a nelze ji upravit.  
  
## <a name="see-also"></a>Viz také:

- [Třídy a struktury](./index.md)
