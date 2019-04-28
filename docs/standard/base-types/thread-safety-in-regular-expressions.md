---
title: Bezpečnost vlákna v regulárních výrazech
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0bcab0757bc48f6a8216dd5878f0289e49a275
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766750"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="251c6-102">Bezpečnost vlákna v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="251c6-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="251c6-103"><xref:System.Text.RegularExpressions.Regex> Třídu je vlákno, byla v bezpečí a neměnné (jen pro čtení).</span><span class="sxs-lookup"><span data-stu-id="251c6-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="251c6-104">To znamená **regulární výraz** objektů se dají vytvářet v libovolném vlákně a sdílet mezi vlákny; odpovídající metody lze volat z libovolného vlákna a nikdy měnit žádné globální stav.</span><span class="sxs-lookup"><span data-stu-id="251c6-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="251c6-105">Nicméně objekty výsledků (**shoda** a **MatchCollection**) vrácený **regulární výraz** byste neměli používat v jednom vlákně.</span><span class="sxs-lookup"><span data-stu-id="251c6-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="251c6-106">I když mnohé z těchto objektů jsou logicky neměnné, jejich implementace mohly zpožďovat výpočtu některé výsledky pro zvýšení výkonu a v důsledku toho volající musí serializovat přístup k nim.</span><span class="sxs-lookup"><span data-stu-id="251c6-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="251c6-107">Pokud je potřeba sdílet **regulární výraz** výsledek objektů z více vláken, tyto objekty lze převést na instance bezpečným pro vlákno voláním jejich synchronizované metody.</span><span class="sxs-lookup"><span data-stu-id="251c6-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="251c6-108">S výjimkou enumerátory všechny třídy regulárních výrazů jsou bezpečné pro vlákna nebo mohou být převedeny na bezpečné pro vlákna objekty synchronizované metody.</span><span class="sxs-lookup"><span data-stu-id="251c6-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="251c6-109">Enumerátory jsou jedinou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="251c6-109">Enumerators are the only exception.</span></span> <span data-ttu-id="251c6-110">Aplikace musí serializovat volání kolekce enumerátory.</span><span class="sxs-lookup"><span data-stu-id="251c6-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="251c6-111">Pokud kolekce jsou současně uvedené na více než jedno vlákno, bude třeba synchronizovat enumerátor metody na kořenový objekt kolekce procházené pomocí čítače výčtu je pravidlo.</span><span class="sxs-lookup"><span data-stu-id="251c6-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251c6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="251c6-112">See also</span></span>

- [<span data-ttu-id="251c6-113">Regulárních výrazů .NET</span><span class="sxs-lookup"><span data-stu-id="251c6-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
