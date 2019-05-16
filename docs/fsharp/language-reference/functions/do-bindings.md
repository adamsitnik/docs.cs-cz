---
title: do – vazby
description: Zjistěte, jak F# "do" vazby se používá k provádění kódu bez definování funkce nebo hodnota.
ms.date: 05/16/2016
ms.openlocfilehash: 0755e36912fc4e5a645e55eb4bee5c730a56cadf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641918"
---
# <a name="do-bindings"></a>do – vazby

A `do` vazby se používá k provádění kódu bez definování funkce nebo hodnota. Také proveďte vazby může být použit ve třídách, naleznete v tématu [ `do` vazby ve třídách](../members/do-bindings-in-classes.md).

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Poznámky

Použití `do` vazby, pokud chcete spustit kód bez ohledu na jejich definici funkce nebo hodnota. Výraz v `do` vazby musí vracet `unit`. Kód v nejvyšší úrovni `do` vazby je proveden při inicializaci modulu. Klíčové slovo `do` je volitelný.

Atributy lze použít na nejvyšší úrovni `do` vazby. Například pokud program používá zprostředkovatele komunikace s objekty COM, můžete chtít použít `STAThread` atribut vašemu programu. Můžete to provést pomocí atributu na `do` vazbu, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](../index.md)
- [Funkce](index.md)
