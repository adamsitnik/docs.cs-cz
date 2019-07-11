---
title: Objekty a třídy v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: dd2968f7ab528fa07ef0c5af85f2a7f07147a76e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755164"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="e14e6-102">Objekty a třídy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e14e6-102">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="e14e6-103">*Objekt* je kombinací kód a data, která lze považovat za jednotku.</span><span class="sxs-lookup"><span data-stu-id="e14e6-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="e14e6-104">Objekt může být část aplikace, jako je ovládací prvek nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="e14e6-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="e14e6-105">Objekt může být také celé aplikace.</span><span class="sxs-lookup"><span data-stu-id="e14e6-105">An entire application can also be an object.</span></span>

<span data-ttu-id="e14e6-106">Když vytvoříte aplikaci v jazyce Visual Basic, neustále práci s objekty.</span><span class="sxs-lookup"><span data-stu-id="e14e6-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="e14e6-107">Objekty poskytnuté jazyka Visual Basic, jako je například přístup k objektům ovládacích prvků formulářů a data se dají použít.</span><span class="sxs-lookup"><span data-stu-id="e14e6-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="e14e6-108">Objekty z jiných aplikací můžete použít taky v rámci vaší aplikace v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e14e6-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="e14e6-109">Dokonce je možné vytvářet vlastní objekty a definovat další vlastnosti a metody pro ně.</span><span class="sxs-lookup"><span data-stu-id="e14e6-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="e14e6-110">Objekty fungují jako stavební bloky pro programy prefabrikované – umožňují napsat kód jednou a opakovaně používat pořád dokola.</span><span class="sxs-lookup"><span data-stu-id="e14e6-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="e14e6-111">Toto téma popisuje objekty podrobně.</span><span class="sxs-lookup"><span data-stu-id="e14e6-111">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="e14e6-112">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="e14e6-112">Objects and classes</span></span>

<span data-ttu-id="e14e6-113">Každý objekt v jazyce Visual Basic je definován *třídy*.</span><span class="sxs-lookup"><span data-stu-id="e14e6-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="e14e6-114">Třída popisuje proměnné, vlastnosti, procedury a události objektu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="e14e6-115">Objekty jsou instancemi třídy; můžete vytvořit libovolný počet objektů, které je nutné po definování třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="e14e6-116">Informace o tom vztah mezi objektem a své třídy, si můžete Představte řezačky souboru cookie a soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="e14e6-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="e14e6-117">Ořezávání soubor cookie je třída.</span><span class="sxs-lookup"><span data-stu-id="e14e6-117">The cookie cutter is the class.</span></span> <span data-ttu-id="e14e6-118">Definuje vlastnosti každého souboru cookie, třeba velikost a tvar.</span><span class="sxs-lookup"><span data-stu-id="e14e6-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="e14e6-119">Třída se používá k vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="e14e6-119">The class is used to create objects.</span></span> <span data-ttu-id="e14e6-120">Objekty jsou soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="e14e6-120">The objects are the cookies.</span></span>

<span data-ttu-id="e14e6-121">Objekt musíte vytvořit předtím, než může přistupovat k jejím členům.</span><span class="sxs-lookup"><span data-stu-id="e14e6-121">You must create an object before you can access its members.</span></span>

### <a name="to-create-an-object-from-a-class"></a><span data-ttu-id="e14e6-122">Chcete-li vytvořit objekt ze třídy</span><span class="sxs-lookup"><span data-stu-id="e14e6-122">To create an object from a class</span></span>

1. <span data-ttu-id="e14e6-123">Určení, z které třídy, kterou chcete vytvořit objekt.</span><span class="sxs-lookup"><span data-stu-id="e14e6-123">Determine from which class you want to create an object.</span></span>

2. <span data-ttu-id="e14e6-124">Zápis [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) vytvoření proměnné, ke kterému lze přiřadit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-124">Write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="e14e6-125">Proměnné by měl být typu požadovanou třídu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-125">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As customer
   ```

3. <span data-ttu-id="e14e6-126">Přidat [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo inicializace proměnné do nové instance třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-126">Add the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New customer
   ```

4. <span data-ttu-id="e14e6-127">Členy třídy nyní přístupné prostřednictvím proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-127">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="e14e6-128">Kdykoli je to možné, by měla deklarovat proměnnou typu třídy, kterou chcete přiřadit k ní.</span><span class="sxs-lookup"><span data-stu-id="e14e6-128">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="e14e6-129">Tento postup se nazývá *časné vazby*.</span><span class="sxs-lookup"><span data-stu-id="e14e6-129">This is called *early binding*.</span></span> <span data-ttu-id="e14e6-130">Pokud si nejste jisti třídy typu v době kompilace, můžete vyvolat *pozdní vazby* deklarováním proměnné bude [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e14e6-130">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="e14e6-131">Ale pozdní vazby můžete provádět pomalejší výkon a omezit přístup k členům run-time objekt.</span><span class="sxs-lookup"><span data-stu-id="e14e6-131">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="e14e6-132">Další informace najdete v tématu [deklarace proměnné objektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e14e6-132">For more information, see [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="e14e6-133">Více instancí</span><span class="sxs-lookup"><span data-stu-id="e14e6-133">Multiple instances</span></span>

<span data-ttu-id="e14e6-134">Objekty nově vytvořené ze třídy jsou často identické k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="e14e6-134">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="e14e6-135">Jakmile existují jako jednotlivé objekty, ale jejich proměnných a vlastností můžete změnit nezávisle na ostatních instancí.</span><span class="sxs-lookup"><span data-stu-id="e14e6-135">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="e14e6-136">Například pokud přidáte tři políčka na formulář, každý objekt zaškrtávací políčko je instance <xref:System.Windows.Forms.CheckBox> třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-136">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="e14e6-137">Jednotlivé <xref:System.Windows.Forms.CheckBox> objekty sdílejí společnou sadu vlastností a možnosti (vlastnosti, proměnné, procedury a události) určené třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-137">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="e14e6-138">Ale každý má svůj vlastní název, můžete samostatně povolit a zakázané a je možné použít v jiném umístění ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="e14e6-138">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="e14e6-139">Členové objektu</span><span class="sxs-lookup"><span data-stu-id="e14e6-139">Object members</span></span>

<span data-ttu-id="e14e6-140">Element aplikace, je objekt reprezentující *instance* třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-140">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="e14e6-141">Pole, vlastnosti, metody a události jsou stavebními bloky objektů a představují jejich *členy*.</span><span class="sxs-lookup"><span data-stu-id="e14e6-141">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="e14e6-142">Přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="e14e6-142">Member Access</span></span>

<span data-ttu-id="e14e6-143">Přístup ke členu objektu tak, že zadáte název proměnné objektu v pořadí, tečku (`.`) a název členu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-143">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="e14e6-144">Následující příklad nastaví <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Label> objektu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-144">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="e14e6-145">Technologie IntelliSense seznam členů</span><span class="sxs-lookup"><span data-stu-id="e14e6-145">IntelliSense listing of members</span></span>

<span data-ttu-id="e14e6-146">Technologie IntelliSense uvádí členy třídy při vyvolání jeho členů seznamu možnost, například když zadáte tečku (`.`) jako operátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="e14e6-146">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="e14e6-147">Pokud zadáte tečku za název proměnné deklarované jako instance této třídy, IntelliSense vypíše všechny členy instance a žádné sdílené členy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-147">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="e14e6-148">Pokud zadáte tečku samotný název třídy, IntelliSense vypíše všechny sdílené členy a žádné členy instance.</span><span class="sxs-lookup"><span data-stu-id="e14e6-148">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="e14e6-149">Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="e14e6-149">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="e14e6-150">Pole a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e14e6-150">Fields and properties</span></span>

<span data-ttu-id="e14e6-151">*Pole* a *vlastnosti* představují informace uložené v objektu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-151">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="e14e6-152">Načíst a nastavit jejich hodnoty pomocí přiřazovací příkazy stejným způsobem jako načíst a nastavit místní proměnné v postupu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-152">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="e14e6-153">Následující příklad načte <xref:System.Windows.Forms.Control.Width%2A> vlastnost a nastaví <xref:System.Windows.Forms.Control.ForeColor%2A> vlastnost <xref:System.Windows.Forms.Label> objektu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-153">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="e14e6-154">Všimněte si, že se také nazývá pole *členskou proměnnou*.</span><span class="sxs-lookup"><span data-stu-id="e14e6-154">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="e14e6-155">Použijte vlastnost postupy při:</span><span class="sxs-lookup"><span data-stu-id="e14e6-155">Use property procedures when:</span></span>

- <span data-ttu-id="e14e6-156">Je nutné určit, kdy a jak je nastavit nebo načíst hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-156">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="e14e6-157">Vlastnost má kvalitně definované sady hodnot, které je potřeba ověřit.</span><span class="sxs-lookup"><span data-stu-id="e14e6-157">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="e14e6-158">Nastavením této hodnoty způsobí, že některé postřehnutelné změny ve stavu objektu, například `IsVisible` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e14e6-158">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="e14e6-159">Nastavení vlastnosti způsobí, že změny na jiné interní proměnné nebo na hodnotách jiných vlastností.</span><span class="sxs-lookup"><span data-stu-id="e14e6-159">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="e14e6-160">Před vlastnost můžete nastavit nebo načíst, je nutné provést sadu kroků.</span><span class="sxs-lookup"><span data-stu-id="e14e6-160">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="e14e6-161">Použití polí při:</span><span class="sxs-lookup"><span data-stu-id="e14e6-161">Use fields when:</span></span>

- <span data-ttu-id="e14e6-162">Hodnota je držitelem ověřování typu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-162">The value is of a self-validating type.</span></span> <span data-ttu-id="e14e6-163">Například chyby nebo převod automatické dat v případě jinou hodnotu než `True` nebo `False` je přiřazen `Boolean` proměnné.</span><span class="sxs-lookup"><span data-stu-id="e14e6-163">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="e14e6-164">Libovolná hodnota v rozsahu podporovaném parametrem datový typ je platný.</span><span class="sxs-lookup"><span data-stu-id="e14e6-164">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="e14e6-165">To platí pro mnoho vlastností typu `Single` nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="e14e6-165">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="e14e6-166">Vlastnost je `String` datový typ a neexistuje žádné omezení velikosti nebo hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="e14e6-166">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="e14e6-167">Další informace najdete v tématu [procedury vlastnosti](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e14e6-167">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

### <a name="methods"></a><span data-ttu-id="e14e6-168">Metody</span><span class="sxs-lookup"><span data-stu-id="e14e6-168">Methods</span></span>

<span data-ttu-id="e14e6-169">A *metoda* je akce, které může objekt provádět.</span><span class="sxs-lookup"><span data-stu-id="e14e6-169">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="e14e6-170">Například <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> je metoda <xref:System.Windows.Forms.ComboBox> objekt, který přidá nový záznam do pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="e14e6-170">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="e14e6-171">Následující příklad ukazuje <xref:System.Windows.Forms.Timer.Start%2A> metodu <xref:System.Windows.Forms.Timer> objektu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-171">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="e14e6-172">Všimněte si, že metoda je jednoduše *postup* , který je zveřejněný prostřednictvím objektu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-172">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="e14e6-173">Další informace najdete v tématu [postupy](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span><span class="sxs-lookup"><span data-stu-id="e14e6-173">For more information, see [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="e14e6-174">Události</span><span class="sxs-lookup"><span data-stu-id="e14e6-174">Events</span></span>

<span data-ttu-id="e14e6-175">Událost je akce rozpoznána v objektu, jako je například kliknutí myší nebo stisknutí klávesy a pro která můžete napsat kód reagovat.</span><span class="sxs-lookup"><span data-stu-id="e14e6-175">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="e14e6-176">Události může dojít v důsledku akcí uživatele nebo kódu programu, nebo může být způsobeno systému.</span><span class="sxs-lookup"><span data-stu-id="e14e6-176">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="e14e6-177">Kód, který signalizuje událost se říká, že *vyvolat* událostí a kód, který reaguje na něj se říká, že *zpracování* ho.</span><span class="sxs-lookup"><span data-stu-id="e14e6-177">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="e14e6-178">Můžete také vyvíjet vlastní události vyvolané službou objekty a zpracovány jinými objekty.</span><span class="sxs-lookup"><span data-stu-id="e14e6-178">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="e14e6-179">Další informace najdete v tématu [události](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="e14e6-179">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="e14e6-180">Členy instance a sdílené členy</span><span class="sxs-lookup"><span data-stu-id="e14e6-180">Instance members and shared members</span></span>

<span data-ttu-id="e14e6-181">Když vytvoříte objekt ze třídy, výsledkem je instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-181">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="e14e6-182">Členy, které nejsou deklarovány s [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) – klíčové slovo se *členy instance*, které patří výhradně pro tuto konkrétní instanci.</span><span class="sxs-lookup"><span data-stu-id="e14e6-182">Members that are not declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="e14e6-183">Člen instance. v jedné instanci je nezávislá na stejný člen v jiná instance stejné třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-183">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="e14e6-184">Členskou proměnnou instance například může mít různé hodnoty v různých instancích.</span><span class="sxs-lookup"><span data-stu-id="e14e6-184">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="e14e6-185">Členy deklarované s `Shared` – klíčové slovo se *sdílené členy*, který patří do třídy jako celek a ne do jakékoli určité instance.</span><span class="sxs-lookup"><span data-stu-id="e14e6-185">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="e14e6-186">Sdílenému členu existuje pouze jednou, bez ohledu na to, kolik instancí své třídy vytvoříte, nebo i v případě, že vytvoříte žádné instance.</span><span class="sxs-lookup"><span data-stu-id="e14e6-186">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="e14e6-187">Proměnná sdílenému členu, například má pouze jednu hodnotu, která je k dispozici pro veškerý kód, který může přistupovat k třídě.</span><span class="sxs-lookup"><span data-stu-id="e14e6-187">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-nonshared-members"></a><span data-ttu-id="e14e6-188">Přístup k nesdílené členy</span><span class="sxs-lookup"><span data-stu-id="e14e6-188">Accessing nonshared members</span></span>

##### <a name="to-access-a-nonshared-member-of-an-object"></a><span data-ttu-id="e14e6-189">Pro přístup k nesdílené člen objektu</span><span class="sxs-lookup"><span data-stu-id="e14e6-189">To access a nonshared member of an object</span></span>

1. <span data-ttu-id="e14e6-190">Ujistěte se, že objekt byl vytvořen ze své třídy a přiřazen do proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-190">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="e14e6-191">V příkazu, který přistupuje k členu, postupujte podle názvu proměnné objektu s *operátor přístup člena* (`.`) a potom název člena.</span><span class="sxs-lookup"><span data-stu-id="e14e6-191">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="e14e6-192">Přístup ke sdílené členy</span><span class="sxs-lookup"><span data-stu-id="e14e6-192">Accessing shared members</span></span>

##### <a name="to-access-a-shared-member-of-an-object"></a><span data-ttu-id="e14e6-193">Pro přístup ke sdílenému členu objektu</span><span class="sxs-lookup"><span data-stu-id="e14e6-193">To access a shared member of an object</span></span>

- <span data-ttu-id="e14e6-194">Postupujte podle názvu třídy s *operátor přístup člena* (`.`) a potom název člena.</span><span class="sxs-lookup"><span data-stu-id="e14e6-194">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="e14e6-195">Vždy byste měli přistupovat k `Shared` člen objektu přímo prostřednictvím názvu třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-195">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="e14e6-196">Pokud jste již vytvořili objekt ze třídy, případně se dostanete `Shared` člen prostřednictvím proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-196">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="e14e6-197">Rozdíly mezi třídami a moduly</span><span class="sxs-lookup"><span data-stu-id="e14e6-197">Differences between classes and modules</span></span>

<span data-ttu-id="e14e6-198">Hlavní rozdíl mezi třídami a moduly je, že třídy může být vytvořen jako objekty, zatímco standardní moduly nelze.</span><span class="sxs-lookup"><span data-stu-id="e14e6-198">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="e14e6-199">Protože existuje jenom jednu kopii standardních modulu dat při změně veřejné proměnné v modulu standardních jedné části programu, získá další část programu stejnou hodnotu, pokud je pak přečte tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e14e6-199">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="e14e6-200">Naproti tomu datový objekt existuje samostatně pro každý objekt instance.</span><span class="sxs-lookup"><span data-stu-id="e14e6-200">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="e14e6-201">Další rozdíl je, že na rozdíl od standardní moduly tříd mohou implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e14e6-201">Another difference is that unlike standard modules, classes can implement interfaces.</span></span>

> [!NOTE]
> <span data-ttu-id="e14e6-202">Když `Shared` modifikátor se použijí na člen třídy, je přidružen k samotné místo konkrétní instanci třídy třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-202">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="e14e6-203">Člen lze přistupovat přímo pomocí názvu třídy, jsou přístupné stejné členy způsob, jak modul.</span><span class="sxs-lookup"><span data-stu-id="e14e6-203">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="e14e6-204">Třídy a moduly také použít jiné rámce jejich členy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-204">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="e14e6-205">Členy definované v rámci třídy mají rozsah v rámci konkrétní instanci třídy a existují jenom po dobu životnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-205">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="e14e6-206">Pro přístup ke členům třídy z mimo třídu, je nutné použít plně kvalifikované názvy ve formátu *objekt*. *Člen*.</span><span class="sxs-lookup"><span data-stu-id="e14e6-206">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="e14e6-207">Na druhé straně členy deklarované v rámci modulu jsou veřejně dostupné ve výchozím nastavení a je možný přes jakýkoli kód, který může přistupovat k modulu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-207">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="e14e6-208">To znamená, že proměnné v modulu standardních jsou účinně globální proměnné, protože jsou viditelné z kdekoli ve vašem projektu a existují po celou dobu životnosti programu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-208">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="e14e6-209">Opětovné použití tříd a objektů</span><span class="sxs-lookup"><span data-stu-id="e14e6-209">Reusing classes and objects</span></span>

<span data-ttu-id="e14e6-210">Objekty vám umožňují deklarovat proměnné a procedury jednou a pak znovu použít kdykoli je to třeba.</span><span class="sxs-lookup"><span data-stu-id="e14e6-210">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="e14e6-211">Například pokud chcete přidat kontrolu pravopisu do aplikace můžete definovat všechny proměnné a funkce pro kontrolu pravopisu nakonfigurovánu podporu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-211">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="e14e6-212">Pokud vytvoříte vaše kontroly pravopisu jako třída, můžete je znovu ji v jiných aplikacích tak, že přidáte odkaz na kompilované sestavení.</span><span class="sxs-lookup"><span data-stu-id="e14e6-212">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="e14e6-213">Ještě lepší je je možné uložit sami nějakou práci pomocí kontroly pravopisu třídu, která už někdo vyvinula.</span><span class="sxs-lookup"><span data-stu-id="e14e6-213">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="e14e6-214">Rozhraní .NET Framework poskytuje mnoho příkladů součásti, které jsou k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="e14e6-214">The .NET Framework provides many examples of components that are available for use.</span></span> <span data-ttu-id="e14e6-215">V následujícím příkladu <xref:System.TimeZone> třídy v <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e14e6-215">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="e14e6-216"><xref:System.TimeZone> obsahuje členy, které umožňují načítat informace o časovém pásmu systému aktuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="e14e6-216"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub examineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    MsgBox(s)
End Sub
```

<span data-ttu-id="e14e6-217">V předchozím příkladu první [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklaruje proměnnou objektu typu <xref:System.TimeZone> a přiřadí ji <xref:System.TimeZone> vrácený <xref:System.TimeZone.CurrentTimeZone%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e14e6-217">In the preceding example, the first [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="e14e6-218">Vztahy mezi objekty</span><span class="sxs-lookup"><span data-stu-id="e14e6-218">Relationships among objects</span></span>

<span data-ttu-id="e14e6-219">Objekty mohou být propojeny k sobě navzájem několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="e14e6-219">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="e14e6-220">Hlavní typy vztahů jsou *hierarchické* a *členství ve skupině*.</span><span class="sxs-lookup"><span data-stu-id="e14e6-220">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="e14e6-221">Hierarchický vztah</span><span class="sxs-lookup"><span data-stu-id="e14e6-221">Hierarchical relationship</span></span>

<span data-ttu-id="e14e6-222">Když jsou třídy odvozeny z více základních tříd, jejich se říká, že jste *hierarchický vztah*.</span><span class="sxs-lookup"><span data-stu-id="e14e6-222">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="e14e6-223">Hierarchie tříd jsou užitečné při popisu položky, které jsou podtyp další obecné třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-223">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="e14e6-224">V následujícím příkladu předpokládejme, že chcete definovat zvláštní druh <xref:System.Windows.Forms.Button> , že funguje jako normální <xref:System.Windows.Forms.Button> , ale také zpřístupní metodu, která obrací barvy popředí a pozadí.</span><span class="sxs-lookup"><span data-stu-id="e14e6-224">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a><span data-ttu-id="e14e6-225">Definování třídy je odvozen z již existující třídu</span><span class="sxs-lookup"><span data-stu-id="e14e6-225">To define a class is derived from an already existing class</span></span>

1. <span data-ttu-id="e14e6-226">Použití [Class – příkaz](../../../../visual-basic/language-reference/statements/class-statement.md) definování třídy, ze kterého chcete vytvořit objekt potřebujete.</span><span class="sxs-lookup"><span data-stu-id="e14e6-226">Use a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class reversibleButton
   ```

   <span data-ttu-id="e14e6-227">Ujistěte se, `End Class` příkaz následuje poslední řádek kódu ve své třídě.</span><span class="sxs-lookup"><span data-stu-id="e14e6-227">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="e14e6-228">Ve výchozím nastavení, budou automaticky generuje integrovaného vývojového prostředí (IDE) `End Class` při zadávání `Class` příkazu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-228">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="e14e6-229">Postupujte podle `Class` příkaz okamžitě [dědí příkaz](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e14e6-229">Follow the `Class` statement immediately with an [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="e14e6-230">Zadejte třídu, ze kterého vaše nová třída odvozena.</span><span class="sxs-lookup"><span data-stu-id="e14e6-230">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="e14e6-231">Nové třídy dědí všechny členy definované prostřednictvím základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-231">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="e14e6-232">Přidejte kód pro další členové vaší odvozené třídě zpřístupňuje.</span><span class="sxs-lookup"><span data-stu-id="e14e6-232">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="e14e6-233">Například můžete přidat `reverseColors` metoda a odvozené třídy může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="e14e6-233">For example, you might add a `reverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class reversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub reverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="e14e6-234">Je-li vytvořit objekt `reversibleButton` třídu, má přístup všichni členové <xref:System.Windows.Forms.Button> třídu, stejně jako `reverseColors` metoda a všemi novými členy můžete definovat na `reversibleButton`.</span><span class="sxs-lookup"><span data-stu-id="e14e6-234">If you create an object from the `reversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `reverseColors` method and any other new members you define on `reversibleButton`.</span></span>

<span data-ttu-id="e14e6-235">Odvozené třídy dědí členy třídy, které jsou založené na, vám umožňuje přidat složitost, jak budete v hierarchii tříd.</span><span class="sxs-lookup"><span data-stu-id="e14e6-235">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="e14e6-236">Další informace najdete v tématu [základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="e14e6-236">For more information, see [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

### <a name="compiling-the-code"></a><span data-ttu-id="e14e6-237">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="e14e6-237">Compiling the code</span></span>

<span data-ttu-id="e14e6-238">Ujistěte se, že kompilátor může přistupovat k třídě, ze kterého máte v úmyslu odvozovat nové třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-238">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="e14e6-239">To může znamenat plně kvalifikováním názvu, jako v předchozím příkladu, nebo při identifikaci svůj obor názvů v [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="e14e6-239">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="e14e6-240">Pokud je třída v jiném projektu, můžete potřebovat přidat odkaz na tento projekt.</span><span class="sxs-lookup"><span data-stu-id="e14e6-240">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="e14e6-241">Další informace najdete v tématu [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="e14e6-241">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="e14e6-242">Vztah členství ve skupině</span><span class="sxs-lookup"><span data-stu-id="e14e6-242">Containment relationship</span></span>

<span data-ttu-id="e14e6-243">Dalším způsobem, že můžete související objekty, je *vztah členství ve skupině*.</span><span class="sxs-lookup"><span data-stu-id="e14e6-243">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="e14e6-244">Kontejnerové objekty zapouzdřují logicky jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="e14e6-244">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="e14e6-245">Například <xref:System.OperatingSystem> logicky obsahuje objekt <xref:System.Version> objektu, který vrací přes jeho <xref:System.OperatingSystem.Version%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e14e6-245">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="e14e6-246">Všimněte si, že objekt kontejneru fyzicky neobsahuje jakýkoli jiný objekt.</span><span class="sxs-lookup"><span data-stu-id="e14e6-246">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="e14e6-247">Kolekce</span><span class="sxs-lookup"><span data-stu-id="e14e6-247">Collections</span></span>

<span data-ttu-id="e14e6-248">Jeden konkrétní typ objektu členství ve skupině je reprezentována *kolekce*.</span><span class="sxs-lookup"><span data-stu-id="e14e6-248">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="e14e6-249">Kolekce jsou skupiny podobně jako objekty, které jsou uvedené.</span><span class="sxs-lookup"><span data-stu-id="e14e6-249">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="e14e6-250">Podporuje specifickou syntaxi v jazyce Visual Basic [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) , který umožňuje iterování položek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e14e6-250">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="e14e6-251">Kromě toho kolekce často bylo možné použít <xref:Microsoft.VisualBasic.Collection.Item%2A> načíst prvky podle jejich indexu nebo tím, že přidružíte s jedinečným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="e14e6-251">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="e14e6-252">Kolekce může být snadnější použití než pole, protože umožňují přidat nebo odebrat položky bez použití indexů.</span><span class="sxs-lookup"><span data-stu-id="e14e6-252">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="e14e6-253">Z důvodu jejich snadné použití kolekce často se používají k ukládání formuláře a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e14e6-253">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="e14e6-254">Související témata</span><span class="sxs-lookup"><span data-stu-id="e14e6-254">Related topics</span></span>

<span data-ttu-id="e14e6-255">[Návod: Definování tříd](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="e14e6-255">[Walkthrough: Defining Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="e14e6-256">Poskytuje podrobný popis toho, jak vytvořit třídu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-256">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="e14e6-257">[Vlastnosti a metody přetečení](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="e14e6-257">[Overloaded Properties and Methods](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="e14e6-258">Vlastnosti a metody přetečení</span><span class="sxs-lookup"><span data-stu-id="e14e6-258">Overloaded Properties and Methods</span></span>

<span data-ttu-id="e14e6-259">[Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="e14e6-259">[Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span></span>\
<span data-ttu-id="e14e6-260">Popisuje modifikátory dědění, přepisování metody a vlastnosti, MyBase a MyClass.</span><span class="sxs-lookup"><span data-stu-id="e14e6-260">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="e14e6-261">[Doba života objektu: Způsob vytváření a zničení objektů](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="e14e6-261">[Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="e14e6-262">Tento článek popisuje vytvoření a uvolnění instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="e14e6-262">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="e14e6-263">[Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="e14e6-263">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span></span>\
<span data-ttu-id="e14e6-264">Popisuje, jak vytvořit a použít anonymní typy, které umožňují vytvářet objekty bez psaní definice třídy datového typu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-264">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="e14e6-265">[Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="e14e6-265">[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="e14e6-266">Tento článek popisuje inicializátory objektů, které se používají k vytvoření instance pojmenované a anonymní typy pomocí jediného výrazu.</span><span class="sxs-lookup"><span data-stu-id="e14e6-266">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="e14e6-267">[Postupy: Odvození názvů a typů v deklaracích anonymního typu vlastností](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="e14e6-267">[How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="e14e6-268">Vysvětluje, jak k odvození názvů a typů v deklaracích anonymního typu vlastností.</span><span class="sxs-lookup"><span data-stu-id="e14e6-268">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="e14e6-269">Obsahuje příklady úspěšné a neúspěšné odvození.</span><span class="sxs-lookup"><span data-stu-id="e14e6-269">Provides examples of successful and unsuccessful inference.</span></span>
