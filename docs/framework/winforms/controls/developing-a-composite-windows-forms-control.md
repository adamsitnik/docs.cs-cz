---
title: Vývoj složeného ovládacího prvku Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: 82d76c1656ff14c6d1c9bbbb1c79ec3a30708a90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635712"
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="acc2c-102">Vývoj složeného ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="acc2c-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="acc2c-103">Můžete vyvíjet složeného ovládacího prvku Windows Forms kombinací jiných ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="acc2c-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="acc2c-104">Složené ovládací prvky, které jsou odvozeny z <xref:System.Web.UI.UserControl> se nazývají uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="acc2c-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="acc2c-105">Základní třída <xref:System.Windows.Forms.UserControl>, poskytuje směrování pro podřízené ovládací prvky, čímž zajišťuje, že podřízených ovládacích prvků může získat fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="acc2c-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="acc2c-106">Příkladem uživatelského ovládacího prvku, naleznete v tématu <xref:System.Windows.Forms.UserControl> ukázku v [jak: Použití atributů v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="acc2c-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="acc2c-107">Návrhář formulářů Windows v sadě Visual Studio poskytuje bohatou podporu návrhu pro vytváření uživatelských ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="acc2c-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>  
  
-   <span data-ttu-id="acc2c-108">[Postupy: Zobrazení ovládacího prvku v zvolit položky panelu nástrojů – dialogové okno](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-108">[How to: Display a Control in the Choose Toolbox Items Dialog Box](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span></span>  
  
-   [<span data-ttu-id="acc2c-109">Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="acc2c-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   <span data-ttu-id="acc2c-110">[Návod: Dědění z Windows Forms ovládací prvek s Vizuálem C# ](https://msdn.microsoft.com/library/09476da0-8d4c-4a4c-b969-649519dfb438))</span><span class="sxs-lookup"><span data-stu-id="acc2c-110">[Walkthrough: Inheriting from a Windows Forms Control with Visual C#](https://msdn.microsoft.com/library/09476da0-8d4c-4a4c-b969-649519dfb438))</span></span>  
  
-   <span data-ttu-id="acc2c-111">[Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-111">[How to: Provide a Toolbox Bitmap for a Control](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="acc2c-112">[Postupy: Dědění z existujících Windows Forms ovládacích prvků](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-112">[How to: Inherit from Existing Windows Forms Controls](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="acc2c-113">[Návod: Ovládací prvky ladění vlastního Windows Forms v době návrhu](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-113">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="acc2c-114">[Postupy: Dědit ze třídy Control](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-114">[How to: Inherit from the Control Class](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span></span>  
  
-   [<span data-ttu-id="acc2c-115">Postupy: Testování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="acc2c-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   <span data-ttu-id="acc2c-116">[Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-116">[How to: Align a Control to the Edges of Forms at Design Time](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="acc2c-117">[Postupy: Dědit ze třídy UserControl](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-117">[How to: Inherit from the UserControl Class](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="acc2c-118">[Postupy: Autor ovládacích prvků Windows Forms](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-118">[How to: Author Controls for Windows Forms](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="acc2c-119">[Postupy: Vytváření složených ovládacích prvků](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-119">[How to: Author Composite Controls](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="acc2c-120">[Návod: Vytvoření složeného ovládacího prvku s jazykem Visual Basic](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-120">[Walkthrough: Authoring a Composite Control with Visual Basic](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="acc2c-121">[Návod: Vytvoření složeného ovládacího prvku s Vizuálem C# ](https://msdn.microsoft.com/library/f88481a8-c746-4a36-9479-374ce5f2e91f))</span><span class="sxs-lookup"><span data-stu-id="acc2c-121">[Walkthrough: Authoring a Composite Control with Visual C#](https://msdn.microsoft.com/library/f88481a8-c746-4a36-9479-374ce5f2e91f))</span></span>  
  
-   <span data-ttu-id="acc2c-122">[Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-122">[Walkthrough: Inheriting from a Windows Forms Control with Visual Basic](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="acc2c-123">[Postupy: Vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu aplikace](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-123">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="acc2c-124">[Postupy: Vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu aplikace](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="acc2c-124">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc2c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acc2c-125">See also</span></span>
- [<span data-ttu-id="acc2c-126">Postupy: Použití atributů v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="acc2c-126">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="acc2c-127">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="acc2c-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="acc2c-128">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="acc2c-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
