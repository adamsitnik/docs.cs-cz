---
title: 'Postupy: Řazení a filtrování dat ADO.NET pomocí komponenty Windows Forms BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: 8904eff39b7278b2a185cc5e2f738ece1e8e88e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306505"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="872b4-102">Postupy: Řazení a filtrování dat ADO.NET pomocí komponenty Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="872b4-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="872b4-103">Můžete zveřejnit řazení a filtrování schopnost <xref:System.Windows.Forms.BindingSource> řídit prostřednictvím <xref:System.Windows.Forms.BindingSource.Sort%2A> a <xref:System.Windows.Forms.BindingSource.Filter%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="872b4-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="872b4-104">Můžete provést jednoduché řazení podkladovým zdrojem dat je <xref:System.ComponentModel.IBindingList>, a můžete použít filtrování a rozšířené řazení, pokud je zdroj dat <xref:System.ComponentModel.IBindingListView>.</span><span class="sxs-lookup"><span data-stu-id="872b4-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="872b4-105"><xref:System.Windows.Forms.BindingSource.Sort%2A> Vlastnost vyžaduje standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntaxe: řetězec představující název sloupce dat ve zdroji dat, za nímž následuje `ASC` nebo `DESC` označující, zda mají být řazeny seznam ve vzestupném nebo sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="872b4-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="872b4-106">Můžete nastavit rozšířené řazení nebo řazení více sloupců tak, že oddělíte každý sloupec s oddělovačem čárkou.</span><span class="sxs-lookup"><span data-stu-id="872b4-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="872b4-107"><xref:System.Windows.Forms.BindingSource.Filter%2A> Vlastnost přebírá řetězcového výrazu.</span><span class="sxs-lookup"><span data-stu-id="872b4-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="872b4-108">Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="872b4-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="872b4-109">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="872b4-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="872b4-110">Další informace najdete v tématu [chrání informace o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="872b4-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="872b4-111">K filtrování dat pomocí objektu BindingSource</span><span class="sxs-lookup"><span data-stu-id="872b4-111">To filter data with the BindingSource</span></span>  
  
-   <span data-ttu-id="872b4-112">Nastavte <xref:System.Windows.Forms.BindingSource.Filter%2A> vlastnost pro výraz, který chcete.</span><span class="sxs-lookup"><span data-stu-id="872b4-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="872b4-113">Výraz v následujícím příkladu kódu je název sloupce zadáte hodnotu, která chcete použít pro sloupec.</span><span class="sxs-lookup"><span data-stu-id="872b4-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="872b4-114">Řazení dat pomocí BindingSource</span><span class="sxs-lookup"><span data-stu-id="872b4-114">To sort data with the BindingSource</span></span>  
  
1. <span data-ttu-id="872b4-115">Nastavte <xref:System.Windows.Forms.BindingSource.Sort%2A> nastavte na název sloupce, který chcete, za nímž následuje `ASC` nebo `DESC` označíte, vzestupném nebo sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="872b4-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2. <span data-ttu-id="872b4-116">Oddělte čárkou více sloupců.</span><span class="sxs-lookup"><span data-stu-id="872b4-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="872b4-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="872b4-117">Example</span></span>  
 <span data-ttu-id="872b4-118">Následující příklad kódu načte data z tabulky Customers v ukázkové databázi Northwind <xref:System.Windows.Forms.DataGridView> ovládací prvek a filtry a seřadí zobrazená data.</span><span class="sxs-lookup"><span data-stu-id="872b4-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="872b4-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="872b4-119">Compiling the Code</span></span>  
 <span data-ttu-id="872b4-120">Chcete-li spustit tento příklad, vložte kód do formuláře, který obsahuje <xref:System.Windows.Forms.BindingSource> s názvem `BindingSource1` a <xref:System.Windows.Forms.DataGridView> s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="872b4-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="872b4-121">Zpracování <xref:System.Windows.Forms.Form.Load> událost pro formulář opravdu zavřít a volání `InitializeSortedFilteredBindingSource` v metodě obslužné rutiny události load.</span><span class="sxs-lookup"><span data-stu-id="872b4-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="872b4-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="872b4-122">See also</span></span>

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- <span data-ttu-id="872b4-123">[Postupy: Instalace ukázkových databází](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="872b4-123">[How to: Install Sample Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span></span>
- [<span data-ttu-id="872b4-124">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="872b4-124">BindingSource Component</span></span>](bindingsource-component.md)
