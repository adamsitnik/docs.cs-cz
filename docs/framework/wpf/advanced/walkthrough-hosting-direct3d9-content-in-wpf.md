---
title: 'Návod: Hostování obsahu Direct3D9 ve WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 2c31c044aa50a74255a61da1675037ab3d09f615
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053454"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>Návod: Hostování obsahu Direct3D9 ve WPF

Tento návod ukazuje, jak hostovat Direct3D9 obsah v aplikaci Windows Presentation Foundation (WPF).

V tomto návodu provedete následující úlohy:

- Vytvořte projekt WPF pro hostování obsahu Direct3D9.

- Importujte obsah Direct3D9.

- Zobrazte obsah Direct3D9 pomocí <xref:System.Windows.Interop.D3DImage> třídy.

 Po dokončení budete znát způsob hostování Direct3D9 obsahu v aplikaci WPF.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio.

- DirectX SDK 9 nebo novější.

- Knihovna DLL, která obsahuje obsah Direct3D9 ve formátu kompatibilním s WPF. Další informace najdete v tématu spolupráce [a postupy pro [WPF a Direct3D9](wpf-and-direct3d9-interoperation.md) : Vytváření obsahu Direct3D9 pro hostování v subsystému WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).

## <a name="creating-the-wpf-project"></a>Vytvoření projektu WPF

Prvním krokem je vytvoření projektu pro aplikaci WPF.

### <a name="to-create-the-wpf-project"></a>Vytvoření projektu WPF

Vytvořte nový projekt aplikace WPF v jazyce Visual C# s `D3DHost`názvem. Další informace najdete v tématu [Návod: Moje první desktopová aplikace](../getting-started/walkthrough-my-first-wpf-desktop-application.md)WPF.

MainWindow. XAML se otevře v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

## <a name="importing-the-direct3d9-content"></a>Import obsahu Direct3D9

Obsah Direct3D9 importujete z nespravované knihovny DLL pomocí `DllImport` atributu.

### <a name="to-import-direct3d9-content"></a>Import obsahu Direct3D9

1. Otevřete MainWindow.xaml.cs v editoru kódu.

2. Nahraďte automaticky generovaný kód následujícím kódem.

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a>Hostování obsahu Direct3D9

Nakonec použijte <xref:System.Windows.Interop.D3DImage> třídu pro hostování obsahu Direct3D9.

### <a name="to-host-the-direct3d9-content"></a>Hostování obsahu Direct3D9

1. V souboru MainWindow. xaml nahraďte automaticky generovaný kód XAML následujícím XAML.

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. Sestavte projekt.

3. Zkopírujte knihovnu DLL obsahující obsah Direct3D9 do složky bin/Debug.

4. Stisknutím klávesy F5 spusťte projekt.

    Obsah Direct3D9 se zobrazí v aplikaci WPF.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.D3DImage>
- [Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
