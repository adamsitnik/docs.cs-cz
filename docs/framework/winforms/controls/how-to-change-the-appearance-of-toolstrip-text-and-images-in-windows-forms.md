---
title: 'Postupy: Změna vzhledu textu a obrázků ToolStrip ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: cf2f332b17bf6ff5b6ffb7cbc2d5777649728ec6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650847"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Postupy: Změna vzhledu textu a obrázků ToolStrip ve Windows Forms
Můžete řídit, zda text a obrázky jsou zobrazeny na <xref:System.Windows.Forms.ToolStripItem> a jak jsou zarovnány relativně vůči sobě navzájem a <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Chcete-li definovat, co se zobrazí na prvku ToolStripItem  
  
- Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost na požadovanou hodnotu. Možnosti jsou `Image`, `ImageAndText`, `None`, a `Text`. Výchozí hodnota je `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Zarovnání textu v prvku ToolStripItem  
  
- Nastavte <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> vlastnost na požadovanou hodnotu. Možnosti jsou kombinací nejvyšší, střední a dolní část s vlevo, na střed a doprava. Výchozí hodnota je `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Chcete-li Zarovnat obrázek na prvku ToolStripItem  
  
- Nastavte <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> vlastnost na požadovanou hodnotu. Možnosti jsou kombinací nejvyšší, střední a dolní část s vlevo, na střed a doprava. Výchozí hodnota je `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Chcete-li definovat, jak ovládací prvek ToolStripItem text a obrázky se zobrazí relativně vůči sobě navzájem  
  
- Nastavte <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> vlastnost na požadovanou hodnotu. Možnosti jsou `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, a `TextBeforeImage`. Výchozí hodnota je `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Shrnutí technologie ToolStrip](toolstrip-technology-summary.md)
