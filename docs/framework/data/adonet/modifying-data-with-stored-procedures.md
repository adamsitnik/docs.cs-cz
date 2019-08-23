---
title: Úpravy dat pomocí uložených procedur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: ebf5c61010a6f658d846ed435ea3a7d18d0d3832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934440"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="cbae5-102">Úpravy dat pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="cbae5-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="cbae5-103">Uložené procedury mohou přijímat data jako vstupní parametry a mohou vracet data jako výstupní parametry, sady výsledků nebo návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cbae5-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="cbae5-104">Následující ukázka ukazuje, jak ADO.NET odesílá a přijímá vstupní parametry, výstupní parametry a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cbae5-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="cbae5-105">Příklad vloží nový záznam do tabulky, kde sloupec primárního klíče je sloupec identity v databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cbae5-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbae5-106">Pokud používáte SQL Server uložené procedury k úpravám nebo odstraňování dat pomocí <xref:System.Data.SqlClient.SqlDataAdapter>, ujistěte se, že v definici uložené procedury nepoužijete nastavení počet.</span><span class="sxs-lookup"><span data-stu-id="cbae5-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="cbae5-107">To způsobí, že počet ovlivněných řádků vrátil hodnotu nula, což `DataAdapter` interpretuje jako konflikt souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="cbae5-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="cbae5-108">V tomto případě <xref:System.Data.DBConcurrencyException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="cbae5-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbae5-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbae5-109">Example</span></span>  
 <span data-ttu-id="cbae5-110">Ukázka používá následující uloženou proceduru k vložení nové kategorie do tabulky kategorií **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="cbae5-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="cbae5-111">Uložená procedura převezme hodnotu ve sloupci **CategoryName** jako vstupní parametr a pomocí funkce SCOPE_IDENTITY () načte novou hodnotu pole identity, **KódKategorie**a vrátí ji do výstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="cbae5-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="cbae5-112">Příkaz return pomocí funkce @@ROWCOUNT vrátí počet vložených řádků.</span><span class="sxs-lookup"><span data-stu-id="cbae5-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="cbae5-113">Následující příklad kódu používá `InsertCategory` uloženou proceduru uvedenou výše jako zdroj <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> pro <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="cbae5-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="cbae5-114">Výstupní parametr se projeví <xref:System.Data.DataSet> v poté, co byl záznam vložen `Update` do databáze <xref:System.Data.SqlClient.SqlDataAdapter> při volání metody. `@Identity`</span><span class="sxs-lookup"><span data-stu-id="cbae5-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="cbae5-115">Kód také načte vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cbae5-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbae5-116">Při použití <xref:System.Data.OleDb.OleDbDataAdapter>, je nutné zadat parametry <xref:System.Data.ParameterDirection> s parametrem **ReturnValue** před jinými parametry.</span><span class="sxs-lookup"><span data-stu-id="cbae5-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cbae5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbae5-117">See also</span></span>

- [<span data-ttu-id="cbae5-118">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cbae5-118">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="cbae5-119">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="cbae5-119">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="cbae5-120">Spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="cbae5-120">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)
- [<span data-ttu-id="cbae5-121">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="cbae5-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
