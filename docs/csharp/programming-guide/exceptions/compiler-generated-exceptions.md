---
title: Výjimky - generovaný kompilátorem C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 15a42b8fb23aed024fede726d0b5fb731d8272f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686358"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Výjimky generované kompilátorem (Průvodce programováním v C#)
Některé výjimky jsou vyvolány automaticky modulem CLR rozhraní .NET Framework common language runtime (CLR), když dojde k selhání základních operací. Tyto výjimky a jejich chybové podmínky jsou uvedeny v následující tabulce.  
  
|Výjimka|Popis|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Základní třída pro výjimky, ke kterým dochází při aritmetické operace, jako například <xref:System.DivideByZeroException> a <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Vyvolána, když pole Nejde uložit daného elementu, protože skutečný typ elementu, který není kompatibilní s skutečný typ pole.|  
|<xref:System.DivideByZeroException>|Vyvolána, když je proveden pokus o se má dělit celočíselnou hodnotu nulou.|  
|<xref:System.IndexOutOfRangeException>|Vyvolána, když je proveden pokus o indexu pole, pokud je index menší než nula nebo mimo hranice pole.|  
|<xref:System.InvalidCastException>|Vyvolána, když selže explicitní převod z typu základní rozhraní nebo odvozeného typu za běhu.|  
|<xref:System.NullReferenceException>|Vyvolána, jestliže se pokusíte odkazovat na objekt, jehož hodnota je [null](../../../csharp/language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Při pokusu o přidělení paměti pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md) operátor selže. To znamená, že byly vyčerpány paměť dostupnou pro modul common language runtime.|  
|<xref:System.OverflowException>|Vyvolána, když v aritmetické operace `checked` kontextu přetečení.|  
|<xref:System.StackOverflowException>|Vyvolána, když se vyčerpá zásobníku spouštění tak, že příliš mnoho volání metody čekající; obvykle označuje velmi podrobné nebo nekonečné rekurzi.|  
|<xref:System.TypeInitializationException>|Vyvolána, když statický konstruktor vyvolá výjimku a žádné kompatibilní `catch` existuje klauzule má zachytit.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)
- [Zpracování výjimek](../../../csharp/programming-guide/exceptions/exception-handling.md)
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)
- [try-finally](../../../csharp/language-reference/keywords/try-finally.md)
- [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
