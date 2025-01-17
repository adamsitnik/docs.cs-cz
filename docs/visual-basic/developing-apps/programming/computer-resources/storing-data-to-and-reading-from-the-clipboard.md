---
title: Ukládání dat do schránky a jejich čtení (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: d7693f6b5dc74e17686cd7d2667f32adbde9df80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916508"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Ukládání dat do schránky a jejich čtení (Visual Basic)
Schránku lze použít k ukládání dat, jako je například text a obrázky. Vzhledem k tomu, že schránka sdílí všechny aktivní procesy, lze ji použít k přenosu dat mezi nimi. `My.Computer.Clipboard` Objekt umožňuje snadný přístup ke schránce a čtení z nich a zápis do ní.  
  
## <a name="reading-from-the-clipboard"></a>Čtení ze schránky  
 K přečtení textu ve schránce použijte metodu.<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> Následující kód přečte text a zobrazí jej v okně se zprávou. Ve schránce musí být uložený text, aby mohl být příklad správně spuštěn.  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > schránka**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> Použijte metodu pro načtení obrázku ze schránky. Tento příklad zkontroluje, zda je ve schránce k dispozici obrázek před jeho načtením a přiřazením k `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > schránka**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Položky umístěné ve schránce zůstanou i po vypnutí aplikace.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Určení typu souboru uloženého ve schránce  
 Data ve schránce mohou mít řadu různých forem, jako je například text, zvukový soubor nebo obrázek. Chcete-li určit, který soubor je ve schránce, můžete použít <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>metody <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>jako například,, a <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Metodu lze použít, pokud máte vlastní formát, který chcete kontrolovat.  
  
 `ContainsImage` Pomocí funkce určíte, zda jsou data obsažená ve schránce obrázkem. Následující kód zkontroluje, zda se jedná o odpovídající obrázek a sestavy.  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a>Vymazávání schránky  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Metoda vymaže schránku. Vzhledem k tomu, že schránka sdílí jiné procesy, její zrušení může mít vliv na tyto procesy.  
  
 Následující kód ukazuje, jak použít `Clear` metodu.  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a>Zápis do schránky  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> Použijte metodu k zápisu textu do schránky. Následující kód zapíše řetězec "Toto je testovací řetězec" do schránky.  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 Metoda může přijmout parametr formátu, který obsahuje <xref:System.Windows.Forms.TextDataFormat>typ. `SetText` Následující kód zapíše řetězec "Toto je testovací řetězec" do schránky jako text RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> Použijte metodu pro zápis dat do schránky. Tento příklad zapíše `DataObject` `dataChunk` do schránky ve vlastním formátu `specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> Použijte metodu pro zápis zvukových dat do schránky. Tento příklad vytvoří bajtové pole `musicReader`, přečte soubor `cool.wav` do něj a pak ho zapíše do schránky.  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> Vzhledem k tomu, že je možné k schránce získat jiní uživatelé, nepoužívejte ji k ukládání citlivých informací, jako jsou hesla nebo důvěrná data.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Postupy: Čtení dat objektů ze souboru XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Postupy: Zápis dat objektů do souboru XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
