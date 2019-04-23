---
title: <GenericParameter> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40fef845a55412e5731ec08bd1e038d6b311694c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111654"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="4313a-102">\<GenericParameter > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="4313a-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="4313a-103">Použije zásady na typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="4313a-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4313a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4313a-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4313a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4313a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4313a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4313a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4313a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="4313a-107">Attributes</span></span>  
  
|<span data-ttu-id="4313a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="4313a-108">Attribute</span></span>|<span data-ttu-id="4313a-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="4313a-109">Attribute type</span></span>|<span data-ttu-id="4313a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4313a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="4313a-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="4313a-111">General</span></span>|<span data-ttu-id="4313a-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-112">Required attribute.</span></span> <span data-ttu-id="4313a-113">Název obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="4313a-113">The name of the generic parameter.</span></span> <span data-ttu-id="4313a-114">Například pro obecný delegát <xref:System.Func%603>, hodnota `Name` atribut je "TResult" runtime zásadu chcete uplatnit na návratovou hodnotu tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="4313a-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="4313a-115">Reflexe</span><span class="sxs-lookup"><span data-stu-id="4313a-115">Reflection</span></span>|<span data-ttu-id="4313a-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-116">Optional attribute.</span></span> <span data-ttu-id="4313a-117">Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="4313a-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="4313a-118">Reflexe</span><span class="sxs-lookup"><span data-stu-id="4313a-118">Reflection</span></span>|<span data-ttu-id="4313a-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-119">Optional attribute.</span></span> <span data-ttu-id="4313a-120">Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4313a-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="4313a-121">Reflexe</span><span class="sxs-lookup"><span data-stu-id="4313a-121">Reflection</span></span>|<span data-ttu-id="4313a-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-122">Optional attribute.</span></span> <span data-ttu-id="4313a-123">Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="4313a-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="4313a-124">Serializace</span><span class="sxs-lookup"><span data-stu-id="4313a-124">Serialization</span></span>|<span data-ttu-id="4313a-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-125">Optional attribute.</span></span> <span data-ttu-id="4313a-126">Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="4313a-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="4313a-127">Serializace</span><span class="sxs-lookup"><span data-stu-id="4313a-127">Serialization</span></span>|<span data-ttu-id="4313a-128">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-128">Optional attribute.</span></span> <span data-ttu-id="4313a-129">Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="4313a-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="4313a-130">Serializace</span><span class="sxs-lookup"><span data-stu-id="4313a-130">Serialization</span></span>|<span data-ttu-id="4313a-131">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-131">Optional attribute.</span></span> <span data-ttu-id="4313a-132">Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="4313a-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="4313a-133">Serializace</span><span class="sxs-lookup"><span data-stu-id="4313a-133">Serialization</span></span>|<span data-ttu-id="4313a-134">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-134">Optional attribute.</span></span> <span data-ttu-id="4313a-135">Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="4313a-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="4313a-136">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="4313a-136">Interop</span></span>|<span data-ttu-id="4313a-137">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-137">Optional attribute.</span></span> <span data-ttu-id="4313a-138">Ovládací prvky zásad pro zařazování odkazové typy Windows Runtime a modelu COM.</span><span class="sxs-lookup"><span data-stu-id="4313a-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="4313a-139">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="4313a-139">Interop</span></span>|<span data-ttu-id="4313a-140">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-140">Optional attribute.</span></span> <span data-ttu-id="4313a-141">Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="4313a-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="4313a-142">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="4313a-142">Interop</span></span>|<span data-ttu-id="4313a-143">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-143">Optional attribute.</span></span> <span data-ttu-id="4313a-144">Určuje zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="4313a-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="4313a-145">Název atributu</span><span class="sxs-lookup"><span data-stu-id="4313a-145">Name attribute</span></span>  
  
|<span data-ttu-id="4313a-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4313a-146">Value</span></span>|<span data-ttu-id="4313a-147">Popis</span><span class="sxs-lookup"><span data-stu-id="4313a-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4313a-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="4313a-148">*generic_parameter_name*</span></span>|<span data-ttu-id="4313a-149">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="4313a-149">Required attribute.</span></span> <span data-ttu-id="4313a-150">Název parametru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4313a-150">The name of the generic type parameter.</span></span> <span data-ttu-id="4313a-151">Například pro obecný delegát <xref:System.Func%603>, *generic_parameter_name* hodnotu "TResult" platí zásady modulu runtime pro vrácené hodnoty delegáta.</span><span class="sxs-lookup"><span data-stu-id="4313a-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="4313a-152">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="4313a-152">All other attributes</span></span>  
  
|<span data-ttu-id="4313a-153">Value</span><span class="sxs-lookup"><span data-stu-id="4313a-153">Value</span></span>|<span data-ttu-id="4313a-154">Popis</span><span class="sxs-lookup"><span data-stu-id="4313a-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4313a-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="4313a-155">*policy_setting*</span></span>|<span data-ttu-id="4313a-156">Toto nastavení platí pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="4313a-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="4313a-157">Možné hodnoty jsou `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="4313a-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="4313a-158">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="4313a-158">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4313a-159">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4313a-159">Child Elements</span></span>  
 <span data-ttu-id="4313a-160">Žádné</span><span class="sxs-lookup"><span data-stu-id="4313a-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4313a-161">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4313a-161">Parent Elements</span></span>  
  
|<span data-ttu-id="4313a-162">Prvek</span><span class="sxs-lookup"><span data-stu-id="4313a-162">Element</span></span>|<span data-ttu-id="4313a-163">Popis</span><span class="sxs-lookup"><span data-stu-id="4313a-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4313a-164">\<Method></span><span class="sxs-lookup"><span data-stu-id="4313a-164">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="4313a-165">Použije zásady reflexe runtime konstruktoru nebo metody.</span><span class="sxs-lookup"><span data-stu-id="4313a-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="4313a-166">\<Type></span><span class="sxs-lookup"><span data-stu-id="4313a-166">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="4313a-167">Použije zásady reflexe runtime určitého typu, jako je například třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="4313a-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4313a-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4313a-168">Remarks</span></span>  
 <span data-ttu-id="4313a-169">`<GenericParameter>` Element je podřízeným prvkem buď [ \<metoda >](../../../docs/framework/net-native/method-element-net-native.md) nebo [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu a se používá k aplikování zásad pro konkrétní typ obecný parametr, který je zadat pomocí jejího názvu do obecného typu nebo metodě podpis.</span><span class="sxs-lookup"><span data-stu-id="4313a-169">The `<GenericParameter>` element is a child of either the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="4313a-170">`<GenericParameter>` Element je nejužitečnější při použití se serializátory.</span><span class="sxs-lookup"><span data-stu-id="4313a-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="4313a-171">V následujícím příkladu `<GenericParameter>` element uplatňovat zásady na typ `T` ve voláních serializátor NewtonSoft JSON [JsonConvert.DeserializeObject\<T > (řetězec)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="4313a-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4313a-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4313a-172">See also</span></span>

- [<span data-ttu-id="4313a-173">\<Metoda > – Element</span><span class="sxs-lookup"><span data-stu-id="4313a-173">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="4313a-174">\<Typ > – Element</span><span class="sxs-lookup"><span data-stu-id="4313a-174">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="4313a-175">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="4313a-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="4313a-176">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="4313a-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="4313a-177">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="4313a-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
