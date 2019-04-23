---
title: Datové typy SQL Serveru a ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 9e81e54f223d35a3db9c943edf6f9f9b24110faa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326304"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="fd77c-102">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fd77c-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="fd77c-103">SQL Server a rozhraní .NET Framework jsou založeny na jiný typ systémy, které může způsobit ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="fd77c-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="fd77c-104">K zachování integrity dat, zprostředkovatele dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>) poskytuje typy přístupové metody pro práci s daty formátu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fd77c-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="fd77c-105">Výčty v můžete použít <xref:System.Data.SqlDbType> třídy k určení <xref:System.Data.SqlClient.SqlParameter> datové typy.</span><span class="sxs-lookup"><span data-stu-id="fd77c-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="fd77c-106">Další informace a tabulku, která popisuje mapování datového typu mezi SQL serverem a datové typy rozhraní .NET Framework najdete v tématu [mapování datového typu SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="fd77c-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="fd77c-107">SQL Server 2008 zavádí nové datové typy, které jsou určeny k uspokojení potřeb pro práci s datem a časem, strukturovaná, částečně strukturovaná a Nestrukturovaná data.</span><span class="sxs-lookup"><span data-stu-id="fd77c-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="fd77c-108">Ty jsou popsány v SQL Server 2008 Books Online.</span><span class="sxs-lookup"><span data-stu-id="fd77c-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="fd77c-109">Datové typy serveru SQL Server, které jsou k dispozici pro použití ve vaší aplikaci, závisí na verzi systému SQL Server, který používáte.</span><span class="sxs-lookup"><span data-stu-id="fd77c-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="fd77c-110">Další informace najdete v příslušné verzi SQL Server Books Online v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="fd77c-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="fd77c-111">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="fd77c-111">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="fd77c-112">Datové typy (databázový stroj)</span><span class="sxs-lookup"><span data-stu-id="fd77c-112">Data Types (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a><span data-ttu-id="fd77c-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fd77c-113">In This Section</span></span>  
 [<span data-ttu-id="fd77c-114">SqlTypes a datová sada</span><span class="sxs-lookup"><span data-stu-id="fd77c-114">SqlTypes and the DataSet</span></span>](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 <span data-ttu-id="fd77c-115">Popisuje podporu typu `SqlTypes` v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="fd77c-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="fd77c-116">Zpracování hodnot null</span><span class="sxs-lookup"><span data-stu-id="fd77c-116">Handling Null Values</span></span>](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 <span data-ttu-id="fd77c-117">Ukazuje, jak pracovat s hodnotami null a s hodnotou tři logiku.</span><span class="sxs-lookup"><span data-stu-id="fd77c-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="fd77c-118">Porovnání hodnoty GUID a uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="fd77c-118">Comparing GUID and uniqueidentifier Values</span></span>](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="fd77c-119">Ukazuje, jak pracovat s identifikátorem GUID a uniqueidentifier hodnotami v systému SQL Server a rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd77c-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="fd77c-120">Kalendářní a časová data</span><span class="sxs-lookup"><span data-stu-id="fd77c-120">Date and Time Data</span></span>](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 <span data-ttu-id="fd77c-121">Popisuje, jak použít nové typy dat data a času zavedena v systému SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="fd77c-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="fd77c-122">Velké uživatelsky definované typy</span><span class="sxs-lookup"><span data-stu-id="fd77c-122">Large UDTs</span></span>](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 <span data-ttu-id="fd77c-123">Ukazuje, jak načíst data z velké hodnoty uživatelsky definované typy zavedena v systému SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="fd77c-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="fd77c-124">Data XML na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="fd77c-124">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 <span data-ttu-id="fd77c-125">Popisuje, jak pracovat s XML dat načtených z SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="fd77c-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fd77c-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="fd77c-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="fd77c-127">Popisuje `DataSet` třídy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="fd77c-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="fd77c-128">Popisuje `SqlTypes` obor názvů a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="fd77c-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="fd77c-129">Popisuje `SqlDbType` výčet a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="fd77c-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="fd77c-130">Popisuje `DbType` výčet a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="fd77c-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd77c-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd77c-131">See also</span></span>

- [<span data-ttu-id="fd77c-132">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="fd77c-132">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [<span data-ttu-id="fd77c-133">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="fd77c-133">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="fd77c-134">Parametry s hodnotami v tabulkách</span><span class="sxs-lookup"><span data-stu-id="fd77c-134">Table-Valued Parameters</span></span>](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)
- [<span data-ttu-id="fd77c-135">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="fd77c-135">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="fd77c-136">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="fd77c-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
