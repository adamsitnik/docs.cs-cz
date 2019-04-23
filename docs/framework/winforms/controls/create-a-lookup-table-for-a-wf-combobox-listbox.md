---
title: 'Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek Windows Forms ComboBox, ListBox nebo CheckedListBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: a58522cc17ac379897a89a8e61485a1e271438a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344101"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="77246-102">Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="77246-102">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="77246-103">Někdy je užitečné zobrazit data ve formátu uživatelsky přívětivé ve formuláři Windows Forms, ale ukládat data ve formátu, který má více smysl pro váš program.</span><span class="sxs-lookup"><span data-stu-id="77246-103">Sometimes it is useful to display data in a user-friendly format on a Windows Form, but store the data in a format that is more meaningful to your program.</span></span> <span data-ttu-id="77246-104">Například může zobrazit formulář objednávky pro potravin položky nabídky podle názvu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="77246-104">For example, an order form for food might display the menu items by name in a list box.</span></span> <span data-ttu-id="77246-105">Tabulka dat záznam pořadí by ale obsahovat jedinečné identifikační čísla představující potravinovém.</span><span class="sxs-lookup"><span data-stu-id="77246-105">However, the data table recording the order would contain the unique ID numbers representing the food.</span></span> <span data-ttu-id="77246-106">Příklad toho, jak ukládat a zobrazovat data formulář objednávky potravin naleznete v následujících tabulkách.</span><span class="sxs-lookup"><span data-stu-id="77246-106">The following tables show an example of how to store and display order-form data for food.</span></span>  
  
### <a name="orderdetailstable"></a><span data-ttu-id="77246-107">OrderDetailsTable</span><span class="sxs-lookup"><span data-stu-id="77246-107">OrderDetailsTable</span></span>  
  
|<span data-ttu-id="77246-108">ID objednávky</span><span class="sxs-lookup"><span data-stu-id="77246-108">OrderID</span></span>|<span data-ttu-id="77246-109">ID položky</span><span class="sxs-lookup"><span data-stu-id="77246-109">ItemID</span></span>|<span data-ttu-id="77246-110">Množství</span><span class="sxs-lookup"><span data-stu-id="77246-110">Quantity</span></span>|  
|-------------|------------|--------------|  
|<span data-ttu-id="77246-111">4085</span><span class="sxs-lookup"><span data-stu-id="77246-111">4085</span></span>|<span data-ttu-id="77246-112">12</span><span class="sxs-lookup"><span data-stu-id="77246-112">12</span></span>|<span data-ttu-id="77246-113">1</span><span class="sxs-lookup"><span data-stu-id="77246-113">1</span></span>|  
|<span data-ttu-id="77246-114">4086</span><span class="sxs-lookup"><span data-stu-id="77246-114">4086</span></span>|<span data-ttu-id="77246-115">13</span><span class="sxs-lookup"><span data-stu-id="77246-115">13</span></span>|<span data-ttu-id="77246-116">3</span><span class="sxs-lookup"><span data-stu-id="77246-116">3</span></span>|  
  
### <a name="itemtable"></a><span data-ttu-id="77246-117">ItemTable</span><span class="sxs-lookup"><span data-stu-id="77246-117">ItemTable</span></span>  
  
|<span data-ttu-id="77246-118">ID</span><span class="sxs-lookup"><span data-stu-id="77246-118">ID</span></span>|<span data-ttu-id="77246-119">Název</span><span class="sxs-lookup"><span data-stu-id="77246-119">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="77246-120">12</span><span class="sxs-lookup"><span data-stu-id="77246-120">12</span></span>|<span data-ttu-id="77246-121">Potato</span><span class="sxs-lookup"><span data-stu-id="77246-121">Potato</span></span>|  
|<span data-ttu-id="77246-122">13</span><span class="sxs-lookup"><span data-stu-id="77246-122">13</span></span>|<span data-ttu-id="77246-123">Kuřecí</span><span class="sxs-lookup"><span data-stu-id="77246-123">Chicken</span></span>|  
  
 <span data-ttu-id="77246-124">V tomto scénáři, jedné tabulky **OrderDetailsTable**, ukládá informace jste obeznámeni s zobrazení a uložení.</span><span class="sxs-lookup"><span data-stu-id="77246-124">In this scenario, one table, **OrderDetailsTable**, stores the actual information you are concerned with displaying and saving.</span></span> <span data-ttu-id="77246-125">Ale pro úsporu místa, dělá to docela nejasné způsobem.</span><span class="sxs-lookup"><span data-stu-id="77246-125">But to save space, it does so in a fairly cryptic fashion.</span></span> <span data-ttu-id="77246-126">V další tabulce **ItemTable**, obsahuje pouze informace vzhled o které ID číslo je ekvivalentní, na které potravin název a nic o objednávkách skutečné potravin.</span><span class="sxs-lookup"><span data-stu-id="77246-126">The other table, **ItemTable**, contains only appearance-related information about which ID number is equivalent to which food name, and nothing about the actual food orders.</span></span>  
  
 <span data-ttu-id="77246-127">**ItemTable** je připojen k <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, nebo <xref:System.Windows.Forms.CheckedListBox> řízení prostřednictvím tři vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="77246-127">The **ItemTable** is connected to the <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control through three properties.</span></span> <span data-ttu-id="77246-128">`DataSource` Vlastnost obsahuje název této tabulky.</span><span class="sxs-lookup"><span data-stu-id="77246-128">The `DataSource` property contains the name of this table.</span></span> <span data-ttu-id="77246-129">`DisplayMember` Vlastnost obsahuje sloupce dat této tabulky, kterou chcete zobrazit v ovládacím prvku (food název).</span><span class="sxs-lookup"><span data-stu-id="77246-129">The `DisplayMember` property contains the data column of that table that you want to display in the control (the food name).</span></span> <span data-ttu-id="77246-130">`ValueMember` Vlastnost obsahuje sloupce dat této tabulky s uložené informace (identifikační číslo).</span><span class="sxs-lookup"><span data-stu-id="77246-130">The `ValueMember` property contains the data column of that table with the stored information (the ID number).</span></span>  
  
 <span data-ttu-id="77246-131">**OrderDetailsTable** je připojen k ovládací prvek pomocí jeho vazby kolekce přistupovat prostřednictvím <xref:System.Windows.Forms.Control.DataBindings%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="77246-131">The **OrderDetailsTable** is connected to the control by its bindings collection, accessed through the <xref:System.Windows.Forms.Control.DataBindings%2A> property.</span></span> <span data-ttu-id="77246-132">Při přidání objektu vazby ke kolekci připojíte vlastnosti ovládacího prvku do konkrétního datového člena (sloupec ID čísla) ve zdroji dat ( **OrderDetailsTable**).</span><span class="sxs-lookup"><span data-stu-id="77246-132">When you add a binding object to the collection, you connect a control property to a specific data member (the column of ID numbers) in a data source (the **OrderDetailsTable**).</span></span> <span data-ttu-id="77246-133">Při provedení výběru v ovládacím prvku Tato tabulka je, kde je uložen vstup formuláře.</span><span class="sxs-lookup"><span data-stu-id="77246-133">When a selection is made in the control, this table is where the form input is saved.</span></span>  
  
### <a name="to-create-a-lookup-table"></a><span data-ttu-id="77246-134">Vytvoření vyhledávací tabulky</span><span class="sxs-lookup"><span data-stu-id="77246-134">To create a lookup table</span></span>  
  
1. <span data-ttu-id="77246-135">Přidat <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, nebo <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku na formuláři.</span><span class="sxs-lookup"><span data-stu-id="77246-135">Add a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control to the form.</span></span>  
  
2. <span data-ttu-id="77246-136">Připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="77246-136">Connect to your data source.</span></span>  
  
3. <span data-ttu-id="77246-137">Vytvořte datová relace mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="77246-137">Establish a data relation between the two tables.</span></span> <span data-ttu-id="77246-138">Zobrazit [Úvod do objektů DataRelation](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="77246-138">See [Introduction to DataRelation Objects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span></span>  
  
4. <span data-ttu-id="77246-139">Nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="77246-139">Set the following properties.</span></span> <span data-ttu-id="77246-140">To můžete udělat v kódu nebo v návrháři.</span><span class="sxs-lookup"><span data-stu-id="77246-140">They can be set in code or in the designer.</span></span>  
  
    |<span data-ttu-id="77246-141">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77246-141">Property</span></span>|<span data-ttu-id="77246-142">Nastavení</span><span class="sxs-lookup"><span data-stu-id="77246-142">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|<span data-ttu-id="77246-143">Tabulka, která obsahuje informace, o které ID číslo odpovídá které položce.</span><span class="sxs-lookup"><span data-stu-id="77246-143">The table that contains information about which ID number is equivalent to which item.</span></span> <span data-ttu-id="77246-144">V předchozím scénáři je to `ItemTable`.</span><span class="sxs-lookup"><span data-stu-id="77246-144">In the previous scenario, this is `ItemTable`.</span></span>|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|<span data-ttu-id="77246-145">Sloupec tabulky zdroje dat, který chcete zobrazit v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="77246-145">The column of the data source table that you want to display in the control.</span></span> <span data-ttu-id="77246-146">V předchozím scénáři je to `"Name"` (Pokud chcete nastavit v kódu, použijte uvozovky).</span><span class="sxs-lookup"><span data-stu-id="77246-146">In the previous scenario, this is `"Name"` (to set in code, use quotation marks).</span></span>|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|<span data-ttu-id="77246-147">Sloupec tabulky zdroje dat, obsahující uložené informace.</span><span class="sxs-lookup"><span data-stu-id="77246-147">The column of the data source table that contains the stored information.</span></span> <span data-ttu-id="77246-148">V předchozím scénáři je to `"ID"` (Pokud chcete nastavit v kódu, použijte uvozovky).</span><span class="sxs-lookup"><span data-stu-id="77246-148">In the previous scenario, this is `"ID"` (to set in code, use quotation marks).</span></span>|  
  
5. <span data-ttu-id="77246-149">V postupu, zavolejte <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metodu <xref:System.Windows.Forms.ControlBindingsCollection> třída pro vytvoření vazby ovládacího prvku <xref:System.Windows.Forms.ListControl.SelectedValue%2A> vlastnost do tabulky záznam vstup formuláře.</span><span class="sxs-lookup"><span data-stu-id="77246-149">In a procedure, call the <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> method of the <xref:System.Windows.Forms.ControlBindingsCollection> class to bind the control's <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property to the table recording the form input.</span></span> <span data-ttu-id="77246-150">Můžete také uděláte v Návrháři místo v kódu, díky přístupu do ovládacího prvku <xref:System.Windows.Forms.Control.DataBindings%2A> vlastnost **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="77246-150">You can also do this in the Designer instead of in code, by accessing the control's <xref:System.Windows.Forms.Control.DataBindings%2A> property in the **Properties** window.</span></span> <span data-ttu-id="77246-151">V předchozím scénáři je to `OrderDetailsTable`, a sloupec je `"ItemID"`.</span><span class="sxs-lookup"><span data-stu-id="77246-151">In the previous scenario, this is `OrderDetailsTable`, and the column is `"ItemID"`.</span></span>  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="77246-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77246-152">See also</span></span>

- [<span data-ttu-id="77246-153">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="77246-153">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="77246-154">Přehled ovládacího prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="77246-154">ListBox Control Overview</span></span>](listbox-control-overview-windows-forms.md)
- [<span data-ttu-id="77246-155">Přehled ovládacího prvku ComboBox</span><span class="sxs-lookup"><span data-stu-id="77246-155">ComboBox Control Overview</span></span>](combobox-control-overview-windows-forms.md)
- [<span data-ttu-id="77246-156">Přehled ovládacího prvku CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="77246-156">CheckedListBox Control Overview</span></span>](checkedlistbox-control-overview-windows-forms.md)
- [<span data-ttu-id="77246-157">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="77246-157">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
