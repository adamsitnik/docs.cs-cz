---
title: 'Postupy: Načtení obrázku pomocí návrháře (model Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 1d95d5baafa42c7dea40933ba837b684d90b7b2b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972376"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="111df-102">Postupy: Načtení obrázku pomocí návrháře (model Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="111df-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="111df-103">Pomocí ovládacího prvku <xref:System.Windows.Forms.PictureBox> model Windows Forms můžete načíst a zobrazit obrázek ve formuláři v době návrhu <xref:System.Windows.Forms.PictureBox.Image%2A> nastavením vlastnosti na platný obrázek.</span><span class="sxs-lookup"><span data-stu-id="111df-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="111df-104">V následující tabulce jsou uvedeny přijatelné typy souborů.</span><span class="sxs-lookup"><span data-stu-id="111df-104">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="111df-105">type</span><span class="sxs-lookup"><span data-stu-id="111df-105">Type</span></span>|<span data-ttu-id="111df-106">Přípona názvu souboru</span><span class="sxs-lookup"><span data-stu-id="111df-106">File name extension</span></span>|
|----------|-------------------------|
|<span data-ttu-id="111df-107">Monochromatick</span><span class="sxs-lookup"><span data-stu-id="111df-107">Bitmap</span></span>|<span data-ttu-id="111df-108">. bmp</span><span class="sxs-lookup"><span data-stu-id="111df-108">.bmp</span></span>|
|<span data-ttu-id="111df-109">Ikona</span><span class="sxs-lookup"><span data-stu-id="111df-109">Icon</span></span>|<span data-ttu-id="111df-110">.ico</span><span class="sxs-lookup"><span data-stu-id="111df-110">.ico</span></span>|
|<span data-ttu-id="111df-111">GIF</span><span class="sxs-lookup"><span data-stu-id="111df-111">GIF</span></span>|<span data-ttu-id="111df-112">. gif</span><span class="sxs-lookup"><span data-stu-id="111df-112">.gif</span></span>|
|<span data-ttu-id="111df-113">Soubory</span><span class="sxs-lookup"><span data-stu-id="111df-113">Metafile</span></span>|<span data-ttu-id="111df-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="111df-114">.wmf</span></span>|
|<span data-ttu-id="111df-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="111df-115">JPEG</span></span>|<span data-ttu-id="111df-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="111df-116">.jpg</span></span>|

> [!NOTE]
>  <span data-ttu-id="111df-117">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="111df-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="111df-118">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="111df-118">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="111df-119">Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="111df-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="111df-120">Zobrazení obrázku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="111df-120">To display a picture at design time</span></span>

1. <span data-ttu-id="111df-121">Nakreslete <xref:System.Windows.Forms.PictureBox> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="111df-121">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="111df-122">V okno Vlastnosti vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a potom klikněte na tlačítko se třemi tečkami. zobrazí se dialogové okno **otevřít** .</span><span class="sxs-lookup"><span data-stu-id="111df-122">On the Properties window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then click the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="111df-123">Pokud hledáte určitý typ souboru (například soubory. gif), vyberte ho v poli **soubory typu** .</span><span class="sxs-lookup"><span data-stu-id="111df-123">If you are looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="111df-124">Vyberte soubor, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="111df-124">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="111df-125">Vymazání obrázku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="111df-125">To clear the picture at design time</span></span>

1. <span data-ttu-id="111df-126">V okně **vlastnosti** vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a klikněte pravým tlačítkem myši na miniaturu malého obrázku, který se zobrazí nalevo od názvu objektu obrázku.</span><span class="sxs-lookup"><span data-stu-id="111df-126">On the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property and right-click the small thumbnail image that appears to the left of the name of the image object.</span></span> <span data-ttu-id="111df-127">Vyberte možnost **obnovit**.</span><span class="sxs-lookup"><span data-stu-id="111df-127">Choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="111df-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="111df-128">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="111df-129">Přehled ovládacího prvku PictureBox</span><span class="sxs-lookup"><span data-stu-id="111df-129">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="111df-130">Postupy: Změna velikosti nebo umístění obrázku v době běhu</span><span class="sxs-lookup"><span data-stu-id="111df-130">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="111df-131">Postupy: Nastavit obrázky v době běhu</span><span class="sxs-lookup"><span data-stu-id="111df-131">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="111df-132">Ovládací prvek PictureBox</span><span class="sxs-lookup"><span data-stu-id="111df-132">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
