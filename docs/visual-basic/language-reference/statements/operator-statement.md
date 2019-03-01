---
title: Operator – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: 44b0a2513f504c8fecec74868130463581b597af
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981696"
---
# <a name="operator-statement"></a><span data-ttu-id="3aa37-102">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="3aa37-102">Operator Statement</span></span>
<span data-ttu-id="3aa37-103">Deklaruje symbol operátoru, operandy a kód, který definuje proceduru operátoru pro třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="3aa37-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aa37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3aa37-104">Syntax</span></span>  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a><span data-ttu-id="3aa37-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="3aa37-105">Parts</span></span>  
 `attrlist`  
 <span data-ttu-id="3aa37-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3aa37-106">Optional.</span></span> <span data-ttu-id="3aa37-107">Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="3aa37-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `Public`  
 <span data-ttu-id="3aa37-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3aa37-108">Required.</span></span> <span data-ttu-id="3aa37-109">Označuje, že tento postup operátor [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup.</span><span class="sxs-lookup"><span data-stu-id="3aa37-109">Indicates that this operator procedure has [Public](../../../visual-basic/language-reference/modifiers/public.md) access.</span></span>  
  
 `Overloads`  
 <span data-ttu-id="3aa37-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3aa37-110">Optional.</span></span> <span data-ttu-id="3aa37-111">Zobrazit [přetížení](../../../visual-basic/language-reference/modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="3aa37-111">See [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span></span>  
  
 `Shared`  
 <span data-ttu-id="3aa37-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3aa37-112">Required.</span></span> <span data-ttu-id="3aa37-113">Označuje, že je tento postup operátor [Shared](../../../visual-basic/language-reference/modifiers/shared.md) postup.</span><span class="sxs-lookup"><span data-stu-id="3aa37-113">Indicates that this operator procedure is a [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedure.</span></span>  
  
 `Shadows`  
 <span data-ttu-id="3aa37-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3aa37-114">Optional.</span></span> <span data-ttu-id="3aa37-115">Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="3aa37-115">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
 `Widening`  
 <span data-ttu-id="3aa37-116">Vyžaduje se pro operátor převodu, pokud zadáte `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="3aa37-117">Označuje, že tento postup operátor definuje [Widening](../../../visual-basic/language-reference/modifiers/widening.md) převodu.</span><span class="sxs-lookup"><span data-stu-id="3aa37-117">Indicates that this operator procedure defines a [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion.</span></span> <span data-ttu-id="3aa37-118">Na tuto stránku nápovědy naleznete v tématu "Rozšíření a zúžení převodů".</span><span class="sxs-lookup"><span data-stu-id="3aa37-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `Narrowing`  
 <span data-ttu-id="3aa37-119">Vyžaduje se pro operátor převodu, pokud zadáte `Widening`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="3aa37-120">Označuje, že tento postup operátor definuje [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) převodu.</span><span class="sxs-lookup"><span data-stu-id="3aa37-120">Indicates that this operator procedure defines a [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="3aa37-121">Na tuto stránku nápovědy naleznete v tématu "Rozšíření a zúžení převodů".</span><span class="sxs-lookup"><span data-stu-id="3aa37-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `operatorsymbol`  
 <span data-ttu-id="3aa37-122">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3aa37-122">Required.</span></span> <span data-ttu-id="3aa37-123">Symbol nebo identifikátor operátor, který definuje této procedury operátora.</span><span class="sxs-lookup"><span data-stu-id="3aa37-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>  
  
 `operand1`  
 <span data-ttu-id="3aa37-124">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3aa37-124">Required.</span></span> <span data-ttu-id="3aa37-125">Název a typ jeden operand unárního operátoru (včetně operátor převodu) nebo levý operand binárního operátoru.</span><span class="sxs-lookup"><span data-stu-id="3aa37-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>  
  
 `operand2`  
 <span data-ttu-id="3aa37-126">Vyžaduje se pro binární operátory.</span><span class="sxs-lookup"><span data-stu-id="3aa37-126">Required for binary operators.</span></span> <span data-ttu-id="3aa37-127">Název a typ pravý operand binárního operátoru.</span><span class="sxs-lookup"><span data-stu-id="3aa37-127">The name and type of the right operand of a binary operator.</span></span>  
  
 <span data-ttu-id="3aa37-128">`operand1` a `operand2` mají následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="3aa37-128">`operand1` and `operand2` have the following syntax and parts:</span></span>  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|<span data-ttu-id="3aa37-129">Část</span><span class="sxs-lookup"><span data-stu-id="3aa37-129">Part</span></span>|<span data-ttu-id="3aa37-130">Popis</span><span class="sxs-lookup"><span data-stu-id="3aa37-130">Description</span></span>|  
|----------|-----------------|  
|`ByVal`|<span data-ttu-id="3aa37-131">Musí být nepovinné, ale mechanismus předávání [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="3aa37-131">Optional, but the passing mechanism must be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>|  
|`operandname`|<span data-ttu-id="3aa37-132">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3aa37-132">Required.</span></span> <span data-ttu-id="3aa37-133">Název proměnné představující tento operand.</span><span class="sxs-lookup"><span data-stu-id="3aa37-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="3aa37-134">Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3aa37-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`operandtype`|<span data-ttu-id="3aa37-135">Volitelné Pokud `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="3aa37-136">Datový typ tohoto operandu.</span><span class="sxs-lookup"><span data-stu-id="3aa37-136">Data type of this operand.</span></span>|  
  
 `type`  
 <span data-ttu-id="3aa37-137">Volitelné Pokud `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="3aa37-138">Vrací datový typ hodnoty procedury operátora.</span><span class="sxs-lookup"><span data-stu-id="3aa37-138">Data type of the value the operator procedure returns.</span></span>  
  
 `statements`  
 <span data-ttu-id="3aa37-139">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3aa37-139">Optional.</span></span> <span data-ttu-id="3aa37-140">Blok příkazů, které spouští procedury operátora.</span><span class="sxs-lookup"><span data-stu-id="3aa37-140">Block of statements that the operator procedure runs.</span></span>  
  
 `returnvalue`  
 <span data-ttu-id="3aa37-141">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3aa37-141">Required.</span></span> <span data-ttu-id="3aa37-142">Hodnota, která procedury operátora vrátí volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="3aa37-142">The value that the operator procedure returns to the calling code.</span></span>  
  
 <span data-ttu-id="3aa37-143">`End``Operator`</span><span class="sxs-lookup"><span data-stu-id="3aa37-143">`End` `Operator`</span></span>  
 <span data-ttu-id="3aa37-144">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3aa37-144">Required.</span></span> <span data-ttu-id="3aa37-145">Ukončí definici této procedury operátora.</span><span class="sxs-lookup"><span data-stu-id="3aa37-145">Terminates the definition of this operator procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3aa37-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3aa37-146">Remarks</span></span>  
 <span data-ttu-id="3aa37-147">Můžete použít `Operator` pouze ve třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="3aa37-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="3aa37-148">To znamená, že *kontext deklarace* operátor nesmí být zdrojový soubor, obor názvů, modulu, rozhraní, procedura nebo blok.</span><span class="sxs-lookup"><span data-stu-id="3aa37-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="3aa37-149">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3aa37-149">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="3aa37-150">Musí být všechny operátory `Public Shared`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="3aa37-151">Nelze zadat `ByRef`, `Optional`, nebo `ParamArray` pro jeden z operandů.</span><span class="sxs-lookup"><span data-stu-id="3aa37-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>  
  
 <span data-ttu-id="3aa37-152">Symbol operátoru nebo identifikátor nelze použít k uložení návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3aa37-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="3aa37-153">Je nutné použít `Return` příkaz který musíte zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3aa37-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="3aa37-154">Libovolný počet `Return` příkazů může vyskytovat kdekoli v postupu.</span><span class="sxs-lookup"><span data-stu-id="3aa37-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>  
  
 <span data-ttu-id="3aa37-155">Definování operátor tento způsob se nazývá *přetížení operátoru*to, jestli používáte `Overloads` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="3aa37-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="3aa37-156">V následující tabulce jsou uvedeny operátory, které můžete definovat.</span><span class="sxs-lookup"><span data-stu-id="3aa37-156">The following table lists the operators you can define.</span></span>  
  
|<span data-ttu-id="3aa37-157">Typ</span><span class="sxs-lookup"><span data-stu-id="3aa37-157">Type</span></span>|<span data-ttu-id="3aa37-158">Operátory</span><span class="sxs-lookup"><span data-stu-id="3aa37-158">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="3aa37-159">Unární</span><span class="sxs-lookup"><span data-stu-id="3aa37-159">Unary</span></span>|<span data-ttu-id="3aa37-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="3aa37-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="3aa37-161">binární</span><span class="sxs-lookup"><span data-stu-id="3aa37-161">Binary</span></span>|<span data-ttu-id="3aa37-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="3aa37-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="3aa37-163">Převod (unární)</span><span class="sxs-lookup"><span data-stu-id="3aa37-163">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="3aa37-164">Všimněte si, že `=` operátor v binárním seznamu je relační operátor, operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3aa37-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="3aa37-165">Při definování `CType`, musíte zadat buď `Widening` nebo `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>  
  
## <a name="matched-pairs"></a><span data-ttu-id="3aa37-166">Odpovídající páry</span><span class="sxs-lookup"><span data-stu-id="3aa37-166">Matched Pairs</span></span>  
 <span data-ttu-id="3aa37-167">Některé operátory je nutné definovat jako odpovídající dvojice.</span><span class="sxs-lookup"><span data-stu-id="3aa37-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="3aa37-168">Pokud definujete buď operátor tyto dvojice, je nutné definovat druhé také.</span><span class="sxs-lookup"><span data-stu-id="3aa37-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="3aa37-169">Odpovídající páry jsou následující:</span><span class="sxs-lookup"><span data-stu-id="3aa37-169">The matched pairs are the following:</span></span>  
  
-   <span data-ttu-id="3aa37-170">`=` a `<>`</span><span class="sxs-lookup"><span data-stu-id="3aa37-170">`=` and `<>`</span></span>  
  
-   <span data-ttu-id="3aa37-171">`>` a `<`</span><span class="sxs-lookup"><span data-stu-id="3aa37-171">`>` and `<`</span></span>  
  
-   <span data-ttu-id="3aa37-172">`>=` a `<=`</span><span class="sxs-lookup"><span data-stu-id="3aa37-172">`>=` and `<=`</span></span>  
  
-   <span data-ttu-id="3aa37-173">`IsTrue` a `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="3aa37-173">`IsTrue` and `IsFalse`</span></span>  
  
## <a name="data-type-restrictions"></a><span data-ttu-id="3aa37-174">Omezení typu dat</span><span class="sxs-lookup"><span data-stu-id="3aa37-174">Data Type Restrictions</span></span>  
 <span data-ttu-id="3aa37-175">Každý operátor, který definujete musí zahrnovat třídy nebo struktury, ve kterém můžete definovat.</span><span class="sxs-lookup"><span data-stu-id="3aa37-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="3aa37-176">To znamená, že třída nebo struktura musí být uvedena jako datový typ z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="3aa37-176">This means that the class or structure must appear as the data type of the following:</span></span>  
  
-   <span data-ttu-id="3aa37-177">Operand unárního operátoru.</span><span class="sxs-lookup"><span data-stu-id="3aa37-177">The operand of a unary operator.</span></span>  
  
-   <span data-ttu-id="3aa37-178">Nejméně jeden z operandů binárního operátoru.</span><span class="sxs-lookup"><span data-stu-id="3aa37-178">At least one of the operands of a binary operator.</span></span>  
  
-   <span data-ttu-id="3aa37-179">Operand nebo návratového typu operátoru převodu.</span><span class="sxs-lookup"><span data-stu-id="3aa37-179">Either the operand or the return type of a conversion operator.</span></span>  
  
 <span data-ttu-id="3aa37-180">Některé operátory mají další datový typ omezení, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3aa37-180">Certain operators have additional data type restrictions, as follows:</span></span>  
  
-   <span data-ttu-id="3aa37-181">Pokud definujete `IsTrue` a `IsFalse` operátory, musí oba vracejí `Boolean` typu.</span><span class="sxs-lookup"><span data-stu-id="3aa37-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>  
  
-   <span data-ttu-id="3aa37-182">Pokud definujete `<<` a `>>` operátory, je nutné obojí zadat `Integer` zadejte `operandtype` z `operand2`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>  
  
 <span data-ttu-id="3aa37-183">Návratový typ nemá tak, aby odpovídaly typu jeden z operandů.</span><span class="sxs-lookup"><span data-stu-id="3aa37-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="3aa37-184">Například operátor porovnání jako `=` nebo `<>` může vrátit `Boolean` i v případě, že ani jeden operand není `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>  
  
## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="3aa37-185">Logické a bitové operátory</span><span class="sxs-lookup"><span data-stu-id="3aa37-185">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="3aa37-186">`And`, `Or`, `Not`, A `Xor` operátory mohou provádět logické a bitové operace v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3aa37-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="3aa37-187">Ale pokud definujete jeden z těchto operátorů v třídě nebo struktuře, můžete definovat pouze jeho bitová operace.</span><span class="sxs-lookup"><span data-stu-id="3aa37-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>  
  
 <span data-ttu-id="3aa37-188">Nelze definovat `AndAlso` operátor přímo s `Operator` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3aa37-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="3aa37-189">Můžete však použít `AndAlso` Pokud jste splnili tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="3aa37-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>  
  
-   <span data-ttu-id="3aa37-190">Jste definovali `And` na stejné typy operandů, kterou chcete použít pro `AndAlso`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>  
  
-   <span data-ttu-id="3aa37-191">Definice `And` vrátí hodnotu stejného typu jako třídy nebo struktury, na kterém jste ji definovali.</span><span class="sxs-lookup"><span data-stu-id="3aa37-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>  
  
-   <span data-ttu-id="3aa37-192">Jste definovali `IsFalse` operátor v třídě nebo struktuře, na které jste definovali `And`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>  
  
 <span data-ttu-id="3aa37-193">Podobně můžete použít `OrElse` Pokud jste definovali `Or` u stejné operandů s návratovým typem třídy nebo struktury a jste definovali `IsTrue` v třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="3aa37-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>  
  
## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="3aa37-194">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="3aa37-194">Widening and Narrowing Conversions</span></span>  
 <span data-ttu-id="3aa37-195">A *rozšiřující převod* vždy úspěšná v době běhu, zatímco *zužující převod* za běhu nemusí zdařit.</span><span class="sxs-lookup"><span data-stu-id="3aa37-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="3aa37-196">Další informace najdete v tématu [Widening a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="3aa37-196">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
 <span data-ttu-id="3aa37-197">Pokud deklarujete proceduru převod bude `Widening`, váš kód procedury nesmí generovat žádné chyby.</span><span class="sxs-lookup"><span data-stu-id="3aa37-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="3aa37-198">To znamená, následující:</span><span class="sxs-lookup"><span data-stu-id="3aa37-198">This means the following:</span></span>  
  
-   <span data-ttu-id="3aa37-199">Platná hodnota typu musí vracet vždycky `type`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-199">It must always return a valid value of type `type`.</span></span>  
  
-   <span data-ttu-id="3aa37-200">Je musí zpracovat všechny výjimky a další chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="3aa37-200">It must handle all possible exceptions and other error conditions.</span></span>  
  
-   <span data-ttu-id="3aa37-201">Vrátí všechny chyby z všechny postupy, které volá, je musí zpracovat.</span><span class="sxs-lookup"><span data-stu-id="3aa37-201">It must handle any error returns from any procedures it calls.</span></span>  
  
 <span data-ttu-id="3aa37-202">Pokud existuje riziko, které by se nemusela podařit proceduru převod, nebo ji může dojít k neošetřené výjimce, je třeba deklarovat bude `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aa37-203">Příklad</span><span class="sxs-lookup"><span data-stu-id="3aa37-203">Example</span></span>  
 <span data-ttu-id="3aa37-204">Následující příklad kódu používá `Operator` příkaz k definování obrysu strukturu, která zahrnuje procedury operátoru pro `And`, `Or`, `IsFalse`, a `IsTrue` operátory.</span><span class="sxs-lookup"><span data-stu-id="3aa37-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="3aa37-205">`And` a `Or` každý používají dva operandy typu `abc` a návratový typ `abc`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="3aa37-206">`IsFalse` a `IsTrue` každá vzít jeden operand typu `abc` a vrátit `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="3aa37-207">Tyto definice povolit, aby volající kód použít `And`, `AndAlso`, `Or`, a `OrElse` s operandy typu `abc`.</span><span class="sxs-lookup"><span data-stu-id="3aa37-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>  
  
 [!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]  
  
## <a name="see-also"></a><span data-ttu-id="3aa37-208">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3aa37-208">See also</span></span>
- [<span data-ttu-id="3aa37-209">Operátor IsFalse</span><span class="sxs-lookup"><span data-stu-id="3aa37-209">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="3aa37-210">Operátor IsTrue</span><span class="sxs-lookup"><span data-stu-id="3aa37-210">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="3aa37-211">Widening</span><span class="sxs-lookup"><span data-stu-id="3aa37-211">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="3aa37-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="3aa37-212">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="3aa37-213">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="3aa37-213">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="3aa37-214">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="3aa37-214">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="3aa37-215">Postupy: Definovat operátor</span><span class="sxs-lookup"><span data-stu-id="3aa37-215">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="3aa37-216">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="3aa37-216">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="3aa37-217">Postupy: Volání procedury operátora</span><span class="sxs-lookup"><span data-stu-id="3aa37-217">How to: Call an Operator Procedure</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="3aa37-218">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="3aa37-218">How to: Use a Class that Defines Operators</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
