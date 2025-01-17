---
title: Datové vazby v klientovi Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: b0f1eb8ca154ab8e37a15b35097f746662511f7c
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928624"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Datové vazby v klientovi Windows Presentation Foundation
Tato ukázka demonstruje použití datových vazeb v klientu Windows Presentation Foundation (WPF). Ukázka používá službu Windows Communication Foundation (WCF), která náhodně generuje pole alb pro návrat do klienta. Každé album má název, cenu a seznam skladeb alba. Stopy alba mají název a dobu trvání. Informace, které služba vrací, jsou automaticky svázány s uživatelským rozhraním (UI) poskytovaným klientem Windows Presentation Foundation (WPF).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Datová vazba umožňuje, aby byl zdroj dat automaticky svázán s uživatelským rozhraním. Tím se zjednoduší programovací model, protože nevyžaduje, abyste programově aktualizovali jednotlivé prvky uživatelského rozhraní daty z datového objektu nebo pole datových objektů. Můžete vytvořit vazby objektu k jednomu prvku uživatelského rozhraní nebo poli k ovládacímu prvku, který přijímá více vstupů, jako je `ListBox`například. Následující kód ukazuje, jak vytvořit vazby dat k `DataContext` prvku uživatelského rozhraní.  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 V `DataContext` předchozím příkladu `grid` jeprvek`myPanel` rozložení s názvem nastaven na data vrácená metodou.`GetAlbumList` `DataContext` Umožňuje elementům zdědit informace z jejich nadřazených prvků o zdroji dat, který se používá pro vazbu, a také k dalším charakteristikám vazby, jako je například cesta. Řádek kódu musí být proveden při každém aktualizování dat na serveru. Například se spustí při inicializaci okna a přidání nového alba.  
  
 V následujícím ukázkovém kódu `ListBox` jazyka XAML určuje. `ItemsSource="{Binding }"`  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 To určuje, že data vázaná na prvek uživatelského rozhraní nejvyšší úrovně jsou také svázána s tímto ovládacím prvkem (tj. polem alba). Kromě toho `ItemTemplate="{StaticResource AlbumStyle}"` Určuje šablonu dat, která se má použít pro každou položku `ListBox`v. Můžete také definovat datové šablony, abyste určili, jak mají být data formátována. Tyto datové šablony lze znovu použít pro jiné prvky uživatelského rozhraní v aplikaci. výhodou je, že je šablona dat definována a udržována na jednom místě.  
  
 Šablona `AlbumStyle` dat obsahuje mřížku dvou `TextBlock`souběžně. Jedna Určuje název alba a druhý počet stop v albu.  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 Následující kód XAML vytvoří sekundu `ListBox`.  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 Kód určuje cestu pro `ItemsSource`. To značí, že data vázaná na tento ovládací prvek nejsou data nejvyšší úrovně, ale vlastnost dat nejvyšší úrovně s názvem `Tracks`. Tato vlastnost představuje pole stop obsažených v albu. Kromě toho je určena jiná `DataTemplate` pojmenovaná `TrackStyle` . Rozložení `TrackStyle` šablony je podobné jako `AlbumStyle` šablona, ale `TextBlock`s je svázána s různými vlastnostmi. Důvodem je to, že dvě šablony jsou používány s různými datovými objekty.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
