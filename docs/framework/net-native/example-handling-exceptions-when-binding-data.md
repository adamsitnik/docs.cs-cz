---
title: 'Příklad: Zpracování výjimek při vázání dat'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25b2117de40bbe7ba36fab028526116fc01ae09b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199892"
---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="6be43-102">Příklad: Zpracování výjimek při vázání dat</span><span class="sxs-lookup"><span data-stu-id="6be43-102">Example: Handling Exceptions When Binding Data</span></span>
> [!NOTE]
>  <span data-ttu-id="6be43-103">Toto téma odkazuje na .NET Native Developer Preview, což je předběžná verze softwaru.</span><span class="sxs-lookup"><span data-stu-id="6be43-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="6be43-104">Preview z si můžete stáhnout [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).</span><span class="sxs-lookup"><span data-stu-id="6be43-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="6be43-105">Následující příklad ukazuje, jak vyřešit [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimka, která je vyvolána při kompilaci aplikace s [!INCLUDE[net_native](../../../includes/net-native-md.md)] řetězce nástrojů se pokusí svázat data.</span><span class="sxs-lookup"><span data-stu-id="6be43-105">The following example shows how to resolve a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain tries to bind data.</span></span> <span data-ttu-id="6be43-106">Tady je informace o výjimce:</span><span class="sxs-lookup"><span data-stu-id="6be43-106">Here’s the exception information:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="6be43-107">Tady je přidružené volání zásobníku:</span><span class="sxs-lookup"><span data-stu-id="6be43-107">Here's the associated call stack:</span></span>  
  
```  
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f   
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31   
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="6be43-108">Co dělal aplikace?</span><span class="sxs-lookup"><span data-stu-id="6be43-108">What was the app doing?</span></span>  
 <span data-ttu-id="6be43-109">Základní zásobníku, snímků z <xref:Windows.UI.Xaml?displayProperty=nameWithType> obor názvů znamenat, že byl spuštěn modul vykreslování XAML.</span><span class="sxs-lookup"><span data-stu-id="6be43-109">At the base of the stack, frames from the <xref:Windows.UI.Xaml?displayProperty=nameWithType> namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="6be43-110">Použití <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> metoda označuje založenými na reflexi vyhledávání hodnoty vlastnosti v typu, jehož metadata byla odebrána.</span><span class="sxs-lookup"><span data-stu-id="6be43-110">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="6be43-111">Prvním krokem při poskytování metadat směrnice by pro přidání `serialize` metadat pro typ tak, aby její vlastnosti jsou všechny dostupné:</span><span class="sxs-lookup"><span data-stu-id="6be43-111">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="6be43-112">Je to izolované případu?</span><span class="sxs-lookup"><span data-stu-id="6be43-112">Is this an isolated case?</span></span>  
 <span data-ttu-id="6be43-113">V tomto scénáři, kdy datové vazby má neúplný metadata pro jeden `ViewModel`, může pro ostatní uživatele, příliš.</span><span class="sxs-lookup"><span data-stu-id="6be43-113">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="6be43-114">Pokud kód je strukturována tak, aby aplikace zobrazit modely jsou všechny na `App.ViewModels` obor názvů, můžete použít další obecné direktivy modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="6be43-114">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="6be43-115">Může být kód přepsán nechcete použít reflexe?</span><span class="sxs-lookup"><span data-stu-id="6be43-115">Could the code be rewritten to not use reflection?</span></span>  
 <span data-ttu-id="6be43-116">Datová vazba je náročné na reflexi, změny kódu, aby se zabránilo reflexe není vhodná.</span><span class="sxs-lookup"><span data-stu-id="6be43-116">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="6be43-117">Existují však způsoby, jak určit `ViewModel` na stránku XAML tak, aby řetězce nástrojů můžete přidružit vlastnost vazby pomocí správného typu v době kompilace a zachovat metadata bez použití direktivy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6be43-117">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="6be43-118">Například můžete použít <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> atribut na vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6be43-118">For example, you could apply the <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> attribute on properties.</span></span> <span data-ttu-id="6be43-119">To způsobí, že kompilátor XAML generovat informace o požadované vyhledávání a se vyhnete nutnosti direktivy modulu runtime v souboru Default.rd.xml.</span><span class="sxs-lookup"><span data-stu-id="6be43-119">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be43-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6be43-120">See also</span></span>

- [<span data-ttu-id="6be43-121">Začínáme</span><span class="sxs-lookup"><span data-stu-id="6be43-121">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="6be43-122">Příklad: Řešení potíží s dynamickým programováním</span><span class="sxs-lookup"><span data-stu-id="6be43-122">Example: Troubleshooting Dynamic Programming</span></span>](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
