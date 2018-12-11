---
title: Struktury – C# Průvodce programováním
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 3f19d0485939e1923c479c1c9fdeb06572a11e14
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240382"
---
# <a name="structs-c-programming-guide"></a>Struktury (Průvodce programováním v C#)

Struktury jsou definované pomocí [struktura](../../language-reference/keywords/struct.md) – klíčové slovo, například:  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
Struktury sdílet většina podle stejné syntaxe jako třídy. Název struktury musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md). Struktury jsou omezeny více než třídy následujícími způsoby:  
  
- V deklaraci struktury pole nelze inicializovat, jestliže nejsou deklarovány jako const nebo statické.  
- Struktury nelze deklarovat výchozí konstruktor (konstruktor bez parametrů) nebo finalizační metodu.  
- Struktury se zkopírují na přiřazení. Když je struktura přiřazena nové proměnné, se data kopírují a jakékoli změny nová kopie nezmění data pro původní kopírování. To je důležité pamatovat při práci s kolekcemi hodnoty typy, jako `Dictionary<string, myStruct>`.  
- Struktury jsou typy hodnot, na rozdíl od tříd, které jsou odkazové typy.  
- Na rozdíl od tříd, struktur dá vytvořit instance bez použití `new` operátor.  
- Struktury můžete deklarovat konstruktory, které mají parametry. 
- Struktura nemůže dědit z jiné třídy nebo struktury a nemůže být základní třídy. Všechny struktury dědí přímo z <xref:System.ValueType>, který dědí z <xref:System.Object>.  
- Struktury můžou implementovat rozhraní.  
- Struktura může sloužit jako typ připouštějící hodnotu Null a je možné přiřadit hodnotu null.  
  
## <a name="related-sections"></a>Související oddíly  

Další informace:  
  
- [Použití struktur](using-structs.md)
- [Konstruktory](constructors.md)
- [Typy s povolenou hodnotou Null](../nullable-types/index.md)
- [Postupy: Zjištění rozdílu mezi předáním struktury a předáním odkazu na metodu třídu](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [Postupy: Implementace uživatelem definovaných převodů mezi strukturami](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](index.md)
- [Třídy](classes.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
