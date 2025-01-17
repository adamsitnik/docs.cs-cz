---
title: Využívání kanálů OData z pracovního postupu – WF
ms.date: 03/30/2017
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
ms.openlocfilehash: e7cfa138a01719988586f9dce0a9009bea643076
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989757"
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Využívání kanálů OData z pracovního postupu

WCF Data Services je součást .NET Framework, která umožňuje vytvořit služby, které používají protokol OData (Open Data Protocol) k vystavení a zpracování dat prostřednictvím webu nebo intranetu pomocí sémantiky opětovného přenosu stavu (REST). OData zpřístupňuje data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI. Každá aplikace může komunikovat s datovou službou OData, pokud může odeslat požadavek HTTP a zpracovat datový kanál OData, který vrátí datová služba. Kromě toho WCF Data Services obsahuje klientské knihovny, které poskytují bohatší programovací prostředí při využívání kanálů OData z aplikací .NET Framework. Toto téma poskytuje přehled o tom, jak používat kanál OData v pracovním postupu s a bez použití klientských knihoven.

## <a name="using-the-sample-northwind-odata-service"></a>Použití ukázkové služby OData Northwind

Příklady v tomto tématu používají ukázkovou datovou službu Northwind v <https://services.odata.org/Northwind/Northwind.svc/>umístění. Tato služba je k dispozici jako součást [sady OData SDK](https://go.microsoft.com/fwlink/?LinkID=185248) a poskytuje přístup jen pro čtení k ukázkové databázi Northwind. Pokud je požadován přístup pro zápis nebo pokud potřebujete místní datovou službu WCF, můžete postupovat podle kroků v [rychlém startu WCF Data Services](https://go.microsoft.com/fwlink/?LinkID=131076) a vytvořit místní službu OData, která poskytuje přístup k databázi Northwind. Pokud budete postupovat podle pokynů v rychlém startu, nahraďte místní identifikátor URI pro ten, který je uveden v příkladu kódu v tomto tématu.

## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>Spotřebovávání datového kanálu OData pomocí klientských knihoven

WCF Data Services obsahuje klientské knihovny, které vám umožní snadněji využívat informační kanál OData z .NET Framework a klientských aplikací. Tyto knihovny zjednodušují posílání a přijímání zpráv HTTP. Také přeloží datovou část zprávy na objekty CLR, které představují data entity. Klientské knihovny funkce jsou dvě základní třídy <xref:System.Data.Services.Client.DataServiceContext> a. <xref:System.Data.Services.Client.DataServiceQuery%601> Tyto třídy vám umožní dotazovat se na datovou službu a pak pracovat s vrácenými daty entity jako s objekty CLR. Tato část obsahuje dva přístupy k vytváření aktivit, které používají klientské knihovny.

### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>Přidání odkazu na službu do datové služby WCF

K vygenerování klientských knihoven Northwind můžete použít dialogové okno **Přidat odkaz na službu** v aplikaci Visual Studio 2012 k přidání odkazu na službu Northwind OData.

![Snímek obrazovky zobrazující dialog Přidat odkaz na službu](./media/consuming-odata-feeds-from-a-workflow/add-service-reference-dialog.gif)

Upozorňujeme, že služba nezveřejňuje žádné operace s službami a v seznamu **služeb** jsou položky, které představují entity vystavené službou Northwind data Service. Při přidání odkazu na službu se pro tyto entity vygenerují třídy a dají se použít v kódu klienta. Příklady v tomto tématu používají tyto třídy a `NorthwindEntities` třídu k provádění dotazů.

> [!NOTE]
> Další informace naleznete v tématu [generování klientské knihovny datové služby (WCF Data Services)](../data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

### <a name="using-asynchronous-methods"></a>Použití asynchronních metod

Pro řešení možných potíží s latencí, ke kterým může dojít při přístupu k prostředkům přes web, doporučujeme WCF Data Services asynchronně přistupovat. Klientské knihovny WCF Data Services obsahují asynchronní metody pro vyvolání dotazů a programovací model Windows Workflow Foundation (WF) poskytuje <xref:System.Activities.AsyncCodeActivity> třídu pro vytváření asynchronních aktivit. <xref:System.Activities.AsyncCodeActivity>odvozené aktivity lze zapsat pro využití výhod .NET Framework třídy, které mají asynchronní metody, nebo kód, který má být proveden asynchronně, lze převést do metody a vyvolat pomocí delegáta. Tato část obsahuje dva příklady <xref:System.Activities.AsyncCodeActivity> odvozené aktivity; jeden, který používá asynchronní metody WCF Data Services klientských knihoven a druhý, který používá delegáta.

> [!NOTE]
> Další informace naleznete v tématu [asynchronní operace (WCF Data Services)](../data/wcf/asynchronous-operations-wcf-data-services.md) a [Vytváření asynchronních aktivit](creating-asynchronous-activities-in-wf.md).

### <a name="using-client-library-asynchronous-methods"></a>Použití asynchronních metod klientské knihovny

Třída poskytuje <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> a<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody pro asynchronní dotazování na službu OData. <xref:System.Data.Services.Client.DataServiceQuery%601> Tyto metody lze volat z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> přepsání <xref:System.Activities.AsyncCodeActivity> odvozené třídy. Pokud přepsání vrátí, může pracovní postup přejít nečinný (ale ne zachovat) a po dokončení <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> asynchronní práce je vyvolána modulem runtime. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> <xref:System.Activities.AsyncCodeActivity>

V následujícím příkladu `OrdersByCustomer` je definována aktivita, která má dva vstupní argumenty. Argument představuje zákazníka, který určuje, které objednávky se mají vrátit, `ServiceUri` a argument představuje identifikátor URI služby OData, pro který se má dotazovat. `CustomerId` Vzhledem k tomu, že aktivita `AsyncCodeActivity<IEnumerable<Order>>` odvozená z je <xref:System.Activities.Activity%601.Result%2A> také výstupním argumentem, který se používá k vrácení výsledků dotazu. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Přepsání vytvoří dotaz LINQ, který vybere všechny objednávky zadaného zákazníka. Tento dotaz je zadán jako <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> z předaného <xref:System.Activities.AsyncCodeActivityContext> <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> a následně je volána metoda dotazu. Všimněte si, že zpětné volání a stav, které jsou předány <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> do dotazu, jsou ty, které jsou předány <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> metodě aktivity. Po dokončení zpracování dotazu je vyvolána <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metoda aktivity. Dotaz je načten z rozhraní <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>a následně je volána <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> Metoda dotazu. Tato metoda vrátí <xref:System.Collections.Generic.IEnumerable%601> ze zadaného typu entity, v tomto případě `Order`. Vzhledem `IEnumerable<Order>` <xref:System.Collections.IEnumerable> k tomu,<xref:System.Activities.AsyncCodeActivity%601>že je obecný typ, je tato možnost nastavena jako aktivita.<xref:System.Activities.OutArgument%601> <xref:System.Activities.Activity%601.Result%2A>

[!code-csharp[CFX_WCFDataServicesActivityExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]

V následujícím příkladu `OrdersByCustomer` aktivita načte seznam objednávek pro zadaného zákazníka a <xref:System.Activities.Statements.ForEach%601> potom aktivita vytvoří výčet vrácených objednávek a zapíše datum jednotlivých objednávek do konzoly.

[!code-csharp[CFX_WCFDataServicesActivityExample#10](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]

Při vyvolání tohoto pracovního postupu jsou do konzoly zapsána následující data:

```console
Calling WCF Data Service...
8/25/1997
10/3/1997
10/13/1997
1/15/1998
3/16/1998
4/9/1998
```

> [!NOTE]
> Pokud nelze navázat připojení k serveru OData, získáte výjimku podobnou této výjimce:
>
> Neošetřená výjimka: System.InvalidOperationException: Při zpracování této žádosti došlo k chybě. ---> System .NET. WebException: Nelze se připojit ke vzdálenému serveru---> System .NET. Sockets. SocketException: Pokus o připojení se nezdařil, protože připojená strana nereagovala po určitém časovém intervalu správně nebo navázáno připojení selhalo, protože se nepovedlo odpovědět připojenému hostiteli.

Pokud je požadováno jakékoli další zpracování dat vrácených dotazem, je možné je provést v <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> přepsání aktivity. <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> A<xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> jsou vyvolány pomocí vlákna pracovního postupu a jakýkoliv kód v těchto přepisech neběží asynchronně. Pokud je další zpracování rozsáhlých nebo dlouhotrvajících, nebo jsou výsledky dotazu stránkované, měli byste zvážit přístup popsaný v následující části, který používá delegáta k provedení dotazu a asynchronní provádění dalších zpracování.

### <a name="using-a-delegate"></a>Použití delegáta

Kromě vyvolání asynchronní metody .NET Framework třídy <xref:System.Activities.AsyncCodeActivity>může aktivita založená také definovat asynchronní logiku v jedné z jeho metod. Tato metoda je určena pomocí delegáta v <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> přepsání aktivity. Když se metoda vrátí, modul runtime vyvolá <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> přepsání aktivity. Při volání služby OData z pracovního postupu lze tuto metodu použít k dotazování služby a k poskytnutí dalšího zpracování.

V následujícím příkladu `ListCustomers` je definována aktivita. Tato aktivita se dotazuje na ukázkovou datovou službu `List<Customer>` Northwind a vrátí, která obsahuje všechny zákazníky v databázi Northwind. Asynchronní práce je prováděna `GetCustomers` metodou. Tato metoda se dotazuje služby pro všechny zákazníky a pak je zkopíruje do `List<Customer>`. Pak zkontroluje, jestli jsou výsledky stránkované. V takovém případě se dotazuje služby na další stránku výsledků, přidá je do seznamu a pokračuje, dokud nebudou načtena všechna zákaznická data.

> [!NOTE]
> Další informace o stránkování v WCF Data Services naleznete v tématu [How to: Načte stránkované výsledky (WCF Data Services)](../data/wcf/how-to-load-paged-results-wcf-data-services.md).

Po přidání všech zákazníků se seznam vrátí. Metoda je určena v <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> přepsání aktivity. `GetCustomers` Vzhledem k tomu, že metoda má návratovou `Func<string, List<Customer>>` hodnotu, je vytvořena pro určení metody.

> [!NOTE]
> Pokud metoda, která provádí asynchronní práci, nemá návratovou hodnotu, <xref:System.Action> použije se místo. <xref:System.Func%601> Příklady vytvoření asynchronního příkladu pomocí obou přístupů naleznete v tématu [Vytváření asynchronních aktivit](creating-asynchronous-activities-in-wf.md).

Tato <xref:System.Func%601> metoda je přiřazena <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>k a `BeginInvoke` je volána. Vzhledem k tomu, že metoda, která má být vyvolána, nemá přístup k prostředí aktivity argumentů, hodnota `ServiceUri` argumentu je předána jako první parametr spolu s zpětným voláním a stavem, které byly předány do. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Při `GetCustomers` návratu<xref:System.Activities.AsyncCodeActivity.EndExecute%2A>vyvolá modul runtime. Kód v <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> načte delegáta <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>z volání `EndInvoke`funkce a vrátí výsledek, který `GetCustomers` je seznam zákazníků vrácených z metody.

[!code-csharp[CFX_WCFDataServicesActivityExample#200](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]

V následujícím příkladu `ListCustomers` aktivita načte seznam zákazníků a <xref:System.Activities.Statements.ForEach%601> potom ji vytvoří a zapíše název společnosti a kontaktní jméno každého zákazníka do konzoly.

[!code-csharp[CFX_WCFDataServicesActivityExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]

Při vyvolání tohoto pracovního postupu se do konzoly zapisují následující data. Vzhledem k tomu, že tento dotaz vrací mnoho zákazníků, zobrazí se zde pouze část výstupu.

```console
Calling WCF Data Service...
Alfreds Futterkiste, Contact: Maria Anders
Ana Trujillo Emparedados y helados, Contact: Ana Trujillo
Antonio Moreno Taquería, Contact: Antonio Moreno
Around the Horn, Contact: Thomas Hardy
Berglunds snabbköp, Contact: Christina Berglund
...
```

## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>Spotřebovávání datového kanálu OData bez použití klientských knihoven

OData zpřístupňuje data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI. Když použijete klientské knihovny, tyto identifikátory URI se vytvoří za vás, ale nemusíte používat klientské knihovny. V případě potřeby lze ke službě OData získat přímý pøístup bez použití klientských knihoven. Pokud nepoužíváte klientské knihovny, umístění služby a požadovaná data jsou určena identifikátorem URI a výsledky se vrátí v reakci na požadavek HTTP. Tato nezpracovaná data pak můžete zpracovat nebo manipulovat požadovaným způsobem. Jedním ze způsobů, jak načíst výsledky dotazu OData, je použití <xref:System.Net.WebClient> třídy. V tomto příkladu se načte název kontaktu zákazníka reprezentovaný službou Key ALFKI.

[!code-csharp[CFX_WCFDataServicesActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]

Při spuštění tohoto kódu se v konzole zobrazí následující výstup:

```console
Raw data returned:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<ContactName xmlns="http://schemas.microsoft.com/ado/2007/08/dataservices">Maria Anders</ContactName>
```

V pracovním postupu může být kód z tohoto příkladu začleněn do <xref:System.Activities.CodeActivity.Execute%2A> přepsání <xref:System.Activities.CodeActivity>vlastní aktivity založené na základě, ale stejné funkce lze také provést pomocí <xref:System.Activities.Expressions.InvokeMethod%601> aktivity. <xref:System.Activities.Expressions.InvokeMethod%601> Aktivita umožňuje autorům pracovních postupů vyvolat statické a instanční metody třídy a má také možnost asynchronní vyvolání zadané metody. V následujícím příkladu <xref:System.Activities.Expressions.InvokeMethod%601> je aktivita nakonfigurována pro <xref:System.Net.WebClient.DownloadString%2A> volání metody <xref:System.Net.WebClient> třídy a vrácení seznamu zákazníků.

[!code-csharp[CFX_WCFDataServicesActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]

<xref:System.Activities.Expressions.InvokeMethod%601>může volat statické a instanční metody třídy. Vzhledem <xref:System.Net.WebClient.DownloadString%2A> k tomu, že je metoda <xref:System.Net.WebClient> instance třídy, je pro <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>třídu zadána <xref:System.Net.WebClient> nová instance třídy. `DownloadString`je určena jako <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, identifikátor URI, který obsahuje dotaz, je určen <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> v kolekci a návratová <xref:System.Activities.Activity%601.Result%2A> hodnota je přiřazena k hodnotě. Hodnota je nastavena na `true`, což znamená, že volání metody bude spuštěno asynchronně s ohledem na pracovní postup. <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> V následujícím příkladu je vytvořen pracovní postup, který používá <xref:System.Activities.Expressions.InvokeMethod%601> aktivitu pro dotaz na ukázkovou datovou službu Northwind pro konkrétního zákazníka a následně vracená data jsou zapsána do konzoly.

[!code-csharp[CFX_WCFDataServicesActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]

Při vyvolání tohoto pracovního postupu se do konzoly zobrazí následující výstup. Vzhledem k tomu, že tento dotaz vrátí několik objednávek, zobrazí se zde pouze část výstupu.

```console
Calling WCF Data Service...
Raw data returned:

<?xml version="1.0" encoding="utf-8" standalone="yes"?>*
<feed
xml:base="http://services.odata.org/Northwind/Northwind.svc/"
xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices"
xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"
xmlns="http://www.w3.org/2005/Atom">
<title type="text">Orders\</title>
<id>http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders\</id>
<updated>2010-05-19T19:37:07Z\</updated>
<link rel="self" title="Orders" href="Orders" />
<entry>
<id>http://services.odata.org/Northwind/Northwind.svc/Orders(10643)\</id>
<title type="text">\</title>
<updated>2010-05-19T19:37:07Z\</updated>
<author>
<name />
</author>
<link rel="edit" title="Order" href="Orders(10643)" />
<link rel="http://schemas.microsoft.com/ado/2007/08/dataservices/related/Customer" type="application/atom+xml;type=entry" title="Customer" href="Orders(10643)/Customer" />
...
```

Tento příklad poskytuje jednu metodu, kterou autoři aplikace pracovní postupy můžou použít ke využívání nezpracovaných dat vrácených ze služby OData. Další informace o přístupu WCF Data Services pomocí identifikátorů URI najdete v tématu [přístup k prostředkům datové služby (WCF Data Services)](../data/wcf/accessing-data-service-resources-wcf-data-services.md) a [OData: Konvence](https://go.microsoft.com/fwlink/?LinkId=185564)identifikátoru URI.
