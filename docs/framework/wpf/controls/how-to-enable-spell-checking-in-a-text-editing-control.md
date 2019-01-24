---
title: 'Postupy: Povolení kontroly pravopisu v ovládacím prvku pro úpravy textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- spellchecking [WPF]
- real-time spellchecking
- TextBox control [WPF], real-time spellchecking
- spelling checker [WPF]
- checking spelling [WPF]
ms.assetid: 6f953d2b-67e8-4012-84ce-53c0e958da47
ms.openlocfilehash: 7a394be98e86bb34cb8fe37b1c5c166417587394
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605627"
---
# <a name="how-to-enable-spell-checking-in-a-text-editing-control"></a>Postupy: Povolení kontroly pravopisu v ovládacím prvku pro úpravy textu
Následující příklad ukazuje, jak povolit kontrolu pravopisu v reálném čase <xref:System.Windows.Controls.TextBox> pomocí <xref:System.Windows.Controls.SpellCheck.IsEnabled%2A> vlastnost <xref:System.Windows.Controls.SpellCheck> třídy.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellCheckExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/spellcheckexample.xaml#spellcheckexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_procedural_snip#SpellCheckCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_procedural_snip/CSharp/SpellCheckExample.cs#spellcheckcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_procedural_snip#SpellCheckCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_procedural_snip/visualbasic/spellcheckexample.vb#spellcheckcodeexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- [Použití kontroly pravopisu s místní nabídkou](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)
- [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
