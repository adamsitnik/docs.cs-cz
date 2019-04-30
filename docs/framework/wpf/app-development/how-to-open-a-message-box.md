---
title: 'Postupy: Otevření okna se zprávou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: cf7534cdee5e17d53e95294573023d660135e395
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947690"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="f0cc4-102">Postupy: Otevření okna se zprávou</span><span class="sxs-lookup"><span data-stu-id="f0cc4-102">How to: Open a Message Box</span></span>
<span data-ttu-id="f0cc4-103">Tento příklad ukazuje, jak otevřít okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="f0cc4-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0cc4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0cc4-104">Example</span></span>  
 <span data-ttu-id="f0cc4-105">Okno se zprávou je prefabrikované modální dialogové okno pro zobrazení informací o uživateli.</span><span class="sxs-lookup"><span data-stu-id="f0cc4-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="f0cc4-106">Zavoláním statické se otevře okno se zprávou <xref:System.Windows.MessageBox.Show%2A> metodu <xref:System.Windows.MessageBox> třídy.</span><span class="sxs-lookup"><span data-stu-id="f0cc4-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="f0cc4-107">Když <xref:System.Windows.MessageBox.Show%2A> je volána, předávání zpráv pomocí parametru řetězce.</span><span class="sxs-lookup"><span data-stu-id="f0cc4-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="f0cc4-108">Několik přetížení <xref:System.Windows.MessageBox.Show%2A> umožňují konfigurovat, jak se zobrazí okno se zprávou (viz <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="f0cc4-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="f0cc4-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0cc4-109">See also</span></span>

- [<span data-ttu-id="f0cc4-110">Ukázka MessageBox</span><span class="sxs-lookup"><span data-stu-id="f0cc4-110">MessageBox Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160023)
