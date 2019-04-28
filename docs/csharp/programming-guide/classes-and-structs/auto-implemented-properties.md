---
title: Automaticky implementované vlastnosti – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: b5447dea8b510def95041549555de2ed5592e2d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683753"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Automaticky implementované vlastnosti (Průvodce programováním v C#)
V jazyce C# 3.0 nebo novější automaticky implementované vlastnosti Zkontrolujte deklaraci vlastnosti stručnější žádné další logiku je vyžadován v přístupových objektech vlastností. Umožňují také klientský kód k vytvoření objektů. Když deklarujete vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří privátní, anonymní pomocné pole, který je přístupný pouze prostřednictvím vlastnosti `get` a `set` přistupující objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchý třídu, která má některé automaticky implementované vlastnosti:  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 V jazyce C# 6 nebo novější můžete inicializovat automaticky implementované vlastnosti podobně jako na pole:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 Třída, která se zobrazí v předchozím příkladu je proměnlivá. Klientský kód může změnit hodnoty v objektech po jejich vytvoření. V komplexní tříd, které obsahují důležité chování (metody) a také data je často potřeba mít veřejné vlastnosti. Však pro malé třídy nebo struktury, které právě zapouzdření sadu hodnot (data) a mít žádné nebo téměř žádné chování, by měly buď provádět objekty neměnné deklarováním přístupový objekt set jako [privátní](../../../csharp/language-reference/keywords/private.md) (neměnné spotřebitelům), nebo deklarace pouze přístupový objekt get (neměnné všude s výjimkou konstruktoru).  Další informace najdete v tématu [jak: Implementace lehké třídy s automaticky implementovanými vlastnostmi](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).  
  
## <a name="see-also"></a>Viz také:

- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)
