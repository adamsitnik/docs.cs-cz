---
title: 'Postupy: Vytvoření ovládacího prvku obsahujícího přístupový klíč a zalamování textu'
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: 48e439719afa2426b5d8f822c621080cdc32514e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174041"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a><span data-ttu-id="b4dd0-102">Postupy: Vytvoření ovládacího prvku obsahujícího přístupový klíč a zalamování textu</span><span class="sxs-lookup"><span data-stu-id="b4dd0-102">How to: Create a Control That Has an Access Key and Text Wrapping</span></span>
<span data-ttu-id="b4dd0-103">Tento příklad ukazuje, jak vytvořit ovládací prvek, který má přístupové klávesy a podporuje zalamování textu.</span><span class="sxs-lookup"><span data-stu-id="b4dd0-103">This example shows how to create a control that has an access key and supports text wrapping.</span></span> <span data-ttu-id="b4dd0-104">V příkladu se používá <xref:System.Windows.Controls.Label> ovládací prvek pro ilustraci těchto konceptů.</span><span class="sxs-lookup"><span data-stu-id="b4dd0-104">The example uses a <xref:System.Windows.Controls.Label> control to illustrate these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4dd0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4dd0-105">Example</span></span>  
 **<span data-ttu-id="b4dd0-106">Přidat zalamování textu popisku</span><span class="sxs-lookup"><span data-stu-id="b4dd0-106">Add Text Wrapping to Your Label</span></span>**  
  
 <span data-ttu-id="b4dd0-107"><xref:System.Windows.Controls.Label> Ovládací prvek nepodporuje zalamování textu.</span><span class="sxs-lookup"><span data-stu-id="b4dd0-107">The <xref:System.Windows.Controls.Label> control does not support text wrapping.</span></span> <span data-ttu-id="b4dd0-108">Pokud potřebujete popisek, který obtéká přes více řádků, je možné vnořovat jiný element, který nepodporuje text zabalení a vložit element uvnitř popisek.</span><span class="sxs-lookup"><span data-stu-id="b4dd0-108">If you need a label that wraps across multiple lines, you can nest another element that does support text wrapping and put the element inside the label.</span></span> <span data-ttu-id="b4dd0-109">Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.TextBlock> má být popisek, který obtéká několik řádků textu.</span><span class="sxs-lookup"><span data-stu-id="b4dd0-109">The following example shows how to use a <xref:System.Windows.Controls.TextBlock> to make a label that wraps several lines of text.</span></span>  
  
 [!code-xaml[LabelSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **<span data-ttu-id="b4dd0-110">Přidat přístupový klíč a zalamování textu do popisku</span><span class="sxs-lookup"><span data-stu-id="b4dd0-110">Add an Access Key and Text Wrapping to Your Label</span></span>**  
  
 <span data-ttu-id="b4dd0-111">Pokud potřebujete <xref:System.Windows.Controls.Label> , který má přístupový klíč (symbol), použijte <xref:System.Windows.Controls.AccessText> element, který se nachází uvnitř <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="b4dd0-111">If you need a <xref:System.Windows.Controls.Label> that has an access key (mnemonic), use the <xref:System.Windows.Controls.AccessText> element that is inside the <xref:System.Windows.Controls.Label>.</span></span>  
  
 <span data-ttu-id="b4dd0-112">Ovládací prvky jako například <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, a <xref:System.Windows.Controls.GroupBox> mají výchozí šablony ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b4dd0-112">Controls such as <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, and <xref:System.Windows.Controls.GroupBox> have default control templates.</span></span> <span data-ttu-id="b4dd0-113">Tyto šablony obsahují <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="b4dd0-113">These templates contain a <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="b4dd0-114">Jedna z vlastností, které můžete nastavit na <xref:System.Windows.Controls.ContentPresenter> je <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", který můžete použít k určení přístupového klíče pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b4dd0-114">One of the properties that you can set on the <xref:System.Windows.Controls.ContentPresenter> is <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true", which you can use to specify an access key for the control.</span></span>  
  
 <span data-ttu-id="b4dd0-115">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Label> , který má přístupové klávesy a podporuje zalamování textu.</span><span class="sxs-lookup"><span data-stu-id="b4dd0-115">The following example shows how to create a <xref:System.Windows.Controls.Label> that has an access key and supports text wrapping.</span></span> <span data-ttu-id="b4dd0-116">Chcete-li povolit zalamování textu, příklad nastaví <xref:System.Windows.Controls.AccessText.TextWrapping%2A> vlastnosti a používá znak podtržení určit přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="b4dd0-116">To enable text wrapping, the example sets the <xref:System.Windows.Controls.AccessText.TextWrapping%2A> property and uses an underline character to specify the access key.</span></span> <span data-ttu-id="b4dd0-117">(Znak, který následuje znak podtržení se přístupový klíč).</span><span class="sxs-lookup"><span data-stu-id="b4dd0-117">(The character that immediately follows the underline character is the access key.)</span></span>  
  
 [!code-xaml[LabelSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b4dd0-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4dd0-118">See also</span></span>

- [<span data-ttu-id="b4dd0-119">Postupy: Nastavte vlastnost Target tohoto popisku</span><span class="sxs-lookup"><span data-stu-id="b4dd0-119">How to: Set the Target Property of a Label</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752101(v=vs.90))
