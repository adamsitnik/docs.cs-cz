---
title: '#If... Then... #Else – direktivy (Visual Basic)'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: 8c0aece749edf144fdd5c8ede9ec7e2e4c96ad54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746714"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else – direktivy
Podmíněně zkompiluje vybrané bloky kódu jazyka Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a>Součásti  
 `expression`  
 Vyžaduje se pro `#If` a `#ElseIf` příkazy, volitelné jinde. Libovolný výraz, který se skládá pouze z jedné nebo více podmíněné konstanty kompilátoru, literály a operátory, které vyhodnotí jako `True` nebo `False`.  
  
 `statements`  
 Vyžaduje se pro `#If` příkaz blokovat, volitelné jinde. Řádky programu jazyka Visual Basic nebo direktivy kompilátoru, které jsou kompilovány, pokud přidružený výraz je vyhodnocen jako `True`.  
  
 `#End If`  
 Ukončuje `#If` blok příkazů.  
  
## <a name="remarks"></a>Poznámky  
 Na ploše, chování `#If...Then...#Else` direktivy vypadá stejně jako u `If...Then...Else` příkazy. Ale `#If...Then...#Else` direktivy vyhodnotit, co je kompilovány pomocí kompilátoru, že `If...Then...Else` příkazy vyhodnotí podmínky za běhu.  
  
 Podmíněná kompilace se obvykle používá ke kompilaci stejného programu pro různé platformy. Používá se také aby se zabránilo ladění kódu povolí, spustitelný soubor. Kód při podmíněné kompilace je zcela vynecháno z konečný spustitelný soubor, takže nemá žádný vliv na výkon nebo velikost.  
  
 Bez ohledu na výsledek jakékoli hodnocení, všechny výrazy jsou vyhodnocovány pomocí `Option Compare Binary`. `Option Compare` Příkazu nemá vliv na výrazy v `#If` a `#ElseIf` příkazy.  
  
> [!NOTE]
>  Žádné jedním řádkem formu `#If`, `#Else`, `#ElseIf`, a `#End If` direktivy existuje. Žádný další kód se nemůže objevit na stejném řádku jako některý z direktivy. 

Příkazy v rámci bloku podmíněné kompilace musí být úplná logické prohlášení. Například nelze Podmíněná kompilace pouze atributy funkce, ale je možné deklarovat podmíněně funkce společně s jeho atributy:

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a>Příklad
 V tomto příkladu `#If...Then...#Else` konstrukce k určení, jestli se má zkompilovat určité příkazy.  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Direktiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
