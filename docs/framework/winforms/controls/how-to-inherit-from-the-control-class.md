---
title: 'Postupy: Dědění ze třídy Control'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: 14f225f5587379b3efa7b6dc2475f1b697ebb281
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941138"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="8b297-102">Postupy: Dědění ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="8b297-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="8b297-103">Pokud chcete vytvořit zcela vlastní ovládací prvek na formuláři Windows používat, musí dědit z <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="8b297-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="8b297-104">Při dědění z <xref:System.Windows.Forms.Control> třídy vyžaduje, můžete provést další plánování a implementace, také poskytuje největší škálu možností.</span><span class="sxs-lookup"><span data-stu-id="8b297-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="8b297-105">Při dědění z <xref:System.Windows.Forms.Control>, zdědíte velmi základní funkce, která provádí ovládací prvky fungují.</span><span class="sxs-lookup"><span data-stu-id="8b297-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="8b297-106">Vyplývajících z funkce <xref:System.Windows.Forms.Control> třída zpracovává vstupu uživatele prostřednictvím klávesnici a myš, definují hranice a velikost ovládacího prvku, poskytuje popisovačů systému windows a poskytuje zpracování zpráv a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8b297-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="8b297-107">Sestavené všechny Malování, který v tomto případě je skutečná vykreslování ovládacího prvku grafického rozhraní, ani nemá začlenit funkce interakce konkrétního uživatele.</span><span class="sxs-lookup"><span data-stu-id="8b297-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="8b297-108">Je nutné zadat všechny tyto aspekty prostřednictvím vlastního kódu.</span><span class="sxs-lookup"><span data-stu-id="8b297-108">You must provide all of these aspects through custom code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b297-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="8b297-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8b297-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="8b297-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8b297-111">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="8b297-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-custom-control"></a><span data-ttu-id="8b297-112">Chcete-li vytvořit vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="8b297-112">To create a custom control</span></span>  
  
1. <span data-ttu-id="8b297-113">Vytvořte nový **aplikace Windows** nebo **Knihovna ovládacích prvků Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="8b297-113">Create a new **Windows Application** or **Windows Control Library** project.</span></span>  
  
2. <span data-ttu-id="8b297-114">Z **projektu** nabídce zvolte **přidat třídu**.</span><span class="sxs-lookup"><span data-stu-id="8b297-114">From the **Project** menu, choose **Add Class**.</span></span>  
  
3. <span data-ttu-id="8b297-115">V **přidat novou položku** dialogové okno, klikněte na tlačítko **vlastní ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="8b297-115">In the **Add New Item** dialog box, click **Custom Control**.</span></span>  
  
     <span data-ttu-id="8b297-116">Nový vlastní ovládací prvek se přidá do vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="8b297-116">A new custom control is added to your project.</span></span>  
  
4. <span data-ttu-id="8b297-117">Stisknutím klávesy F7 otevřít **Editor kódu** pro vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8b297-117">Press F7 to open the **Code Editor** for your custom control.</span></span>  
  
5. <span data-ttu-id="8b297-118">Vyhledejte <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, která bude prázdný s výjimkou volání <xref:System.Windows.Forms.Control.OnPaint%2A> metody základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8b297-118">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
6. <span data-ttu-id="8b297-119">Upravte kód začlenit vlastní vykreslení obsahu, které chcete pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8b297-119">Modify the code to incorporate any custom painting you want for your control.</span></span>  
  
     <span data-ttu-id="8b297-120">Informace o psaní kódu pro vykreslení grafiky pro ovládací prvky najdete v tématu [vlastní ovládací prvek Malování a vykreslování](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="8b297-120">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>  
  
7. <span data-ttu-id="8b297-121">Implementujte všechny vlastní metody, vlastnosti nebo události, které bude obsahovat váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8b297-121">Implement any custom methods, properties, or events that your control will incorporate.</span></span>  
  
8. <span data-ttu-id="8b297-122">Uložit a testování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8b297-122">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b297-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b297-123">See also</span></span>

- [<span data-ttu-id="8b297-124">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="8b297-124">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="8b297-125">Postupy: Dědit ze třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="8b297-125">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="8b297-126">Postupy: Dědění z existujících Windows Forms ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="8b297-126">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="8b297-127">Postupy: Autor ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b297-127">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="8b297-128">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b297-128">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="8b297-129">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="8b297-129">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
