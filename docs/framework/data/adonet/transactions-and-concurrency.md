---
title: Transakce a souběžnost
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: c78031150d9b1209372dece49813dfcf0a03b9d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965215"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="25adf-102">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="25adf-102">Transactions and Concurrency</span></span>
<span data-ttu-id="25adf-103">Transakce se skládá z jednoho příkazu nebo skupiny příkazů, které se spouštějí jako balíček.</span><span class="sxs-lookup"><span data-stu-id="25adf-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="25adf-104">Transakce umožňují zkombinovat více operací do jedné pracovní jednotky.</span><span class="sxs-lookup"><span data-stu-id="25adf-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="25adf-105">Pokud dojde k selhání v jednom bodě transakce, všechny aktualizace mohou být vráceny zpět do jejich stavu před transakcí.</span><span class="sxs-lookup"><span data-stu-id="25adf-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="25adf-106">Transakce musí odpovídat vlastnostem kyseliny – nedělitelnost, konzistence, izolaci a odolnost, aby se zajistila konzistence dat.</span><span class="sxs-lookup"><span data-stu-id="25adf-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="25adf-107">Většina relačních databázových systémů, jako je například Microsoft SQL Server, podporuje transakce, které poskytují funkce pro správu uzamčení, protokolování a transakcí pokaždé, když klientská aplikace provede operaci aktualizace, vložení nebo odstranění.</span><span class="sxs-lookup"><span data-stu-id="25adf-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25adf-108">Pokud se zámky uchovávají příliš dlouho, můžou transakce, které zahrnují víc prostředků, snížit souběžnost.</span><span class="sxs-lookup"><span data-stu-id="25adf-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="25adf-109">Proto Udržujte transakce co nejkratší.</span><span class="sxs-lookup"><span data-stu-id="25adf-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="25adf-110">Pokud transakce zahrnuje více tabulek ve stejné databázi nebo serveru, pak jsou explicitní transakce v uložených procedurách často lepší.</span><span class="sxs-lookup"><span data-stu-id="25adf-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="25adf-111">Transakce lze vytvořit v SQL Server uložených procedurách pomocí příkazů Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`a `ROLLBACK TRANSACTION` .</span><span class="sxs-lookup"><span data-stu-id="25adf-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="25adf-112">Další informace najdete v tématu SQL Server Knihy online.</span><span class="sxs-lookup"><span data-stu-id="25adf-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="25adf-113">Transakce týkající se různých správců prostředků, jako je například transakce mezi SQL Server a Oracle, vyžadují distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="25adf-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="25adf-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="25adf-114">In This Section</span></span>  
 [<span data-ttu-id="25adf-115">Místní transakce</span><span class="sxs-lookup"><span data-stu-id="25adf-115">Local Transactions</span></span>](../../../../docs/framework/data/adonet/local-transactions.md)  
 <span data-ttu-id="25adf-116">Ukazuje, jak provádět transakce v databázi.</span><span class="sxs-lookup"><span data-stu-id="25adf-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="25adf-117">Distribuované transakce</span><span class="sxs-lookup"><span data-stu-id="25adf-117">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 <span data-ttu-id="25adf-118">Popisuje, jak provádět distribuované transakce v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="25adf-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="25adf-119">Integrace System.Transactions s SQL Serverem</span><span class="sxs-lookup"><span data-stu-id="25adf-119">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="25adf-120">Popisuje <xref:System.Transactions> integraci s SQL Server pro práci s distribuovanými transakcemi.</span><span class="sxs-lookup"><span data-stu-id="25adf-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="25adf-121">Optimistická metoda souběžného zpracování</span><span class="sxs-lookup"><span data-stu-id="25adf-121">Optimistic Concurrency</span></span>](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 <span data-ttu-id="25adf-122">Popisuje optimistickou a pesimistickou souběžnost a způsob testování pro souběhy souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="25adf-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25adf-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25adf-123">See also</span></span>

- [<span data-ttu-id="25adf-124">Principy transakcí</span><span class="sxs-lookup"><span data-stu-id="25adf-124">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)
- [<span data-ttu-id="25adf-125">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="25adf-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="25adf-126">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="25adf-126">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="25adf-127">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="25adf-127">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="25adf-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="25adf-128">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [<span data-ttu-id="25adf-129">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="25adf-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
