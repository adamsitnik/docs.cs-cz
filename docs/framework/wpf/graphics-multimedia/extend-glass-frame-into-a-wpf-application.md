---
title: Rozšíření skleněného rámečku do aplikace WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
ms.openlocfilehash: d7a00f2508769534e49c965d098dbacb01a1f189
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843529"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a><span data-ttu-id="f3289-102">Rozšíření skleněného rámečku do aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="f3289-102">Extend Glass Frame Into a WPF Application</span></span>

<span data-ttu-id="f3289-103">Toto téma ukazuje, jak rozšířit [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] skleněného rámečku do aplikace Windows Presentation Foundation (WPF) v oblasti klienta.</span><span class="sxs-lookup"><span data-stu-id="f3289-103">This topic demonstrates how to extend the [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] glass frame into the client area of a Windows Presentation Foundation (WPF) application.</span></span>

> [!NOTE]
> <span data-ttu-id="f3289-104">Tento příklad bude fungovat jenom na [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] počítač Správce oken plochy (DWM) pomocí skla povolena.</span><span class="sxs-lookup"><span data-stu-id="f3289-104">This example will only work on a [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] machine running the Desktop Window Manager (DWM) with glass enabled.</span></span> [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] <span data-ttu-id="f3289-105">Edice Home Basic nepodporuje efekt skla transparentní.</span><span class="sxs-lookup"><span data-stu-id="f3289-105">Home Basic edition does not support the transparent glass effect.</span></span> <span data-ttu-id="f3289-106">Oblasti, které by obvykle vykreslení s efekt skla transparentní na jinou edici [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] jsou generovány neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="f3289-106">Areas that would typically render with the transparent glass effect on other editions of [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] are rendered opaque.</span></span>

## <a name="example"></a><span data-ttu-id="f3289-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3289-107">Example</span></span>

<span data-ttu-id="f3289-108">Následující obrázek ukazuje skleněného rámečku rozšířit do adresa aplikace Internet Explorer 7.</span><span class="sxs-lookup"><span data-stu-id="f3289-108">The following image illustrates the glass frame extended into the address bar of Internet Explorer 7.</span></span>

<span data-ttu-id="f3289-109">**Internet Explorer s rozšířenou skleněného rámečku za adresního řádku.**</span><span class="sxs-lookup"><span data-stu-id="f3289-109">**Internet Explorer with extended glass frame behind address bar.**</span></span>

<span data-ttu-id="f3289-110">![Aplikace Internet Explorer 7 s rozšířeným za adresního řádku skleněného rámečku. ](./media/ie7glasstopbar.PNG "IE7glasstopbar")</span><span class="sxs-lookup"><span data-stu-id="f3289-110">![IE7 with glass frame extended behind address bar.](./media/ie7glasstopbar.PNG "IE7glasstopbar")</span></span>

<span data-ttu-id="f3289-111">Rozšíření skleněného rámečku na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací, přístupu k nespravované [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] je potřeba.</span><span class="sxs-lookup"><span data-stu-id="f3289-111">To extend the glass frame on a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application, access to unmanaged [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] is needed.</span></span> <span data-ttu-id="f3289-112">Následující příklad kódu nemá nespravovaného kódu (pinvoke) pro dva [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] potřeba splnit pro rozšíření rámce do klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="f3289-112">The following code example does a Platform Invoke (pinvoke) for the two [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] needed to extend the frame into the client area.</span></span> <span data-ttu-id="f3289-113">Každá z těchto [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] jsou deklarovány ve třídě volá **NonClientRegionAPI**.</span><span class="sxs-lookup"><span data-stu-id="f3289-113">Each of these [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] are declared in a class called **NonClientRegionAPI**.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential)]
public struct MARGINS
{
    public int cxLeftWidth;      // width of left border that retains its size
    public int cxRightWidth;     // width of right border that retains its size
    public int cyTopHeight;      // height of top border that retains its size
    public int cyBottomHeight;   // height of bottom border that retains its size
};

[DllImport("DwmApi.dll")]
public static extern int DwmExtendFrameIntoClientArea(
    IntPtr hwnd,
    ref MARGINS pMarInset);
```

```vb
<StructLayout(LayoutKind.Sequential)>
Public Structure MARGINS
    Public cxLeftWidth As Integer ' width of left border that retains its size
    Public cxRightWidth As Integer ' width of right border that retains its size
    Public cyTopHeight As Integer ' height of top border that retains its size
    Public cyBottomHeight As Integer ' height of bottom border that retains its size
End Structure

<DllImport("DwmApi.dll")>
Public Shared Function DwmExtendFrameIntoClientArea(ByVal hwnd As IntPtr, ByRef pMarInset As MARGINS) As Integer
End Function
```

<span data-ttu-id="f3289-114">[Dwmextendframeintoclientarea –](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) je funkce Správce oken plochy, která rozšiřuje rámce do klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="f3289-114">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) is the DWM function that extends the frame into the client area.</span></span> <span data-ttu-id="f3289-115">Přebírá dva parametry; Popisovač okna a [OKRAJE](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) struktury.</span><span class="sxs-lookup"><span data-stu-id="f3289-115">It takes two parameters; a window handle and a [MARGINS](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) structure.</span></span> <span data-ttu-id="f3289-116">[OKRAJE](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) Správce oken plochy pozná, kolik dalších rámce by měl být rozšířena na klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="f3289-116">[MARGINS](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) is used to tell the DWM how much extra the frame should be extended into the client area.</span></span>

## <a name="example"></a><span data-ttu-id="f3289-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3289-117">Example</span></span>

<span data-ttu-id="f3289-118">Použít [dwmextendframeintoclientarea –](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) funkce, je potřeba pořídit popisovač okna.</span><span class="sxs-lookup"><span data-stu-id="f3289-118">To use the [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) function, a window handle must be obtained.</span></span> <span data-ttu-id="f3289-119">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], můžete získat popisovač okna <xref:System.Windows.Interop.HwndSource.Handle%2A> vlastnost <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="f3289-119">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], the window handle can be obtained from the <xref:System.Windows.Interop.HwndSource.Handle%2A> property of an <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="f3289-120">V následujícím příkladu je na rámce rozšíří do klientské oblasti <xref:System.Windows.FrameworkElement.Loaded> událostí okna.</span><span class="sxs-lookup"><span data-stu-id="f3289-120">In the following example, the frame is extended into the client area on the <xref:System.Windows.FrameworkElement.Loaded> event of the window.</span></span>

```csharp
void OnLoaded(object sender, RoutedEventArgs e)
{
   try
   {
      // Obtain the window handle for WPF application
      IntPtr mainWindowPtr = new WindowInteropHelper(this).Handle;
      HwndSource mainWindowSrc = HwndSource.FromHwnd(mainWindowPtr);
      mainWindowSrc.CompositionTarget.BackgroundColor = Color.FromArgb(0, 0, 0, 0);

      // Get System Dpi
      System.Drawing.Graphics desktop = System.Drawing.Graphics.FromHwnd(mainWindowPtr);
      float DesktopDpiX = desktop.DpiX;
      float DesktopDpiY = desktop.DpiY;

      // Set Margins
      NonClientRegionAPI.MARGINS margins = new NonClientRegionAPI.MARGINS();

      // Extend glass frame into client area
      // Note that the default desktop Dpi is 96dpi. The  margins are
      // adjusted for the system Dpi.
      margins.cxLeftWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cxRightWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cyTopHeight = Convert.ToInt32(((int)topBar.ActualHeight + 5) * (DesktopDpiX / 96));
      margins.cyBottomHeight = Convert.ToInt32(5 * (DesktopDpiX / 96));

      int hr = NonClientRegionAPI.DwmExtendFrameIntoClientArea(mainWindowSrc.Handle, ref margins);
      //
      if (hr < 0)
      {
         //DwmExtendFrameIntoClientArea Failed
      }
   }
   // If not Vista, paint background white.
   catch (DllNotFoundException)
   {
      Application.Current.MainWindow.Background = Brushes.White;
   }
}
```

## <a name="example"></a><span data-ttu-id="f3289-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3289-121">Example</span></span>

<span data-ttu-id="f3289-122">Následující příklad ukazuje, jednoduché okno, ve kterém je rámec rozšíří do klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="f3289-122">The following example shows a simple window in which the frame is extended into the client area.</span></span> <span data-ttu-id="f3289-123">Snímek je rozšířená za horního ohraničení, která obsahuje dvě <xref:System.Windows.Controls.TextBox> objekty.</span><span class="sxs-lookup"><span data-stu-id="f3289-123">The frame is extended behind the top border that contains the two <xref:System.Windows.Controls.TextBox> objects.</span></span>

```xaml
<Window x:Class="SDKSample.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Extended Glass in WPF" Height="300" Width="400"
    Loaded="OnLoaded" Background="Transparent"
    >
  <Grid ShowGridLines="True">
    <DockPanel Name="mainDock">
      <!-- The border is used to compute the rendered height with margins.
           topBar contents will be displayed on the extended glass frame.-->
      <Border Name="topBar" DockPanel.Dock="Top" >
        <Grid Name="grid">
          <Grid.ColumnDefinitions>
            <ColumnDefinition MinWidth="100" Width="*"/>
            <ColumnDefinition Width="Auto"/>
          </Grid.ColumnDefinitions>
          <TextBox Grid.Column="0" MinWidth="100" Margin="0,0,10,5">Path</TextBox>
          <TextBox Grid.Column="1" MinWidth="75" Margin="0,0,0,5">Search</TextBox>
        </Grid>
      </Border>
      <Grid DockPanel.Dock="Top" >
        <Grid.ColumnDefinitions>
          <ColumnDefinition/>
        </Grid.ColumnDefinitions>
        <TextBox Grid.Column="0" AcceptsReturn="True"/>
      </Grid>
    </DockPanel>
  </Grid>
</Window>
```

<span data-ttu-id="f3289-124">Následující obrázek ukazuje skleněného rámečku do rozšířené [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="f3289-124">The following image illustrates the glass frame extended into a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application.</span></span>

<span data-ttu-id="f3289-125">**Rozšíří skleněného rámečku do**[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]**aplikace.**</span><span class="sxs-lookup"><span data-stu-id="f3289-125">**Glass Frame Extended into a**  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  **Application.**</span></span>

<span data-ttu-id="f3289-126">![Skleněného rámečku rozšíří do aplikace WPF. ](./media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")</span><span class="sxs-lookup"><span data-stu-id="f3289-126">![Glass Frame Extended into a WPF application.](./media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")</span></span>

## <a name="see-also"></a><span data-ttu-id="f3289-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3289-127">See also</span></span>

- [<span data-ttu-id="f3289-128">Přehled Správce oken plochy</span><span class="sxs-lookup"><span data-stu-id="f3289-128">Desktop Window Manager Overview</span></span>](/windows/desktop/dwm/dwm-overview)
- [<span data-ttu-id="f3289-129">Přehled Správce oken plochy rozostření</span><span class="sxs-lookup"><span data-stu-id="f3289-129">Desktop Window Manager Blur Overview</span></span>](/windows/desktop/dwm/blur-ovw)
- [<span data-ttu-id="f3289-130">DwmExtendFrameIntoClientArea</span><span class="sxs-lookup"><span data-stu-id="f3289-130">DwmExtendFrameIntoClientArea</span></span>](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
