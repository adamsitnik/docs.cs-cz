---
title: Podpora klienta SqlClient pro LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 416945964af7fda5ed5aaab2f5aae1bbc8928556
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204754"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="9b00f-102">Podpora klienta SqlClient pro LocalDB</span><span class="sxs-lookup"><span data-stu-id="9b00f-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="9b00f-103">SQL Server s kódovým názvem Denali počínaje, bude k dispozici Odlehčená verze systému SQL Server LocalDB, volá.</span><span class="sxs-lookup"><span data-stu-id="9b00f-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="9b00f-104">Toto téma popisuje, jak se připojit k databázi LocalDB.</span><span class="sxs-lookup"><span data-stu-id="9b00f-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b00f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b00f-105">Remarks</span></span>  
 <span data-ttu-id="9b00f-106">Další informace o databázi LocalDB, včetně LocalDB nainstalovat a nakonfigurovat instanci LocalDB, naleznete v tématu knihy Online SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9b00f-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="9b00f-107">Slouží ke shrnutí, co můžete dělat s LocalDB:</span><span class="sxs-lookup"><span data-stu-id="9b00f-107">To summarize what you can do with LocalDB:</span></span>  
  
-   <span data-ttu-id="9b00f-108">Vytvoření a spuštění instance LocalDB s sqllocaldb.exe nebo v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="9b00f-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
-   <span data-ttu-id="9b00f-109">Pro přidání a úpravu databáze v instanci LocalDB pomocí sqlcmd.exe.</span><span class="sxs-lookup"><span data-stu-id="9b00f-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="9b00f-110">Například, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="9b00f-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
-   <span data-ttu-id="9b00f-111">Použití `AttachDBFilename` klíčové slovo připojovacího řetězce pro přidání databázi k instanci LocalDB.</span><span class="sxs-lookup"><span data-stu-id="9b00f-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="9b00f-112">Při použití `AttachDBFilename`, pokud není zadán název databáze s `Database` klíčové slovo připojovacího řetězce databáze bude nebyla odebrána od LocalDB instance, až se aplikace zavře.</span><span class="sxs-lookup"><span data-stu-id="9b00f-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="9b00f-113">V připojovacím řetězci zadejte instanci LocalDB.</span><span class="sxs-lookup"><span data-stu-id="9b00f-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="9b00f-114">Například je název vaší instance `myInstance`, připojovací řetězec bude zahrnovat:</span><span class="sxs-lookup"><span data-stu-id="9b00f-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 `User Instance=True` <span data-ttu-id="9b00f-115">Při připojení k databázi LocalDB není povolen.</span><span class="sxs-lookup"><span data-stu-id="9b00f-115">is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="9b00f-116">Můžete si stáhnout LocalDB z [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="9b00f-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="9b00f-117">Pokud použijete sqlcmd.exe upravovat data v instanci LocalDB, budete potřebovat sqlcmd ze systému SQL Server 2012, který můžete získat také z SQL Server 2012 Feature Pack.</span><span class="sxs-lookup"><span data-stu-id="9b00f-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="9b00f-118">Prostřednictvím kódu programu vytvořit pojmenovanou instanci</span><span class="sxs-lookup"><span data-stu-id="9b00f-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="9b00f-119">Aplikace můžete vytvořit pojmenovanou instanci a zadejte databázi následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9b00f-119">An application can create a named instance and specify a database as follows:</span></span>  
  
-   <span data-ttu-id="9b00f-120">Zadejte instance LocalDB následujícím způsobem vytvořte v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="9b00f-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="9b00f-121">Číslo verze instance by měla být stejná jako číslo verze instalace LocalDB.</span><span class="sxs-lookup"><span data-stu-id="9b00f-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="9b00f-122">Zadejte název instance pomocí `server` klíčové slovo připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="9b00f-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="9b00f-123">Název instance zadané v `server` klíčové slovo připojovacího řetězce musí odpovídat názvu zadanému v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="9b00f-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
-   <span data-ttu-id="9b00f-124">Použití `AttachDBFilename` klíčové slovo připojovacího řetězce k určení. Soubor MDF.</span><span class="sxs-lookup"><span data-stu-id="9b00f-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b00f-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b00f-125">See also</span></span>

- [<span data-ttu-id="9b00f-126">Funkce SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b00f-126">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [<span data-ttu-id="9b00f-127">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="9b00f-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
