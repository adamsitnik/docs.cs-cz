---
title: 'Postupy: Analýza cest k souborům v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 6961f481126d34b18c5a11d83c4c6c37c2c81c71
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64629169"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Postupy: Analýza cest k souborům v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem> Objekt nabízí celou řadu užitečných metod při analýze cesty k souborům.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Metoda přijímá dvě cesty a vrátí správně formátovaná kombinovanou cestu.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Metoda vrátí absolutní cesta nadřazeného člena zadané cestě.  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Metoda vrátí hodnotu <xref:System.IO.FileInfo> objekt, který může být dotazována k určení vlastností souboru, například jeho název a cesta.  
  
 Rozhodování o obsahu souboru neřiďte příponou názvu souboru. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.  
  
### <a name="to-determine-a-files-name-and-path"></a>Chcete-li zjistit název a cesta k souboru  
  
- Použití <xref:System.IO.FileInfo.DirectoryName%2A> a <xref:System.IO.FileInfo.Name%2A> vlastnosti <xref:System.IO.FileInfo> objektu určit název a cesta k souboru. Tento příklad určuje název a cestu a zobrazí je.  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Kombinovat adresář k vytvoření úplnou cestu a název souboru  
  
- Použití `CombinePath` metodu adresáře a názvu. V tomto příkladu přebírá řetězce `folderPath` a `fileName` vytvořili v předchozím příkladu, sloučí a zobrazí výsledek.  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [Postupy: Získání kolekce souborů v adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
