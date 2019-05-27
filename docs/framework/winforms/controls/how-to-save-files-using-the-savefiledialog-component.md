---
title: 'Postupy: Ukládání souborů pomocí komponenty SaveFileDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
ms.openlocfilehash: 18d9b93b78d3ed588eafa48831448983ccd61fe8
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053512"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="b945c-102">Postupy: Ukládání souborů pomocí komponenty SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="b945c-102">How to: Save Files Using the SaveFileDialog Component</span></span>
<span data-ttu-id="b945c-103"><xref:System.Windows.Forms.SaveFileDialog> Komponenta umožňuje uživatelům procházet systému souborů a vyberte soubory, které se má uložit.</span><span class="sxs-lookup"><span data-stu-id="b945c-103">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="b945c-104">Dialogové okno vrací cestu a název souboru, který uživatel vybral v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="b945c-104">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="b945c-105">Ale musíte napsat kód, který ve skutečnosti soubory zapisují na disk.</span><span class="sxs-lookup"><span data-stu-id="b945c-105">However, you must write the code to actually write the files to disk.</span></span>  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="b945c-106">Uložte soubor pomocí komponenty SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="b945c-106">To save a file using the SaveFileDialog component</span></span>  
  
- <span data-ttu-id="b945c-107">Zobrazení **uložit soubor** dialogové okno a uložte soubor vybraný uživatelem volání metody.</span><span class="sxs-lookup"><span data-stu-id="b945c-107">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>  
  
     <span data-ttu-id="b945c-108">Použití <xref:System.Windows.Forms.SaveFileDialog> komponenty <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metoda k uložení souboru.</span><span class="sxs-lookup"><span data-stu-id="b945c-108">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="b945c-109">Tato metoda poskytuje <xref:System.IO.Stream> můžete zapisovat do objektu.</span><span class="sxs-lookup"><span data-stu-id="b945c-109">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>  
  
     <span data-ttu-id="b945c-110">V příkladu níže použití <xref:System.Windows.Forms.DialogResult> vlastnost a získat tak název souboru a <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda k uložení souboru.</span><span class="sxs-lookup"><span data-stu-id="b945c-110">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="b945c-111"><xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Metoda poskytuje datového proudu pro zápis souboru.</span><span class="sxs-lookup"><span data-stu-id="b945c-111">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>  
  
     <span data-ttu-id="b945c-112">V následujícím příkladu je <xref:System.Windows.Forms.Button> ovládací prvek s přiřazenou image.</span><span class="sxs-lookup"><span data-stu-id="b945c-112">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="b945c-113">Když kliknete na tlačítko <xref:System.Windows.Forms.SaveFileDialog> s filtrem, který umožňuje soubory typu .gif, .jpeg a .bmp je vytvořena instance komponenty.</span><span class="sxs-lookup"><span data-stu-id="b945c-113">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="b945c-114">Pokud v dialogovém okně Uložit soubor byl vybrán soubor tohoto typu, je uložen obrázek na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b945c-114">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b945c-115">Pro získání nebo nastavení <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="b945c-115">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="b945c-116">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku, protože nedostatečná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b945c-116">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="b945c-117">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="b945c-117">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="b945c-118">Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládacím prvkem jeho <xref:System.Windows.Forms.ButtonBase.Image%2A> nastavenou na soubor typu .gif, .jpeg nebo BMP.</span><span class="sxs-lookup"><span data-stu-id="b945c-118">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b945c-119"><xref:System.Windows.Forms.FileDialog> Třídy <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> vlastnosti (které, z důvodu dědičnosti, je součástí <xref:System.Windows.Forms.SaveFileDialog> třídy) používá indexu se základem 1.</span><span class="sxs-lookup"><span data-stu-id="b945c-119">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="b945c-120">To je důležité, pokud píšete kód k uložení dat v určitém formátu (například ukládání souboru ve formátu prostého textu a binárních).</span><span class="sxs-lookup"><span data-stu-id="b945c-120">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="b945c-121">Tato vlastnost je mezi vybranými položkami v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b945c-121">This property is featured in the example below.</span></span>  
  
    ```vb  
    Private Sub Button2_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button2.Click  
       ' Displays a SaveFileDialog so the user can save the Image  
       ' assigned to Button2.  
       Dim saveFileDialog1 As New SaveFileDialog()  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"  
       saveFileDialog1.Title = "Save an Image File"  
       saveFileDialog1.ShowDialog()  
  
       ' If the file name is not an empty string open it for saving.  
       If saveFileDialog1.FileName <> "" Then  
          ' Saves the Image via a FileStream created by the OpenFile method.  
          Dim fs As System.IO.FileStream = Ctype _  
             (saveFileDialog1.OpenFile(), System.IO.FileStream)  
          ' Saves the Image in the appropriate ImageFormat based upon the  
          ' file type selected in the dialog box.  
          ' NOTE that the FilterIndex property is one-based.  
          Select Case saveFileDialog1.FilterIndex  
             Case 1  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Jpeg)  
  
             Case 2  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Bmp)  
  
             Case 3  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Gif)  
           End Select  
  
           fs.Close()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button2_Click(object sender, System.EventArgs e)  
    {  
       // Displays a SaveFileDialog so the user can save the Image  
       // assigned to Button2.  
       SaveFileDialog saveFileDialog1 = new SaveFileDialog();  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
       saveFileDialog1.Title = "Save an Image File";  
       saveFileDialog1.ShowDialog();  
  
       // If the file name is not an empty string open it for saving.  
       if(saveFileDialog1.FileName != "")  
       {  
          // Saves the Image via a FileStream created by the OpenFile method.  
          System.IO.FileStream fs =   
             (System.IO.FileStream)saveFileDialog1.OpenFile();  
          // Saves the Image in the appropriate ImageFormat based upon the  
          // File type selected in the dialog box.  
          // NOTE that the FilterIndex property is one-based.  
          switch(saveFileDialog1.FilterIndex)  
          {  
             case 1 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Jpeg);  
             break;  
  
             case 2 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Bmp);  
             break;  
  
             case 3 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Gif);  
             break;  
          }  
  
       fs.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays a SaveFileDialog so the user can save the Image  
          // assigned to Button2.  
          SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();  
          saveFileDialog1->Filter =   
             "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
          saveFileDialog1->Title = "Save an Image File";  
          saveFileDialog1->ShowDialog();  
          // If the file name is not an empty string, open it for saving.  
          if(saveFileDialog1->FileName != "")  
          {  
             // Saves the Image through a FileStream created by  
             // the OpenFile method.  
             System::IO::FileStream ^ fs =   
                safe_cast\<System::IO::FileStream*>(  
                saveFileDialog1->OpenFile());  
             // Saves the Image in the appropriate ImageFormat based on  
             // the file type selected in the dialog box.  
             // Note that the FilterIndex property is one based.  
             switch(saveFileDialog1->FilterIndex)  
             {  
                case 1 :  
                   this->button2->Image->Save(fs,  
                      System::Drawing::Imaging::ImageFormat::Jpeg);  
                   break;  
                case 2 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Bmp);  
                   break;  
                case 3 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Gif);  
                   break;  
             }  
          fs->Close();  
          }  
       }  
    ```  
  
     <span data-ttu-id="b945c-122">(Visual C# a vizuální C++) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b945c-122">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     <span data-ttu-id="b945c-123">Další informace o vytváření datové proudy souborů najdete v tématu <xref:System.IO.FileStream.BeginWrite%2A> a <xref:System.IO.FileStream.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="b945c-123">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b945c-124">Některé ovládací prvky, jako například <xref:System.Windows.Forms.RichTextBox> řídit, se budou moct ukládat soubory.</span><span class="sxs-lookup"><span data-stu-id="b945c-124">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span> <span data-ttu-id="b945c-125">Další informace najdete v části "Komponenty SaveFileDialog" technického článku MSDN Online Library [základní kód pro Windows Forms dialogových oknech](https://go.microsoft.com/fwlink/?LinkID=102575).</span><span class="sxs-lookup"><span data-stu-id="b945c-125">For more information, see the "SaveFileDialog Component" section of the MSDN Online Library technical article, [Essential Code for Windows Forms Dialog Boxes](https://go.microsoft.com/fwlink/?LinkID=102575).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b945c-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b945c-126">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="b945c-127">Komponenta SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="b945c-127">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
