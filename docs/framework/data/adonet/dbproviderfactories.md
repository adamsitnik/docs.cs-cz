---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 2376cf39228cb5e8208112333ba06bb80070de84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606993"
---
# <a name="dbproviderfactories"></a><span data-ttu-id="d9050-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="d9050-102">DbProviderFactories</span></span>
<span data-ttu-id="d9050-103"><xref:System.Data.Common> Obor názvů obsahuje třídy pro vytváření <xref:System.Data.Common.DbProviderFactory> instance pro práci s konkrétní zdroje.</span><span class="sxs-lookup"><span data-stu-id="d9050-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="d9050-104">Když vytvoříte <xref:System.Data.Common.DbProviderFactory> instance a předávat informace o poskytovateli dat `DbProviderFactory` můžete určit objekt správný, silného typu připojení se vraťte na základě informací byl poskytnut.</span><span class="sxs-lookup"><span data-stu-id="d9050-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="d9050-105">Počínaje .NET Framework verze 4, zprostředkovatele dat, jako <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, a <xref:System.Data.OracleClient> jsou už není uvedený v souboru machine.config, ale vlastní zprostředkovatelé bude dál zobrazovat existuje.</span><span class="sxs-lookup"><span data-stu-id="d9050-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9050-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d9050-106">In This Section</span></span>  
 [<span data-ttu-id="d9050-107">Přehled modelu objektu pro vytváření</span><span class="sxs-lookup"><span data-stu-id="d9050-107">Factory Model Overview</span></span>](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 <span data-ttu-id="d9050-108">Poskytuje přehled vzoru návrhu objekt pro vytváření a programovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d9050-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="d9050-109">Získání DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="d9050-109">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="d9050-110">Ukazuje, jak se seznam nainstalovaných dat a vytvářet <xref:System.Data.Common.DbConnection> z `DbProviderFactory`.</span><span class="sxs-lookup"><span data-stu-id="d9050-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="d9050-111">DbConnection, DbCommand a DbException</span><span class="sxs-lookup"><span data-stu-id="d9050-111">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="d9050-112">Ukazuje, jak vytvořit <xref:System.Data.Common.DbCommand> a <xref:System.Data.Common.DbDataReader>a způsob zpracování chyb dat pomocí <xref:System.Data.Common.DbException>.</span><span class="sxs-lookup"><span data-stu-id="d9050-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="d9050-113">Úpravy dat přes DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="d9050-113">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="d9050-114">Ukazuje, jak používat <xref:System.Data.Common.DbCommandBuilder> s <xref:System.Data.Common.DbDataAdapter> načtení a upravovat data.</span><span class="sxs-lookup"><span data-stu-id="d9050-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9050-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9050-115">See also</span></span>

- [<span data-ttu-id="d9050-116">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d9050-116">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="d9050-117">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="d9050-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
