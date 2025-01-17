---
title: 'Postupy: Extrahování ikony přidružené k souboru v modelu Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: c3173a3fa756a3294154217f5cf0a13dbc8721f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645403"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Postupy: Extrahování ikony přidružené k souboru v modelu Windows Forms
Mnoho souborů s vloženými ikony, které poskytují vizuální znázornění přidružený soubor typu. Například Microsoft Word dokumenty obsahují ikonu, která je identifikuje jako dokumentů aplikace Word. Při zobrazování souborů do ovládacího prvku seznamu nebo ovládacího prvku tabulky, můžete zobrazit ikonu představující typ souboru vedle názvu každého souboru. Můžete to provést jednoduše pomocí <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak k extrahování ikony přidružené k souboru a zobrazení názvu souboru a jeho přidružené ikonu v <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li příklad zkompilovat:  
  
- Předchozí kód vložte do formuláře Windows a volání `ExtractAssociatedIconExample` metodu z konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metody zpracování událostí.  
  
     Budete muset Ujistěte se, že váš formulář importuje <xref:System.IO> oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Ovládací prvek ListView](../controls/listview-control-windows-forms.md)
