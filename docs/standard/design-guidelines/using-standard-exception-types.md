---
title: Použití standardních typů výjimek
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: KrzysztofCwalina
ms.openlocfilehash: b947c7cce057c060b1ab5054d1227f5703ccbf89
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543903"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="12bc2-102">Použití standardních typů výjimek</span><span class="sxs-lookup"><span data-stu-id="12bc2-102">Using Standard Exception Types</span></span>
<span data-ttu-id="12bc2-103">Tato část popisuje standardních výjimek poskytované rozhraní Framework a podrobnosti o jejich využití.</span><span class="sxs-lookup"><span data-stu-id="12bc2-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="12bc2-104">V seznamu nejsou v žádném smyslu vyčerpávající.</span><span class="sxs-lookup"><span data-stu-id="12bc2-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="12bc2-105">Najdete na referenční dokumentaci rozhraní .NET Framework pro použití jiných typů výjimek Framework.</span><span class="sxs-lookup"><span data-stu-id="12bc2-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="12bc2-106">Výjimky a SystemException</span><span class="sxs-lookup"><span data-stu-id="12bc2-106">Exception and SystemException</span></span>  
 <span data-ttu-id="12bc2-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> nebo <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="12bc2-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="12bc2-108">**X DO NOT** catch `System.Exception` nebo `System.SystemException` v rámci kódu, pokud máte v úmyslu opětovné.</span><span class="sxs-lookup"><span data-stu-id="12bc2-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="12bc2-109">**X AVOID** zachytávání `System.Exception` nebo `System.SystemException`, kromě obslužné rutiny výjimek nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="12bc2-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="12bc2-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="12bc2-110">ApplicationException</span></span>  
 <span data-ttu-id="12bc2-111">**X DO NOT** throw nebo jsou odvozeny od <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="12bc2-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="12bc2-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="12bc2-112">InvalidOperationException</span></span>  
 <span data-ttu-id="12bc2-113">**✓ DO** throw <xref:System.InvalidOperationException> Pokud objekt je v nevhodném stavu.</span><span class="sxs-lookup"><span data-stu-id="12bc2-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="12bc2-114">ArgumentException ArgumentNullException a ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="12bc2-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="12bc2-115">**✓ DO** throw <xref:System.ArgumentException> nebo jednoho z jeho podtypech Pokud chybné argumenty jsou předány na člena.</span><span class="sxs-lookup"><span data-stu-id="12bc2-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="12bc2-116">Preferovat nejvíc odvozený typ výjimky, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="12bc2-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="12bc2-117">**✓ DO** nastavit `ParamName` při vyvolání jeden podtříd `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="12bc2-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="12bc2-118">Tato vlastnost představuje název parametru, která způsobila vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="12bc2-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="12bc2-119">Všimněte si, že vlastnost lze nastavit pomocí jednoho z přetížení konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="12bc2-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="12bc2-120">**✓ DO** použít `value` pro název implicitní hodnota parametru nastavením vlastností.</span><span class="sxs-lookup"><span data-stu-id="12bc2-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="12bc2-121">NullReferenceException IndexOutOfRangeException a výjimka AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="12bc2-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="12bc2-122">**X DO NOT** povolit veřejně možné volat rozhraní API pro explicitně nebo implicitně throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, nebo <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="12bc2-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="12bc2-123">Tyto výjimky jsou vyhrazené a vyvolané prováděcí modul a ve že většině případů označuje chybu.</span><span class="sxs-lookup"><span data-stu-id="12bc2-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="12bc2-124">Proveďte kontrolu, aby tyto výjimky argumentu.</span><span class="sxs-lookup"><span data-stu-id="12bc2-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="12bc2-125">Vyvolání těchto výjimek poskytuje metodu, která se můžou časem změnit podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="12bc2-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="12bc2-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="12bc2-126">StackOverflowException</span></span>  
 <span data-ttu-id="12bc2-127">**X DO NOT** explicitní generování <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="12bc2-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="12bc2-128">Pouze pomocí modulu CLR by měla být explicitně vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="12bc2-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="12bc2-129">**X DO NOT** catch `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="12bc2-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="12bc2-130">Je téměř nemožné psát spravovaný kód, který zůstává konzistentní za přítomnosti libovolného zásobníku přetečení.</span><span class="sxs-lookup"><span data-stu-id="12bc2-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="12bc2-131">Díky používání sond přesunout přetečení zásobníku na jasně definovaných místa, nikoli podle anulování z přetečení zásobníku libovolného zůstaly konzistentní nespravované části modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="12bc2-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="12bc2-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="12bc2-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="12bc2-133">**X DO NOT** explicitní generování <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="12bc2-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="12bc2-134">Tato výjimka je vyvolána pouze infrastrukturou CLR.</span><span class="sxs-lookup"><span data-stu-id="12bc2-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="12bc2-135">ComException SEHException – a ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="12bc2-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="12bc2-136">**X DO NOT** explicitní generování <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, a <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="12bc2-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="12bc2-137">Tyto výjimky jsou vyvolány pouze infrastruktury CLR.</span><span class="sxs-lookup"><span data-stu-id="12bc2-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="12bc2-138">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="12bc2-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="12bc2-139">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="12bc2-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12bc2-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12bc2-140">See also</span></span>

- [<span data-ttu-id="12bc2-141">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="12bc2-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="12bc2-142">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="12bc2-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
