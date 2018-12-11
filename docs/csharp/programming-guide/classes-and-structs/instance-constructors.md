---
title: Instance konstruktory - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 5cc7c06a763c4b274b154afc581e495a7e2aa09b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241652"
---
# <a name="instance-constructors-c-programming-guide"></a>Konstruktory instancí (Průvodce programováním v C#)
Konstruktory instancí se používají k vytváření a inicializace žádné proměnné členů instance při použití [nové](../../../csharp/language-reference/keywords/new.md) výraz, který se vytvoří objekt [třídy](../../../csharp/language-reference/keywords/class.md). Inicializace [statické](../../../csharp/language-reference/keywords/static.md) třídy nebo statické proměnné v nestatické třídy, je nutné definovat statický konstruktor. Další informace najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 Následující příklad ukazuje konstruktor instance:  
  
 [!code-csharp[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  Pro přehlednost Tato třída obsahuje veřejná pole. Použití veřejná pole není doporučený postup programování, protože umožňuje libovolné metody kdekoli v programu neomezený i neověřených přístup k objektu vnitřní fungování. Datové členy obecně by měly být privátní a by měl mít přístup jenom prostřednictvím metody třídy a vlastnosti.  
  
 Tento konstruktor instance je volána pokaždé, když se na základě objektu `CoOrds` je vytvořená třída. Jako tohoto objektu, která nepřijímá žádné argumenty, se nazývá konstruktor *výchozí konstruktor*. Často je však užitečný k zadání dalších konstruktory. Například můžeme přidat konstruktoru `CoOrds` třídu, která umožňuje zadat počáteční hodnoty pro datové členy:  
  
 [!code-csharp[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 Díky tomu `CoOrd` objekty vytvořené pomocí výchozí nebo konkrétní počáteční hodnoty tímto způsobem:  
  
 [!code-csharp[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 Pokud třída nemá konstruktor, výchozí konstruktor není automaticky vygenerován a výchozí hodnoty se používají k inicializaci pole objektů. Například [int](../../../csharp/language-reference/keywords/int.md) je inicializován na hodnotu 0. Další informace o výchozí hodnoty, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md). Proto protože `CoOrds` výchozí konstruktor třídy inicializuje všechny datové členy na hodnotu nula, je možné odebrat úplně beze změny, jak funguje třídy. V příkladu 1 dále v tomto tématu poskytuje kompletní příklad použití více konstruktorů a příklad o automaticky generovaný konstruktor je k dispozici v příkladu 2.  
  
 Konstruktory instancí lze také volat konstruktor instance základní třídy. Konstruktor třídy lze vyvolat konstruktor základní třídy pomocí inicializátoru, následujícím způsobem:  
  
 [!code-csharp[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 V tomto příkladu `Circle` třídy předá hodnoty představující radius a výšku konstruktoru poskytované `Shape` odkud `Circle` je odvozen. Úplný příklad použití `Shape` a `Circle` se zobrazí v tomto tématu jako příklad 3.  
  
## <a name="example-1"></a>Příklad 1  
 Následující příklad ukazuje třídu s dvěma třídami konstruktory, jeden bez argumentů a druhý se dvěma argumenty.  
  
 [!code-csharp[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a>Příklad 2  
 V tomto příkladu třída `Person` nemá žádné konstruktory, ve kterých případu, výchozí konstruktor je poskytována automaticky a pole jsou inicializovány na výchozích hodnotách.  
  
 [!code-csharp[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 Všimněte si, že výchozí hodnota `age` je `0` a výchozí hodnota `name` je `null`. Další informace o výchozí hodnoty, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Příklad 3  
 Následující příklad ukazuje použití inicializátoru pro základní třídu. `Circle` Třídy je odvozen od obecné třídy `Shape`a `Cylinder` je třída odvozena z `Circle` třídy. Konstruktor pro jednotlivé odvozené třídy používá inicializátor její základní třídy.  
  
 [!code-csharp[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 Další příklady vyvolání konstruktory základní třídy naleznete v tématu [virtuální](../../../csharp/language-reference/keywords/virtual.md), [přepsat](../../../csharp/language-reference/keywords/override.md), a [základní](../../../csharp/language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [static](../../../csharp/language-reference/keywords/static.md)
