---
title: 'Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
ms.openlocfilehash: 286b56cddc18589b936a7f053a12ed44c81a32b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072971"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="65b2b-102">Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList</span><span class="sxs-lookup"><span data-stu-id="65b2b-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="65b2b-103">Windows Forms <xref:System.Windows.Forms.ImageList> komponenty se obvykle vyplní imagí dřív, než bude přidružena k ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="65b2b-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="65b2b-104">Můžete ale přidávat a odebírat Image po přidružení seznamu obrázků s ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="65b2b-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65b2b-105">Když odeberete Image, ověřte, že <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> vlastnosti všech přidružených ovládacích prvků je stále platný.</span><span class="sxs-lookup"><span data-stu-id="65b2b-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="65b2b-106">Přidání bitové kopie prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="65b2b-106">To add images programmatically</span></span>  
  
-   <span data-ttu-id="65b2b-107">Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metoda seznamu obrázků <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="65b2b-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="65b2b-108">V následujícím příkladu kódu nastavena cesta pro umístění image je **dokumenty** složky.</span><span class="sxs-lookup"><span data-stu-id="65b2b-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="65b2b-109">Toto umístění se používá, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows bude obsahovat této složky.</span><span class="sxs-lookup"><span data-stu-id="65b2b-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="65b2b-110">Výběrem tohoto umístění také umožňuje uživatelům, kteří mají minimální systém úrovně přístupu Další bezpečné spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="65b2b-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="65b2b-111">Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.ImageList> ovládací prvek již přidán.</span><span class="sxs-lookup"><span data-stu-id="65b2b-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    End Sub  
    ```  
  
    ```csharp  
    public void addImage()  
    {  
    // Be sure that you use an appropriate escape sequence (such as the   
    // @) when specifying the location of the file.  
       System.Drawing.Image myImage =   
         Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
    }  
    ```  
  
    ```cpp  
    public:  
       void addImage()  
       {  
       // Replace the bold image in the following sample   
       // with your own icon.  
       // Be sure that you use an appropriate escape sequence (such as   
       // \\) when specifying the location of the file.  
          System::Drawing::Image ^ myImage =   
             Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
       }  
    ```  
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="65b2b-112">Přidání bitové kopie s hodnotou klíče.</span><span class="sxs-lookup"><span data-stu-id="65b2b-112">To add images with a key value.</span></span>  
  
-   <span data-ttu-id="65b2b-113">Použijte jednu z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metody ze seznamu obrázků <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost, která přebírá hodnotu klíče.</span><span class="sxs-lookup"><span data-stu-id="65b2b-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="65b2b-114">V následujícím příkladu kódu nastavena cesta pro umístění image je **dokumenty** složky.</span><span class="sxs-lookup"><span data-stu-id="65b2b-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="65b2b-115">Toto umístění se používá, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows bude obsahovat této složky.</span><span class="sxs-lookup"><span data-stu-id="65b2b-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="65b2b-116">Výběrem tohoto umístění také umožňuje uživatelům, kteří mají minimální systém úrovně přístupu Další bezpečné spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="65b2b-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="65b2b-117">Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.ImageList> ovládací prvek již přidán.</span><span class="sxs-lookup"><span data-stu-id="65b2b-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add("myPhoto", myImage)  
    End Sub  
    ```  
  
```csharp  
public void addImage()  
{  
// Be sure that you use an appropriate escape sequence (such as the   
// @) when specifying the location of the file.  
   System.Drawing.Image myImage =   
     Image.FromFile  
   (System.Environment.GetFolderPath  
   (System.Environment.SpecialFolder.Personal)  
   + @"\Image.gif");  
   imageList1.Images.Add("myPhoto", myImage);  
}  
```  
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="65b2b-118">Chcete-li odebrat všechny bitové kopie prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="65b2b-118">To remove all images programmatically</span></span>  
  
-   <span data-ttu-id="65b2b-119">Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> metoda odebrání jedné image</span><span class="sxs-lookup"><span data-stu-id="65b2b-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="65b2b-120">, - nebo -</span><span class="sxs-lookup"><span data-stu-id="65b2b-120">,-or-</span></span>  
  
     <span data-ttu-id="65b2b-121">Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> metoda zrušte všechny Image v seznamu obrázků.</span><span class="sxs-lookup"><span data-stu-id="65b2b-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
    ```vb  
    ' Removes the first image in the image list  
    ImageList1.Images.Remove(myImage)  
    ' Clears all images in the image list  
    ImageList1.Images.Clear()  
    ```  
  
```csharp  
// Removes the first image in the image list.  
imageList1.Images.Remove(myImage);  
// Clears all images in the image list.  
imageList1.Images.Clear();  
```  
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="65b2b-122">Chcete-li odebrat imagí pomocí klíče</span><span class="sxs-lookup"><span data-stu-id="65b2b-122">To remove images by key</span></span>  
  
-   <span data-ttu-id="65b2b-123">Použití <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> metoda odebrání jedné image podle jeho klíče.</span><span class="sxs-lookup"><span data-stu-id="65b2b-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="65b2b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65b2b-124">See also</span></span>

- [<span data-ttu-id="65b2b-125">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="65b2b-125">ImageList Component</span></span>](imagelist-component-windows-forms.md)
- [<span data-ttu-id="65b2b-126">Přehled komponenty ImageList</span><span class="sxs-lookup"><span data-stu-id="65b2b-126">ImageList Component Overview</span></span>](imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="65b2b-127">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="65b2b-127">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
