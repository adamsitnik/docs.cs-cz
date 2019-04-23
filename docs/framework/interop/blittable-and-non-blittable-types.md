---
title: Přenositelné a nepřenositelné typy
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37b226cad9a34f1629d2972dacf8019adad54d7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115372"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="1d848-102">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="1d848-102">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="1d848-103">Většina datových typů mají společné reprezentaci ve spravované i nespravované paměti a nevyžadují žádná zvláštní zacházení podle interoperační zařazovač.</span><span class="sxs-lookup"><span data-stu-id="1d848-103">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="1d848-104">Tyto typy jsou označovány jako *přenositelné typy* vzhledem k tomu, že když jsou předávány mezi nevyžadují převod spravovaného a nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="1d848-104">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="1d848-105">Struktury, které jsou vráceny z platformy vyvolat volání musí být přenositelné typy.</span><span class="sxs-lookup"><span data-stu-id="1d848-105">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="1d848-106">Vyvolání platformy nepodporuje nepřenositelné struktury jako typy vracených hodnot.</span><span class="sxs-lookup"><span data-stu-id="1d848-106">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="1d848-107">Následující typy <xref:System> obor názvů jsou přenositelné typy:</span><span class="sxs-lookup"><span data-stu-id="1d848-107">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
-   <xref:System.Byte?displayProperty=nameWithType>  
  
-   <xref:System.SByte?displayProperty=nameWithType>  
  
-   <xref:System.Int16?displayProperty=nameWithType>  
  
-   <xref:System.UInt16?displayProperty=nameWithType>  
  
-   <xref:System.Int32?displayProperty=nameWithType>  
  
-   <xref:System.UInt32?displayProperty=nameWithType>  
  
-   <xref:System.Int64?displayProperty=nameWithType>  
  
-   <xref:System.UInt64?displayProperty=nameWithType>  
  
-   <xref:System.IntPtr?displayProperty=nameWithType>  
  
-   <xref:System.UIntPtr?displayProperty=nameWithType>  
  
-   <xref:System.Single?displayProperty=nameWithType>  
  
-   <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="1d848-108">Přenositelné typy jsou také následující komplexní typy:</span><span class="sxs-lookup"><span data-stu-id="1d848-108">The following complex types are also blittable types:</span></span>  
  
-   <span data-ttu-id="1d848-109">Jednorozměrná pole přenositelné typy, jako je například pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="1d848-109">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="1d848-110">Ale typ, který obsahuje proměnné pole přenositelné typy není samotného typu blittable.</span><span class="sxs-lookup"><span data-stu-id="1d848-110">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
-   <span data-ttu-id="1d848-111">Formátovaná hodnota typy, které obsahují pouze přenositelné typy (a třídy, pokud jsou zařazeny jako formátovaný typy).</span><span class="sxs-lookup"><span data-stu-id="1d848-111">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="1d848-112">Další informace o typech formátovaná hodnota najdete v tématu [výchozí zařazování pro typy hodnot](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="1d848-112">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="1d848-113">Odkazy na objekty nejsou typu blittable.</span><span class="sxs-lookup"><span data-stu-id="1d848-113">Object references are not blittable.</span></span> <span data-ttu-id="1d848-114">To zahrnuje pole odkazů na objekty, které jsou přenositelné samy o sobě.</span><span class="sxs-lookup"><span data-stu-id="1d848-114">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="1d848-115">Například můžete definovat strukturu, která je typu blittable, ale nelze definovat typu blittable, který obsahuje pole odkazů na tyto struktury.</span><span class="sxs-lookup"><span data-stu-id="1d848-115">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="1d848-116">Optimalizace, jsou pole přenositelné typy a třídy, které obsahují pouze členy typu blittable [připnuté](../../../docs/framework/interop/copying-and-pinning.md) místo zkopírovaných při zařazování.</span><span class="sxs-lookup"><span data-stu-id="1d848-116">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](../../../docs/framework/interop/copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="1d848-117">Tyto typy může zdát zařadit jako vstup a výstup parametry při volajícím a volaným jsou ve stejném objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="1d848-117">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="1d848-118">Ale tyto typy jsou ve skutečnosti zařadit jako parametry in a je nutné použít <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributy, pokud chcete zařadit argument jako vstupně -výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="1d848-118">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="1d848-119">Některé spravované datové typy vyžadují různé reprezentace v nespravované prostředí.</span><span class="sxs-lookup"><span data-stu-id="1d848-119">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="1d848-120">Tyto nepřenositelné typy dat musí být převeden do formuláře, který může být zařazována.</span><span class="sxs-lookup"><span data-stu-id="1d848-120">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="1d848-121">Například spravované řetězce jsou nepřenositelné typy, protože je potřeba je převést na řetězec objekty předtím, než může být zařazována.</span><span class="sxs-lookup"><span data-stu-id="1d848-121">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="1d848-122">V následující tabulce jsou uvedeny nepřenositelné typy z <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1d848-122">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="1d848-123">[Delegáti](default-marshaling-behavior.md#default-marshaling-for-delegates), které jsou datové struktury, které odkazují na statickou metodu nebo instanci třídy jsou také nepřenositelná.</span><span class="sxs-lookup"><span data-stu-id="1d848-123">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="1d848-124">Přenositelné bez typu</span><span class="sxs-lookup"><span data-stu-id="1d848-124">Non-blittable type</span></span>|<span data-ttu-id="1d848-125">Popis</span><span class="sxs-lookup"><span data-stu-id="1d848-125">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="1d848-126">[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="1d848-126">[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md)</span></span>|<span data-ttu-id="1d848-127">Převede pole stylu C nebo `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="1d848-127">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="1d848-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1d848-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="1d848-129">Převede na 1, 2 nebo 4 bajty hodnoty s `true` jako 1 nebo -1.</span><span class="sxs-lookup"><span data-stu-id="1d848-129">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="1d848-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1d848-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="1d848-131">Převede znak Unicode nebo ANSI.</span><span class="sxs-lookup"><span data-stu-id="1d848-131">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="1d848-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1d848-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="1d848-133">Převede na třídy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1d848-133">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="1d848-134">System.Object</span><span class="sxs-lookup"><span data-stu-id="1d848-134">System.Object</span></span>](../../../docs/framework/interop/default-marshaling-for-objects.md)|<span data-ttu-id="1d848-135">Převede hodnotu typu variant nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1d848-135">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="1d848-136">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="1d848-136">System.Mdarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="1d848-137">Převede pole stylu C nebo `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="1d848-137">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="1d848-138">System.String</span><span class="sxs-lookup"><span data-stu-id="1d848-138">System.String</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)|<span data-ttu-id="1d848-139">Převede řetězec ukončení v odkaz s hodnotou null nebo BSTR.</span><span class="sxs-lookup"><span data-stu-id="1d848-139">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="1d848-140">[Typ System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1d848-140">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="1d848-141">Převede na strukturu s rozložením pevné paměti.</span><span class="sxs-lookup"><span data-stu-id="1d848-141">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="1d848-142">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="1d848-142">System.Szarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="1d848-143">Převede pole stylu C nebo `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="1d848-143">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="1d848-144">Typy tříd a objektů jsou podporovány pouze komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="1d848-144">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="1d848-145">Pro odpovídající typy v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#a C++, naleznete v tématu [– přehled knihovny tříd](../../../docs/standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1d848-145">For corresponding types in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++, see the [Class Library Overview](../../../docs/standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d848-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d848-146">See also</span></span>

- [<span data-ttu-id="1d848-147">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="1d848-147">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)
