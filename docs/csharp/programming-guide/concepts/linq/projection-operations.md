---
title: Operace projekce (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: 74792c1a58aa17c65f3a153216d50c672e0b6cf6
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411210"
---
# <a name="projection-operations-c"></a><span data-ttu-id="53402-102">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="53402-102">Projection Operations (C#)</span></span>
<span data-ttu-id="53402-103">Projekce odkazuje na operace transformace objektu na nový formulář, který často se skládá pouze z těchto vlastností, které se následně použijí.</span><span class="sxs-lookup"><span data-stu-id="53402-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="53402-104">S použitím projekce, můžete vytvořit nový typ, který je sestaven z každého objektu.</span><span class="sxs-lookup"><span data-stu-id="53402-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="53402-105">Můžete vlastnosti projektu a provádění matematických funkcí na něj.</span><span class="sxs-lookup"><span data-stu-id="53402-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="53402-106">Můžete také promítnout na původní objekt bez provedení změn.</span><span class="sxs-lookup"><span data-stu-id="53402-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="53402-107">V následující části jsou uvedeny standardní metody operátoru dotazu, které provádějí projekce.</span><span class="sxs-lookup"><span data-stu-id="53402-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53402-108">Metody</span><span class="sxs-lookup"><span data-stu-id="53402-108">Methods</span></span>  
  
|<span data-ttu-id="53402-109">Název metody</span><span class="sxs-lookup"><span data-stu-id="53402-109">Method Name</span></span>|<span data-ttu-id="53402-110">Popis</span><span class="sxs-lookup"><span data-stu-id="53402-110">Description</span></span>|<span data-ttu-id="53402-111">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="53402-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="53402-112">Další informace</span><span class="sxs-lookup"><span data-stu-id="53402-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="53402-113">Vyberte</span><span class="sxs-lookup"><span data-stu-id="53402-113">Select</span></span>|<span data-ttu-id="53402-114">Projekty hodnoty, které jsou založeny na funkce transformace.</span><span class="sxs-lookup"><span data-stu-id="53402-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="53402-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="53402-115">SelectMany</span></span>|<span data-ttu-id="53402-116">Projekty pořadí hodnot, které jsou založeny na funkce transformace a sloučí je do jedné sekvence.</span><span class="sxs-lookup"><span data-stu-id="53402-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="53402-117">Použití více `from` klauzule</span><span class="sxs-lookup"><span data-stu-id="53402-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="53402-118">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="53402-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="53402-119">Vyberte</span><span class="sxs-lookup"><span data-stu-id="53402-119">Select</span></span>  
 <span data-ttu-id="53402-120">V následujícím příkladu `select` klauzuli do projektu první písmeno každého řetězce v seznamu řetězců.</span><span class="sxs-lookup"><span data-stu-id="53402-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a><span data-ttu-id="53402-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="53402-121">SelectMany</span></span>  
 <span data-ttu-id="53402-122">Následující příklad používá více `from` klauzule do projektu všechna slova ze každý řetězec v seznamu řetězců.</span><span class="sxs-lookup"><span data-stu-id="53402-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="53402-123">Vyberte a operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="53402-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="53402-124">Práce z obou `Select()` a `SelectMany()` je výsledná hodnota (nebo hodnoty) ze zdrojové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="53402-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="53402-125">`Select()` vytvoří jednu výslednou hodnotu pro každou zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="53402-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="53402-126">Celkový výsledek je proto kolekci, která má stejný počet prvků jako zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="53402-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="53402-127">Naproti tomu `SelectMany()` jeden celkový výsledek, který obsahuje zřetězených podřízené kolekce od všech hodnot zdroje.</span><span class="sxs-lookup"><span data-stu-id="53402-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="53402-128">Funkce transformace, která je předána jako argument `SelectMany()` musí vracet vyčíslitelné posloupnost hodnot pro každou zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="53402-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="53402-129">Tyto vyčíslitelné sekvence jsou pak zřetězeny podle `SelectMany()` vytvořte jedno velké pořadí.</span><span class="sxs-lookup"><span data-stu-id="53402-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="53402-130">Následující dva obrázky ukazují konceptuální rozdíl mezi akcemi z těchto dvou metod.</span><span class="sxs-lookup"><span data-stu-id="53402-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="53402-131">V obou případech se předpokládá, že funkce selektor (transformace) vybere z každé zdrojové hodnoty pole květin.</span><span class="sxs-lookup"><span data-stu-id="53402-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="53402-132">Tento obrázek znázorňuje, jak `Select()` vrátí kolekci, která má stejný počet prvků jako zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="53402-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Obrázek znázorňující, akce Select&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="53402-134">Tento obrázek znázorňuje, jak `SelectMany()` zřetězí zprostředkující pořadí polí do jedné hodnoty konečný výsledek, který obsahuje každou hodnotu z každé zprostředkující pole.</span><span class="sxs-lookup"><span data-stu-id="53402-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![Obrázek znázorňující akce operátor SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="53402-136">Příklad kódu</span><span class="sxs-lookup"><span data-stu-id="53402-136">Code Example</span></span>  
 <span data-ttu-id="53402-137">Následující příklad porovnává chování `Select()` a `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="53402-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="53402-138">Kód vytvoří "kytice" květin díky první dvě položky z každého seznam názvů květinu ve zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="53402-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="53402-139">V tomto příkladu "jedna hodnota", který funkce transformace <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> používá, je samotný kolekci hodnot.</span><span class="sxs-lookup"><span data-stu-id="53402-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="53402-140">To vyžaduje, aby nadbytečné `foreach` smyčky, aby bylo možné vytvořit výčet každého řetězce v každé dílčí sekvenci.</span><span class="sxs-lookup"><span data-stu-id="53402-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********              
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="53402-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53402-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="53402-142">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="53402-142">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="53402-143">select – klauzule</span><span class="sxs-lookup"><span data-stu-id="53402-143">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)
- [<span data-ttu-id="53402-144">Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="53402-144">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="53402-145">Postupy: Rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="53402-145">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
