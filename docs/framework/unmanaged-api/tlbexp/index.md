---
title: Podpůrné funkce Tlbexp (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f41a233e9b5338bdb0a324ff9af267a97821d4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967697"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="4c197-102">Podpůrné funkce Tlbexp (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="4c197-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="4c197-103">[Nástroje Exportér knihovny typů](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) dynamické knihovny DLL s názvem TlbRef.dll načte (Tlbexp.exe).</span><span class="sxs-lookup"><span data-stu-id="4c197-103">The [Type Library Exporter tool](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="4c197-104">Tato knihovna DLL obsahuje dvě pomocné funkce a rozhraní, které používá nástroj exportu během procesu převodu sestavení na typu knihovny.</span><span class="sxs-lookup"><span data-stu-id="4c197-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c197-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4c197-105">In This Section</span></span>  
 [<span data-ttu-id="4c197-106">GetTypeLibInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="4c197-106">GetTypeLibInfo Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 <span data-ttu-id="4c197-107">Poskytuje informace o lokalizaci a operační systém pro knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="4c197-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="4c197-108">LoadTypeLibWithResolver – funkce</span><span class="sxs-lookup"><span data-stu-id="4c197-108">LoadTypeLibWithResolver Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 <span data-ttu-id="4c197-109">Načte knihovnu typů pomocí implementace [itypelibresolver – rozhraní](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) vyřešit všechny odkazované knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="4c197-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="4c197-110">ITypeLibResolver – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c197-110">ITypeLibResolver Interface</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 <span data-ttu-id="4c197-111">Poskytuje [resolvetypelib – metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), který vrátí plně kvalifikovanou cestu knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="4c197-111">Provides the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
