---
title: 'Postupy: Připojení k webové službě'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
ms.openlocfilehash: 76fa13d4a12362d04c832fd59ee69db5a6811029
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454456"
---
# <a name="how-to-bind-to-a-web-service"></a>Postupy: Připojení k webové službě
Tento příklad ukazuje, jak vytvořit vazby k objektům vráceným voláními metody webové služby.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá [služba obsahu MTPS (MSDN/TechNet Publishing System)](https://go.microsoft.com/fwlink/?LinkId=95677) k načtení seznamu jazyků podporovaných zadaným dokumentem.  
  
 Před voláním webové služby je nutné vytvořit odkaz na ni. Chcete-li vytvořit webový odkaz na službu MTPS pomocí sady Visual Studio, postupujte podle následujících kroků:  
  
1. Otevřete projekt v aplikaci Visual Studio.  
  
2. V nabídce **projekt** klikněte na příkaz **Přidat webový odkaz**.  
  
3. V dialogovém okně nastavte **adresu URL** na [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4. Stiskněte tlačítko **Přejít** a pak **Přidat odkaz**.  
  
 Dále zavoláte metodu webové služby a nastavíte <xref:System.Windows.FrameworkElement.DataContext%2A> příslušného ovládacího prvku nebo okna na vrácený objekt. Metoda `GetContent` služby MTPS používá odkaz na objekt `getContentRequest`. Proto následující příklad nejprve nastaví objekt žádosti:  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Po nastavení <xref:System.Windows.FrameworkElement.DataContext%2A> můžete vytvořit vazby na vlastnosti objektu, na který byl <xref:System.Windows.FrameworkElement.DataContext%2A> nastaven. V tomto příkladu je <xref:System.Windows.FrameworkElement.DataContext%2A> nastavena na objekt `getContentResponse` vrácený metodou `GetContent`. V následujícím příkladu se <xref:System.Windows.Controls.ItemsControl> váže k a zobrazí `locale` hodnoty `availableVersionsAndLocales` `getContentResponse`.  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Informace o struktuře `getContentResponse`najdete v [dokumentaci ke službě obsahu](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled zdrojů vazby](binding-sources-overview.md)
- [Zpřístupnění dat pro vazbu v jazyku XAML](how-to-make-data-available-for-binding-in-xaml.md)
