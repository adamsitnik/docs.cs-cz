---
title: Uživatelem definované typy CLR
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: b946a87e49d8bf496fb215eb95f9db9cb453c13c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681024"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="4b269-102">Uživatelem definované typy CLR</span><span class="sxs-lookup"><span data-stu-id="4b269-102">CLR User-Defined Types</span></span>
<span data-ttu-id="4b269-103">Microsoft SQL Server poskytuje podporu pro uživatelem definované typy (UDT) implementuje pomocí rozhraní Microsoft .NET Framework common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4b269-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="4b269-104">Modul CLR je integrován do systému SQL Server a tento mechanismus umožňuje rozšířit systém typů databáze.</span><span class="sxs-lookup"><span data-stu-id="4b269-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="4b269-105">Uživatelsky definované typy zajistí možnosti rozšíření uživatele systém typů dat serveru SQL Server a také možnost definovat komplexní typy structured.</span><span class="sxs-lookup"><span data-stu-id="4b269-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="4b269-106">Uživatelsky definovaný typ může poskytnout dvě klíčové výhody z hlediska architektury aplikace:</span><span class="sxs-lookup"><span data-stu-id="4b269-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
-   <span data-ttu-id="4b269-107">Silné zapouzdření (i v klientovi a serveru) mezi vnitřní stav a externí chování.</span><span class="sxs-lookup"><span data-stu-id="4b269-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
-   <span data-ttu-id="4b269-108">Hluboká integrace s jinými související funkce serveru.</span><span class="sxs-lookup"><span data-stu-id="4b269-108">Deep integration with other related server features.</span></span> <span data-ttu-id="4b269-109">Jakmile definujete vlastní UDT, můžete ho ve všech kontextech kde můžete použít typ systému v systému SQL Server, včetně definice sloupců a jako proměnné, parametry, výsledky funkce, ukazatele, aktivační události a replikace.</span><span class="sxs-lookup"><span data-stu-id="4b269-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="4b269-110">Podrobnější informace najdete v článku [dokumentaci k SQL serveru](/sql) pro verzi systému SQL Server používáte.</span><span class="sxs-lookup"><span data-stu-id="4b269-110">For more detailed information, see the [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="4b269-111">**Dokumentaci k SQL serveru**</span><span class="sxs-lookup"><span data-stu-id="4b269-111">**SQL Server documentation**</span></span>
  
1. [<span data-ttu-id="4b269-112">Uživatelem definované typy CLR</span><span class="sxs-lookup"><span data-stu-id="4b269-112">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="see-also"></a><span data-ttu-id="4b269-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b269-113">See also</span></span>

- [<span data-ttu-id="4b269-114">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4b269-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
