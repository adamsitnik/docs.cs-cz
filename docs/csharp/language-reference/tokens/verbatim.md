---
title: '@ – C# Odkaz'
ms.custom: seodec18
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9575f408da351ac3715e1969d601c0cc73da286
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244164"
---
# <a name="-c-reference"></a>@ (Referenční dokumentace jazyka C#)

`@` Speciální znak slouží jako doslovný identifikátor. Je možné následujícími způsoby:

1. Povolit klíčová slova jazyka C# má být použit jako identifikátory. `@` Znak předpon prvek kódu, který kompilátor, je interpretováno jako identifikátor místo klíčového slova jazyka C#. V následujícím příkladu `@` znak definovat identifikátor s názvem `for` používající v `for` smyčky.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Označuje, že řetězcového literálu verbatim interpretovat. `@` Definuje znak v tomto případě *doslovný řetězec literálu*. Jednoduchá řídící sekvence (například `"\\"` pro zpětné lomítko), hexadecimální řídicí sekvence (, jako `"\x0041"` pro velká A) a řídicí sekvence Unicode (například `"\u0041"` pro velká A) jsou interpretovány literálně. Nabídky řídicí sekvence (`""`) nebyl interpretován doslovně; vytvoří jednoduchou uvozovku. Kromě toho v případě verbatim [interpolovaný řetězec](interpolated.md) složenou závorku řídicí sekvence (`{{` a `}}`) nejsou interpretován doslovně; vytvářejí jednu složenou závorku znaků. Následující příklad definuje dvě cesty k souborům identické, pomocí regulárních řetězcový literál a druhý s použitím doslovný řetězec literálu. Toto je jeden z více běžná použití služby verbatim řetězcové literály.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Následující příklad ukazuje účinek definování regulárního řetězcový literál a doslovný řetězec literálu, které obsahují stejné znakové sekvence.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Umožňuje kompilátoru k rozlišení mezi atributy v případě konfliktu názvů. Atribut je třída, která je odvozena z <xref:System.Attribute>. Obvykle obsahuje příponu názvu typu **atribut**, i když kompilátor nevynucuje Tato konvence. Atribut může poté odkazovat v kódu, buď pomocí jeho úplný název typu (například `[InfoAttribute]` nebo jeho zkrácený název (například `[Info]`). Ale ke konfliktu názvů v případě dvou zkrátila názvy typů atributů jsou identické, a zahrnuje jeden název typu **atribut** příponu, ale druhá ne. Například následující kód nejde zkompilovat, protože kompilátor nemůže určit, jestli `Info` nebo `InfoAttribute` atribut aplikován `Example` třídy. Zobrazit [CS1614](../compiler-messages/cs1614.md) Další informace.

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Speciální znaky v jazyce C#](../../../csharp/language-reference/tokens/index.md)
