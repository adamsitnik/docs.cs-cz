---
title: Me, My, MyBase a MyClass v jazyce Visual Basic
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: 7df146e09a1d7cd730f4cf539d6823f7ced44bd1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002529"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase a MyClass v jazyce Visual Basic
`Me`, `My`, `MyBase` a `MyClass` v Visual Basic mají podobné názvy, ale různé účely. Toto téma popisuje každou z těchto entit, aby je bylo možné odlišit.  
  
## <a name="me"></a>Mně  
 Klíčové slovo `Me` poskytuje způsob, jak odkazovat na konkrétní instanci třídy nebo struktury, ve které je kód aktuálně spuštěn. `Me` se chová jako proměnná objektu nebo proměnná struktury odkazující na aktuální instanci. Použití `Me` je zvlášť užitečné pro předávání informací o aktuálně vykonávané instanci třídy nebo struktury na proceduru v jiné třídě, struktuře nebo modulu.  
  
 Předpokládejme například, že v modulu máte následující proceduru.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Tento postup můžete zavolat a předat aktuální instanci třídy <xref:System.Windows.Forms.Form> jako argument pomocí následujícího příkazu.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Moje  
 Funkce `My` poskytuje snadný a intuitivní přístup k řadě tříd .NET Framework a umožňuje uživatelům Visual Basic interakci s počítačem, aplikací, nastavením, prostředky a tak dále.  
  
## <a name="mybase"></a>MyBase  
 Klíčové slovo `MyBase` se chová jako proměnná objektu odkazující na základní třídu aktuální instance třídy. `MyBase` se běžně používá pro přístup ke členům základních tříd, které jsou přepsány nebo vrženy v odvozené třídě. `MyBase.New` slouží k explicitnímu volání konstruktoru základní třídy z konstruktoru odvozené třídy.  
  
## <a name="myclass"></a>MyClass  
 Klíčové slovo `MyClass` se chová jako proměnná objektu odkazující na aktuální instanci třídy, jak je původně implementována. `MyClass` je podobný `Me`, ale všechna volání metody jsou považována za, jako kdyby byla metoda `NotOverridable`.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
