---
title: Načítání informací o databázovém schématu
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 885d3c9ad61c9099c960ddb0c0f77fa8a98dbefa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664243"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="6e6d6-102">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="6e6d6-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="6e6d6-103">Získání informací o schématu z databáze se provádí v procesu zjišťování schématu.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="6e6d6-104">Zjišťování schématu umožňuje aplikacím vyžadovat, že spravovaného poskytovatele vyhledání a vrácení informací o schématu databáze, označované také jako *metadat*, dané databáze.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="6e6d6-105">Prvky schématu jinou databázi, jako například tabulky, sloupce a uložené procedury jsou přístupné prostřednictvím kolekce schémat.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="6e6d6-106">Každá kolekce schématu obsahuje širokou škálu informací o schématu specifické pro použitý zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="6e6d6-107">Každá implementace spravovaného zprostředkovatele .NET Framework **GetSchema** metoda ve **připojení** třídy a informace o schématu, která je vrácena z **GetSchema**metoda je k dispozici ve formě <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="6e6d6-108">**GetSchema** je metoda přetížená metoda, která poskytuje volitelných parametrů pro určení kolekce schématu pro vrácení a omezit množství vrácených informací.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="6e6d6-109">Zprostředkovatelé dat .NET Framework pro OLE DB, ODBC, Oracle a SqlClient poskytují **GetSchemaTable** metodu, která vrací objekt DataTable popisující sloupce metadat **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="6e6d6-110">Zprostředkovatel dat .NET Framework pro OLE DB také poskytuje informace o schématu pomocí <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> metodu <xref:System.Data.OleDb.OleDbConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="6e6d6-111">Jako argumenty **Metoda GetOleDbSchemaTable** přebírá <xref:System.Data.OleDb.OleDbSchemaGuid> , který identifikuje vrátí informace o schématu, a vrátí pole omezení toho, které sloupce.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="6e6d6-112">**Metoda GetOleDbSchemaTable** vrátí <xref:System.Data.DataTable> načtou informace požadované schéma.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e6d6-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6e6d6-113">In This Section</span></span>  
 [<span data-ttu-id="6e6d6-114">Příkaz GetSchema a kolekce schémat</span><span class="sxs-lookup"><span data-stu-id="6e6d6-114">GetSchema and Schema Collections</span></span>](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 <span data-ttu-id="6e6d6-115">Popisuje **GetSchema** metoda a jak ho lze načíst a omezit informace o schématu z databáze.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="6e6d6-116">Omezení schématu</span><span class="sxs-lookup"><span data-stu-id="6e6d6-116">Schema Restrictions</span></span>  
 <span data-ttu-id="6e6d6-117">Popisuje omezení schématu, které lze použít s **GetSchema**.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="6e6d6-118">Společné kolekce schémat</span><span class="sxs-lookup"><span data-stu-id="6e6d6-118">Common Schema Collections</span></span>](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 <span data-ttu-id="6e6d6-119">Popisuje všechny společné kolekce schémat všech zprostředkovatelů spravovaným rozhraním .NET Framework podporován.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="6e6d6-120">Kolekce schémat SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="6e6d6-120">SQL Server Schema Collections</span></span>](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 <span data-ttu-id="6e6d6-121">Popisuje kolekci schémat zprostředkovatelem rozhraní .NET Framework pro SQL Server podporována.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="6e6d6-122">Kolekce schémat Oracle</span><span class="sxs-lookup"><span data-stu-id="6e6d6-122">Oracle Schema Collections</span></span>](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 <span data-ttu-id="6e6d6-123">Popisuje kolekci schémat zprostředkovatelem rozhraní .NET Framework pro Oracle podporována.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="6e6d6-124">Kolekce schémat ODBC</span><span class="sxs-lookup"><span data-stu-id="6e6d6-124">ODBC Schema Collections</span></span>](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 <span data-ttu-id="6e6d6-125">Popisuje kolekce schémat pro ovladače ODBC.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="6e6d6-126">Kolekce schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="6e6d6-126">OLE DB Schema Collections</span></span>](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 <span data-ttu-id="6e6d6-127">Popisuje kolekce schémat pro zprostředkovatele OLE DB.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6e6d6-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="6e6d6-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="6e6d6-129">Popisuje **GetSchema** metodu <xref:System.Data.Common.DbConnection> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="6e6d6-130">Popisuje **GetSchema** metodu <xref:System.Data.Odbc.OdbcConnection> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="6e6d6-131">Popisuje **GetSchema** metodu <xref:System.Data.OleDb.OleDbConnection> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="6e6d6-132">Popisuje **GetSchema** metodu <xref:System.Data.OracleClient.OracleConnection> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="6e6d6-133">Popisuje **GetSchema** metodu <xref:System.Data.SqlClient.SqlConnection> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="6e6d6-134">Popisuje **GetSchemaTable** metodu <xref:System.Data.Common.DbDataReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="6e6d6-135">Popisuje **GetSchemaTable** metodu <xref:System.Data.Odbc.OdbcDataReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="6e6d6-136">Popisuje **GetSchemaTable** metodu <xref:System.Data.OleDb.OleDbDataReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="6e6d6-137">Popisuje **GetSchemaTable** metodu <xref:System.Data.OracleClient.OracleDataReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="6e6d6-138">Popisuje **GetSchemaTable** metodu <xref:System.Data.SqlClient.SqlDataReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="6e6d6-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6d6-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e6d6-139">See also</span></span>

- [<span data-ttu-id="6e6d6-140">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6e6d6-140">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="6e6d6-141">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="6e6d6-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
