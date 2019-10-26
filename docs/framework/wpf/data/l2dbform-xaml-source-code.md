---
title: Zdrojový kód L2DBForm.xaml
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 290b00e136f0c49e1b27d4fa1bca7321eebe936e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920942"
---
# <a name="l2dbformxaml-source-code"></a><span data-ttu-id="66e81-102">Zdrojový kód L2DBForm.xaml</span><span class="sxs-lookup"><span data-stu-id="66e81-102">L2DBForm.xaml source code</span></span>

<span data-ttu-id="66e81-103">Tato stránka obsahuje a popisuje zdrojový soubor XAML pro [datovou vazbu WPF pomocí LINQ to XMLho příkladu](linq-to-xml-data-binding-sample.md).</span><span class="sxs-lookup"><span data-stu-id="66e81-103">This page contains and describes the XAML source file for the [WPF data binding using LINQ to XML example](linq-to-xml-data-binding-sample.md).</span></span>

## <a name="overall-ui-structure"></a><span data-ttu-id="66e81-104">Celková struktura uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="66e81-104">Overall UI structure</span></span>

<span data-ttu-id="66e81-105">Jak je typický pro projekt WPF, tento soubor obsahuje jeden nadřazený prvek, <xref:System.Windows.Window> element XML, který je přidružen k odvozené třídě `L2XDBFrom` v oboru názvů `LinqToXmlDataBinding`.</span><span class="sxs-lookup"><span data-stu-id="66e81-105">As is typical for a WPF project, this file contains one parent element, a <xref:System.Windows.Window> XML element that's associated with the derived class `L2XDBFrom` in the `LinqToXmlDataBinding` namespace.</span></span>

<span data-ttu-id="66e81-106">Klientská oblast je obsažena v <xref:System.Windows.Controls.StackPanel>, kterému je přiděleno světlé modré pozadí.</span><span class="sxs-lookup"><span data-stu-id="66e81-106">The client area is contained within a <xref:System.Windows.Controls.StackPanel> that's given a light blue background.</span></span> <span data-ttu-id="66e81-107">Tento panel obsahuje čtyři oddíly <xref:System.Windows.Controls.DockPanel> uživatelského rozhraní oddělené <xref:System.Windows.Controls.Separator> panely.</span><span class="sxs-lookup"><span data-stu-id="66e81-107">This panel contains four <xref:System.Windows.Controls.DockPanel> UI sections separated by <xref:System.Windows.Controls.Separator> bars.</span></span> <span data-ttu-id="66e81-108">Účel těchto oddílů je popsán [zde](linq-to-xml-data-binding-sample.md#overview).</span><span class="sxs-lookup"><span data-stu-id="66e81-108">The purpose of these sections is described [here](linq-to-xml-data-binding-sample.md#overview).</span></span>

<span data-ttu-id="66e81-109">Každá část obsahuje popisek, který ho identifikuje.</span><span class="sxs-lookup"><span data-stu-id="66e81-109">Each section contains a label that identifies it.</span></span> <span data-ttu-id="66e81-110">V prvních dvou oddílech je tento popisek otočen 90 stupňů pomocí <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.</span><span class="sxs-lookup"><span data-stu-id="66e81-110">In the first two sections, this label is rotated 90 degrees through the use of a <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.</span></span> <span data-ttu-id="66e81-111">Zbytek oddílu obsahuje prvky uživatelského rozhraní odpovídající účelu této části, například textové bloky, textová pole a tlačítka.</span><span class="sxs-lookup"><span data-stu-id="66e81-111">The rest of the section contains UI elements appropriate to the purpose of that section, for example, text blocks, text boxes, and buttons.</span></span> <span data-ttu-id="66e81-112">V některých případech je použita podřízená <xref:System.Windows.Controls.StackPanel> k zarovnání těchto podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="66e81-112">Sometimes a child <xref:System.Windows.Controls.StackPanel> is used to align these child controls.</span></span>

## <a name="window-resource-section"></a><span data-ttu-id="66e81-113">Oddíl prostředků okna</span><span class="sxs-lookup"><span data-stu-id="66e81-113">Window resource section</span></span>

<span data-ttu-id="66e81-114">Úvodní značka `<Window.Resources>` na řádku 9 označuje začátek oddílu prostředků okna.</span><span class="sxs-lookup"><span data-stu-id="66e81-114">The opening `<Window.Resources>` tag on line 9 indicates the start of the window resource section.</span></span> <span data-ttu-id="66e81-115">Končí uzavírací značkou na řádku 35.</span><span class="sxs-lookup"><span data-stu-id="66e81-115">It ends with the closing tag on line 35.</span></span>

<span data-ttu-id="66e81-116">Značka `<ObjectDataProvider>`, která zahrnuje řádky 11 až 25, deklaruje <xref:System.Windows.Data.ObjectDataProvider> s názvem `LoadedBooks`, která jako zdroj používá <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="66e81-116">The `<ObjectDataProvider>` tag, which spans lines 11 through 25, declares a <xref:System.Windows.Data.ObjectDataProvider>, named `LoadedBooks`, that uses an <xref:System.Xml.Linq.XElement> as the source.</span></span> <span data-ttu-id="66e81-117"><xref:System.Xml.Linq.XElement> se inicializuje analýzou vloženého dokumentu XML (`CDATA` elementu).</span><span class="sxs-lookup"><span data-stu-id="66e81-117">The <xref:System.Xml.Linq.XElement> is initialized by parsing an embedded XML document (a `CDATA` element).</span></span> <span data-ttu-id="66e81-118">Všimněte si, že prázdné znaky jsou zachovány při deklaraci vloženého dokumentu XML a také při jeho analýze.</span><span class="sxs-lookup"><span data-stu-id="66e81-118">Notice that white space is preserved when declaring the embedded XML document and also when it's parsed.</span></span> <span data-ttu-id="66e81-119">Prázdné znaky jsou zachovány, protože ovládací prvek <xref:System.Windows.Controls.TextBlock>, který slouží k zobrazení nezpracovaného kódu XML, nemá žádné speciální funkce formátování XML.</span><span class="sxs-lookup"><span data-stu-id="66e81-119">White space is preserved because the <xref:System.Windows.Controls.TextBlock> control, which is used to display the raw XML, has no special XML formatting capabilities.</span></span>

<span data-ttu-id="66e81-120">Nakonec <xref:System.Windows.DataTemplate> s názvem `BookTemplate` je definována na řádcích 28 až 34.</span><span class="sxs-lookup"><span data-stu-id="66e81-120">Lastly, a <xref:System.Windows.DataTemplate> named `BookTemplate` is defined on lines 28 through 34.</span></span> <span data-ttu-id="66e81-121">Tato šablona slouží k zobrazení položek v části uživatelské rozhraní **seznamu knih** .</span><span class="sxs-lookup"><span data-stu-id="66e81-121">This template is used to display the entries in the **Book List** UI section.</span></span> <span data-ttu-id="66e81-122">Pomocí datových vazeb a LINQ to XML dynamické vlastnosti k získání ID knihy a názvu knihy prostřednictvím následujících přiřazení:</span><span class="sxs-lookup"><span data-stu-id="66e81-122">It uses data binding and LINQ to XML dynamic properties to retrieve the book ID and book name through the following assignments:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a><span data-ttu-id="66e81-123">Kód datové vazby</span><span class="sxs-lookup"><span data-stu-id="66e81-123">Data binding code</span></span>

<span data-ttu-id="66e81-124">Kromě prvku <xref:System.Windows.DataTemplate> se datová vazba používá v několika dalších místech tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="66e81-124">In addition to the <xref:System.Windows.DataTemplate> element, data binding is used in a number of other places in this file.</span></span>

<span data-ttu-id="66e81-125">V úvodní značce `<StackPanel>` na řádku 38 je vlastnost <xref:System.Windows.FrameworkElement.DataContext%2A> tohoto panelu nastavena na `LoadedBooks` poskytovatel dat.</span><span class="sxs-lookup"><span data-stu-id="66e81-125">In the opening `<StackPanel>` tag on line 38, the <xref:System.Windows.FrameworkElement.DataContext%2A> property of this panel is set to the `LoadedBooks` data provider.</span></span>

```xaml
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

<span data-ttu-id="66e81-126">Nastavení kontextu dat umožňuje, aby bylo možné (na řádku 46) pro <xref:System.Windows.Controls.TextBlock> s názvem `tbRawXml` zobrazit nezpracovaný kód XML vazbou na vlastnost `Xml` tohoto poskytovatele dat:</span><span class="sxs-lookup"><span data-stu-id="66e81-126">Setting the data context makes it possible (on line 46) for the <xref:System.Windows.Controls.TextBlock> named `tbRawXml` to display the raw XML by binding to this data provider's `Xml` property:</span></span>

```xaml
Text="{Binding Path=Xml}"
```

<span data-ttu-id="66e81-127"><xref:System.Windows.Controls.ListBox> v části uživatelské rozhraní **seznamu knih** na řádcích 58 až 62 nastaví šablonu pro své položky zobrazení na `BookTemplate` definované v části prostředků systému Windows:</span><span class="sxs-lookup"><span data-stu-id="66e81-127">The <xref:System.Windows.Controls.ListBox> in the **Book List** UI section, on lines 58 through 62, sets the template for its display items to the `BookTemplate` defined in the window resource section:</span></span>

```xaml
ItemTemplate ="{StaticResource BookTemplate}"
```

<span data-ttu-id="66e81-128">Pak na řádcích 59 až 62 jsou skutečné hodnoty knih vázány na tento seznam:</span><span class="sxs-lookup"><span data-stu-id="66e81-128">Then, on lines 59 through 62, the actual values of the books are bound to this list box:</span></span>

```xaml
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

<span data-ttu-id="66e81-129">Třetí oddíl uživatelského rozhraní, **Upravit vybranou knihu**, nejprve váže <xref:System.Windows.FrameworkElement.DataContext%2A> nadřazených <xref:System.Windows.Controls.StackPanel> k aktuálně vybrané položce v části uživatelského rozhraní **seznamu knih** (řádek 82):</span><span class="sxs-lookup"><span data-stu-id="66e81-129">The third UI section, **Edit Selected Book**, first binds the <xref:System.Windows.FrameworkElement.DataContext%2A> of the parent <xref:System.Windows.Controls.StackPanel> to the currently selected item in from the **Book List** UI section (line 82):</span></span>

```xaml
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

<span data-ttu-id="66e81-130">Potom používá obousměrnou datovou vazbu, aby se aktuální hodnoty prvků knihy zobrazovaly do a aktualizovaly ze dvou textových polí na tomto panelu.</span><span class="sxs-lookup"><span data-stu-id="66e81-130">It then uses two-way data binding, so that the current values of the book elements are displayed to, and updated from, the two text boxes in this panel.</span></span> <span data-ttu-id="66e81-131">Datová vazba na dynamické vlastnosti je podobná datové vazbě, která se používá v šabloně `BookTemplate` dat:</span><span class="sxs-lookup"><span data-stu-id="66e81-131">Data binding to dynamic properties is similar to the data binding used in the `BookTemplate` data template:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

<span data-ttu-id="66e81-132">Poslední oddíl uživatelského rozhraní, **Přidat novou knihu**, ve svém kódu XAML nepoužívá datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="66e81-132">The last UI section, **Add New Book**, doesn't use data binding in its XAML code.</span></span> <span data-ttu-id="66e81-133">Místo toho je datová vazba v kódu zpracování události v souboru *L2DBForm.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="66e81-133">Instead, data binding is in its event handling code in the file *L2DBForm.xaml.cs*.</span></span>

## <a name="example"></a><span data-ttu-id="66e81-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="66e81-134">Example</span></span>

### <a name="description"></a><span data-ttu-id="66e81-135">Popis</span><span class="sxs-lookup"><span data-stu-id="66e81-135">Description</span></span>

> [!NOTE]
> <span data-ttu-id="66e81-136">Doporučujeme zkopírovat následující kód níže do editoru kódu, jako je C# například editor zdrojového kódu v aplikaci Visual Studio, aby bylo číslování řádků snazší sledovat.</span><span class="sxs-lookup"><span data-stu-id="66e81-136">We recommend that you copy the following code below into a code editor, such as the C# source code editor in Visual Studio, so that line numbers will be easier to track.</span></span>

### <a name="code"></a><span data-ttu-id="66e81-137">Kód</span><span class="sxs-lookup"><span data-stu-id="66e81-137">Code</span></span>

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>
```

### <a name="comments"></a><span data-ttu-id="66e81-138">Komentáře</span><span class="sxs-lookup"><span data-stu-id="66e81-138">Comments</span></span>

<span data-ttu-id="66e81-139">C# Zdrojový kód obslužných rutin událostí přidružených k PRVKŮM uživatelského rozhraní WPF naleznete v tématu [L2DBForm.XAML.cs Source Code](l2dbform-xaml-cs-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="66e81-139">For the C# source code for the event handlers associated with the WPF UI elements, see [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66e81-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66e81-140">See also</span></span>

- [<span data-ttu-id="66e81-141">Návod: příklad příkladu LinqToXmlDataBinding</span><span class="sxs-lookup"><span data-stu-id="66e81-141">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="66e81-142">Zdrojový kód L2DBForm.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="66e81-142">L2DBForm.xaml.cs source code</span></span>](l2dbform-xaml-cs-source-code.md)
