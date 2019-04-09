---
title: Připojení ke zdroji dat v ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: c04624be758e4bc7c8b1981ad6a9dc44430d62b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083709"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="714e0-102">Připojení ke zdroji dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="714e0-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="714e0-103">V ADO.NET pomocí **připojení** objektu, který chcete připojit ke konkrétnímu zdroji dat zadáním potřebné ověřovací údaje v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="714e0-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="714e0-104">**Připojení** objektu použijete, závisí na typu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="714e0-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="714e0-105">Má každý zprostředkovatele dat .NET Framework je součástí rozhraní .NET Framework <xref:System.Data.Common.DbConnection> objektu: obsahuje zprostředkovatele dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbConnection> objektu zprostředkovatele dat .NET Framework pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlConnection> objektu,. Zahrnuje NET Framework Data Provider pro rozhraní ODBC <xref:System.Data.Odbc.OdbcConnection> objektu a zprostředkovatele dat .NET Framework pro Oracle se zahrnuje <xref:System.Data.OracleClient.OracleConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="714e0-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="714e0-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="714e0-106">In This Section</span></span>  
 [<span data-ttu-id="714e0-107">Navazování připojení</span><span class="sxs-lookup"><span data-stu-id="714e0-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="714e0-108">Popisuje způsob použití **připojení** k navázání připojení ke zdroji dat objektu.</span><span class="sxs-lookup"><span data-stu-id="714e0-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="714e0-109">Události připojení</span><span class="sxs-lookup"><span data-stu-id="714e0-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="714e0-110">Popisuje způsob použití **InfoMessage** na načtení informační zprávy ze zdroje dat události.</span><span class="sxs-lookup"><span data-stu-id="714e0-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="714e0-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="714e0-111">See also</span></span>

- [<span data-ttu-id="714e0-112">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="714e0-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="714e0-113">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="714e0-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)
- [<span data-ttu-id="714e0-114">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="714e0-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="714e0-115">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="714e0-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="714e0-116">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="714e0-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [<span data-ttu-id="714e0-117">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="714e0-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
