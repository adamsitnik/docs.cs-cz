---
title: 'Postupy: Seznam datových formátů v datovém objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
ms.openlocfilehash: f8230eac33a18a0d99cc757d54c2b901c1afe977
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077742"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="d6b6e-102">Postupy: Seznam datových formátů v datovém objektu</span><span class="sxs-lookup"><span data-stu-id="d6b6e-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="d6b6e-103">Následující příklady ukazují, jak používat <xref:System.Windows.DataObject.GetFormats%2A> přetížení metody get pole řetězců, které označuje každou formát dat, který je k dispozici v datovém objektu.</span><span class="sxs-lookup"><span data-stu-id="d6b6e-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6b6e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6b6e-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d6b6e-105">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b6e-105">Description</span></span>  
 <span data-ttu-id="d6b6e-106">Následující příklad kódu používá <xref:System.Windows.DataObject.GetFormats%2A> přetížení pro získání pole řetězců, které označuje všechny datových formátů do datového objektu (nativní a automaticky převoditelné).</span><span class="sxs-lookup"><span data-stu-id="d6b6e-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="d6b6e-107">Kód</span><span class="sxs-lookup"><span data-stu-id="d6b6e-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="d6b6e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6b6e-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d6b6e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b6e-109">Description</span></span>  
 <span data-ttu-id="d6b6e-110">Následující příklad kódu používá <xref:System.Windows.DataObject.GetFormats%2A> přetížení pro získání pole řetězců, které označuje pouze datových formátů do datového objektu (formáty jsou filtrovány lze automaticky převést data) k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d6b6e-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="d6b6e-111">Kód</span><span class="sxs-lookup"><span data-stu-id="d6b6e-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="d6b6e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6b6e-112">See also</span></span>

- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="d6b6e-113">Přehled přetažení</span><span class="sxs-lookup"><span data-stu-id="d6b6e-113">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
