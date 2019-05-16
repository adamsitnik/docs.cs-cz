---
title: Aktivace založená na konfiguraci v IIS a WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 99f6c7d41620a7bafea0981cbeaa5cdcbad5ef12
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636130"
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="eb04d-102">Aktivace založená na konfiguraci v IIS a WAS</span><span class="sxs-lookup"><span data-stu-id="eb04d-102">Configuration-Based Activation in IIS and WAS</span></span>

<span data-ttu-id="eb04d-103">Obvykle při hostování služby Windows Communication Foundation (WCF) v rámci Internetové informační služby (IIS) nebo Windows Process Activation Service (WAS), je nutné zadat soubor SVC.</span><span class="sxs-lookup"><span data-stu-id="eb04d-103">Normally when hosting a Windows Communication Foundation (WCF) service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="eb04d-104">Souboru SVC obsahuje název služby a objektu pro vytváření hostitele volitelné vlastní služby.</span><span class="sxs-lookup"><span data-stu-id="eb04d-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="eb04d-105">Tento přidaný soubor přidává režijní náklady na správu.</span><span class="sxs-lookup"><span data-stu-id="eb04d-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="eb04d-106">Funkce aktivace podle konfigurace eliminuje nutnost mít souboru .svc a proto přidružené režie.</span><span class="sxs-lookup"><span data-stu-id="eb04d-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>

## <a name="configuration-based-activation"></a><span data-ttu-id="eb04d-107">Aktivace podle konfigurace</span><span class="sxs-lookup"><span data-stu-id="eb04d-107">Configuration-Based Activation</span></span>

<span data-ttu-id="eb04d-108">Aktivace podle konfigurace používá metadata, která používá budou umístěny v souboru svc a umístí jej do souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="eb04d-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="eb04d-109">V rámci <`serviceHostingEnvironment`> element neexistuje <`serviceActivations`> element.</span><span class="sxs-lookup"><span data-stu-id="eb04d-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="eb04d-110">V rámci <`serviceActivations`> element jsou jeden nebo více <`add`> elementy, jeden pro každý hostovanou službu.</span><span class="sxs-lookup"><span data-stu-id="eb04d-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="eb04d-111"><`add`> Element obsahuje atributy, které umožňují nastavit relativní adresu pro službu a typ služby nebo objekt pro vytváření hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="eb04d-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="eb04d-112">Následující příklad kódu konfigurace ukazuje, jak se používá v této části.</span><span class="sxs-lookup"><span data-stu-id="eb04d-112">The following configuration example code shows how this section is used.</span></span>

> [!NOTE]
>  <span data-ttu-id="eb04d-113">Každý <`add`> element musí určovat atribut factory nebo služby.</span><span class="sxs-lookup"><span data-stu-id="eb04d-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="eb04d-114">Zadání služba a výrobce atributy je povoleno.</span><span class="sxs-lookup"><span data-stu-id="eb04d-114">Specifying both service and factory attributes is allowed.</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 <span data-ttu-id="eb04d-115">S tímto v souboru Web.config můžete umístit služby zdrojový kód v adresáři App_Code splněny sestavení v adresáři Bin aplikace nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb04d-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>

> [!NOTE]
> - <span data-ttu-id="eb04d-116">Při použití aktivace prostřednictvím konfigurace, vložení kódu za hledání souborů .svc se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="eb04d-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>
> - <span data-ttu-id="eb04d-117">`relativeAddress` Atribut musí být nastaven na relativní adresu, jako například "\<podadresář > / service.svc" nebo "~ /\<directory dílčí, service.svc".</span><span class="sxs-lookup"><span data-stu-id="eb04d-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>
> - <span data-ttu-id="eb04d-118">Když si zaregistrujete relativní adresa, na kterém není známá přípona přidružená k WCF, je vyvolána výjimka v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="eb04d-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>
> - <span data-ttu-id="eb04d-119">Zadaná relativní adresa je relativní vzhledem k kořen virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb04d-119">The relative address specified is relative to the root of the virtual application.</span></span>
> - <span data-ttu-id="eb04d-120">Z důvodu hierarchický model konfigurace registrované relativní adresy na úrovni počítače a serveru jsou děděné virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb04d-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>
> - <span data-ttu-id="eb04d-121">Registrace v konfiguračním souboru mají přednost před nastavením v .svc, .xamlx, XOML nebo jiný soubor.</span><span class="sxs-lookup"><span data-stu-id="eb04d-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>
> - <span data-ttu-id="eb04d-122">Žádné ' \' (zpětná lomítka) v identifikátoru URI odeslané do služby IIS / WAS se automaticky převedou na "/" (lomítko).</span><span class="sxs-lookup"><span data-stu-id="eb04d-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="eb04d-123">Pokud je relativní adresa se přidá, který obsahuje "\" a odeslat služby IIS, který používá relativní adresu URI, zpětné lomítko je převedeno na dopředné lomítko a služby IIS nesmí odpovídat na relativní adresu.</span><span class="sxs-lookup"><span data-stu-id="eb04d-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="eb04d-124">Služba IIS odesílá informace o trasování, která označuje, že nejsou nalezeny žádné odpovídající položky.</span><span class="sxs-lookup"><span data-stu-id="eb04d-124">IIS sends out trace information that indicates that there are no matches found.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb04d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb04d-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [<span data-ttu-id="eb04d-126">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="eb04d-126">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="eb04d-127">Přehled hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="eb04d-127">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [<span data-ttu-id="eb04d-128">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="eb04d-128">\<serviceHostingEnvironment></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [<span data-ttu-id="eb04d-129">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="eb04d-129">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
