---
title: Automaticky implementované vlastnosti – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 1277e0908b42b6f8185219a33c2b28537c8b6607
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244190"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="13776-102">Automaticky implementované vlastnosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="13776-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="13776-103">V jazyce C# 3.0 nebo novější automaticky implementované vlastnosti Zkontrolujte deklaraci vlastnosti stručnější žádné další logiku je vyžadován v přístupových objektech vlastností.</span><span class="sxs-lookup"><span data-stu-id="13776-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="13776-104">Umožňují také klientský kód k vytvoření objektů.</span><span class="sxs-lookup"><span data-stu-id="13776-104">They also enable client code to create objects.</span></span> <span data-ttu-id="13776-105">Když deklarujete vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří privátní, anonymní pomocné pole, který je přístupný pouze prostřednictvím vlastnosti `get` a `set` přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="13776-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13776-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="13776-106">Example</span></span>  
 <span data-ttu-id="13776-107">Následující příklad ukazuje jednoduchý třídu, která má některé automaticky implementované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="13776-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 <span data-ttu-id="13776-108">V jazyce C# 6 nebo novější můžete inicializovat automaticky implementované vlastnosti podobně jako na pole:</span><span class="sxs-lookup"><span data-stu-id="13776-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="13776-109">Třída, která se zobrazí v předchozím příkladu je proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="13776-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="13776-110">Klientský kód může změnit hodnoty v objektech po jejich vytvoření.</span><span class="sxs-lookup"><span data-stu-id="13776-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="13776-111">V komplexní tříd, které obsahují důležité chování (metody) a také data je často potřeba mít veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13776-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="13776-112">Však pro malé třídy nebo struktury, které právě zapouzdření sadu hodnot (data) a mít žádné nebo téměř žádné chování, by měly buď provádět objekty neměnné deklarováním přístupový objekt set jako [privátní](../../../csharp/language-reference/keywords/private.md) (neměnné spotřebitelům), nebo deklarace pouze přístupový objekt get (neměnné všude s výjimkou konstruktoru).</span><span class="sxs-lookup"><span data-stu-id="13776-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="13776-113">Další informace najdete v tématu [jak: Implementace lehké třídy s automaticky implementovanými vlastnostmi](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="13776-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="13776-114">Atributy jsou povolené automaticky implementované vlastnosti ale samozřejmě ne pole zálohování od těch, nejsou přístupné ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="13776-114">Attributes are permitted on auto-implemented properties but obviously not on the backing fields since those are not accessible from your source code.</span></span> <span data-ttu-id="13776-115">Pokud je nutné použít atribut na pomocným polem vlastnosti, stačí vytvořte jenom obvyklá vlastnost.</span><span class="sxs-lookup"><span data-stu-id="13776-115">If you must use an attribute on the backing field of a property, just create a regular property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13776-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="13776-116">See Also</span></span>

- [<span data-ttu-id="13776-117">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="13776-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="13776-118">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="13776-118">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
