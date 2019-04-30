---
title: Spuštění příkazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: c3ed424aff3cd485a78d26a7f27bc5b1eac66448
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879408"
---
# <a name="executing-a-command"></a><span data-ttu-id="493de-102">Spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="493de-102">Executing a Command</span></span>
<span data-ttu-id="493de-103">Každý poskytovatel dat rozhraní .NET Framework součástí rozhraní .NET Framework má svůj vlastní objekt příkazu, která dědí z <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="493de-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="493de-104">Obsahuje zprostředkovatele dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbCommand> objektu zprostředkovatele dat .NET Framework pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlCommand> objektu zprostředkovatele dat .NET Framework pro ODBC zahrnuje <xref:System.Data.Odbc.OdbcCommand> objektu a rozhraní .NET Framework Zprostředkovatel dat pro Oracle se zahrnuje <xref:System.Data.OracleClient.OracleCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="493de-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="493de-105">Každá z těchto metod zpřístupňuje objekty pro spouštění příkazů na základě typu příkazu a požadovaného vrácené hodnoty, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="493de-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="493de-106">Příkaz</span><span class="sxs-lookup"><span data-stu-id="493de-106">Command</span></span>|<span data-ttu-id="493de-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="493de-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="493de-108">Vrátí hodnotu `DataReader` objektu.</span><span class="sxs-lookup"><span data-stu-id="493de-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="493de-109">Vrátí jednu skalární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="493de-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="493de-110">Provede příkaz, který nevrací žádné řádky.</span><span class="sxs-lookup"><span data-stu-id="493de-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="493de-111">Vrátí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="493de-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="493de-112">K dispozici pro `SqlCommand` pouze objekt.</span><span class="sxs-lookup"><span data-stu-id="493de-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="493de-113">Také podporuje každý příkaz silného typu objektu <xref:System.Data.CommandType> výčet, který určuje, jak interpretovat řetězec příkazu, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="493de-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="493de-114">CommandType</span><span class="sxs-lookup"><span data-stu-id="493de-114">CommandType</span></span>|<span data-ttu-id="493de-115">Popis</span><span class="sxs-lookup"><span data-stu-id="493de-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="493de-116">Příkaz SQL definovat příkazy, které mají být provedeny ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="493de-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="493de-117">Název uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="493de-117">The name of the stored procedure.</span></span> <span data-ttu-id="493de-118">Můžete použít `Parameters` vlastnost příkazu pro přístup k vstupní a výstupní parametry a návratové hodnoty, bez ohledu na to, které `Execute` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="493de-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="493de-119">Při použití `ExecuteReader`, návratové hodnoty a výstupní parametry nebude dostupný dokud `DataReader` je zavřený.</span><span class="sxs-lookup"><span data-stu-id="493de-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="493de-120">Název tabulky.</span><span class="sxs-lookup"><span data-stu-id="493de-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="493de-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="493de-121">Example</span></span>  
 <span data-ttu-id="493de-122">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlCommand> objekt pro provedení uložené procedury nastavením jeho vlastností.</span><span class="sxs-lookup"><span data-stu-id="493de-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="493de-123">A <xref:System.Data.SqlClient.SqlParameter> objektu se používá k určení vstupní parametr uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="493de-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="493de-124">Spuštění příkazu pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody a její výstup <xref:System.Data.SqlClient.SqlDataReader> se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="493de-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="493de-125">Řešení potíží s příkazy</span><span class="sxs-lookup"><span data-stu-id="493de-125">Troubleshooting Commands</span></span>  
 <span data-ttu-id="493de-126">Zprostředkovatel dat .NET Framework pro SQL Server přidá čítačů výkonu rozpoznávat přerušované problémy související s spuštění příkazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="493de-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="493de-127">Další informace najdete v části [čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="493de-127">For more information see [Performance Counters](../../../../docs/framework/data/adonet/performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493de-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="493de-128">See also</span></span>

- [<span data-ttu-id="493de-129">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="493de-129">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="493de-130">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="493de-130">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="493de-131">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="493de-131">ADO.NET Overview</span></span>](ado-net-overview.md)
