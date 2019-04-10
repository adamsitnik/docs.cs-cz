---
title: 'Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
ms.openlocfilehash: c5668bd056c180f2cdf9b6160aa4d96e2ac2f5f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228598"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a>Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C\#
S [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], můžete vytvořit výkonné vlastní ovládací prvky prostřednictvím *dědičnosti*. Prostřednictvím dědičnosti je možné vytvořit ovládací prvky, které zachovat všechny vlastní funkce standardní ovládací prvky Windows Forms, ale také začlenit vlastní funkce. V tomto návodu vytvoříte jednoduchý volá zděděný ovládací prvek `ValueButton`. Toto tlačítko bude funkce dědit ze standardních formulářů Windows <xref:System.Windows.Forms.Button> řídit a bude vystavovat vlastní vlastnost s názvem `ButtonValue`.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Když vytvoříte nový projekt, zadejte jeho název nastavit kořenový obor názvů, název sestavení a název projektu a ujistěte se, že součást výchozí bude v správný obor názvů.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Chcete-li vytvořit ValueButtonLib Knihovna ovládacích prvků a ovládací prvek ValueButton  
  
1.  Na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu** otevřete **nový projekt** dialogové okno.  
  
2.  Vyberte **Knihovna ovládacích prvků Windows Forms** šablonu projektu ze seznamu Projekty Visual C# a typ `ValueButtonLib` v **název** pole.  
  
     Název projektu `ValueButtonLib`, je také přiřazený k oboru názvů root ve výchozím nastavení. Kořenový obor názvů se používá k určení názvů součástí sestavení. Například, pokud se dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete zadat vaše `ValueButton` pomocí komponenty `ValueButtonLib.ValueButton`. Další informace najdete v tématu [obory názvů](../../../csharp/programming-guide/namespaces/index.md).  
  
3.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **UserControl1.cs**, klikněte na tlačítko **přejmenovat** z místní nabídky. Změňte název souboru, aby `ValueButton.cs`. Klikněte na tlačítko **Ano** tlačítko, pokud budete vyzváni, pokud chcete přejmenovat všechny odkazy na prvek kódu '`UserControl1`".  
  
4.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ValueButton.cs** a vyberte **zobrazit kód**.  
  
5.  Vyhledejte `class` řádek příkazu `public partial class ValueButton`a změňte typ, ze kterého dědí tohoto ovládacího prvku z <xref:System.Windows.Forms.UserControl> k <xref:System.Windows.Forms.Button>. To umožňuje dědí všechny funkce, které jsou součástí zděděný ovládací prvek <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
6.  V **Průzkumníka řešení**, otevřete **ValueButton.cs** uzel k zobrazení souboru kód generovaný návrhářem **ValueButton.Designer.cs**. Tento soubor otevřít v **Editor kódu**.  
  
7.  Vyhledejte `InitializeComponent` metoda a odebrat řádek, který se přiřadí <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> vlastnost. Tato vlastnost neexistuje v <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
8.  Z **souboru** nabídce zvolte **Uložit vše** chcete projekt uložit.  
  
    > [!NOTE]
    >  Vizuálního návrháře již není k dispozici. Vzhledem k tomu, <xref:System.Windows.Forms.Button> ovládací prvek provede vlastní vykreslovací, nemůžete změnit její vzhled v návrháři. Jeho vizuální znázornění byla přesně stejná jako, který dědí z třídy (to znamená <xref:System.Windows.Forms.Button>) není-li upravit v kódu. Součásti, které mají bez prvků uživatelského rozhraní, stále můžete přidat na návrhovou plochu.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Přidání vlastnosti do zděděný ovládací prvek  
 Je to možné užívání zděděný ovládací prvky Windows Forms je vytváření ovládacích prvků, které jsou stejné ve vzhledu a chování standardní ovládací prvky Windows Forms, ale vystavovat vlastní vlastnosti. V této části přidáte vlastnost s názvem `ButtonValue` do ovládacího prvku.  
  
#### <a name="to-add-the-value-property"></a>Chcete-li přidat vlastnost Value  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ValueButton.cs**a potom klikněte na tlačítko **zobrazit kód** z místní nabídky.  
  
2.  Vyhledejte `class` příkazu. Ihned po `{`, zadejte následující kód:  
  
    ```csharp  
    // Creates the private variable that will store the value of your   
    // property.  
    private int varValue;  
    // Declares the property.  
    public int ButtonValue  
    {  
       // Sets the method for retrieving the value of your property.  
       get  
       {  
          return varValue;  
       }  
       // Sets the method for setting the value of your property.  
       set  
       {  
          varValue = value;  
       }  
    }  
    ```  
  
     Tento kód nastaví metody, pomocí kterého `ButtonValue` vlastnost je uložená a načíst. `get` Příkaz nastaví hodnotu vrácenou hodnotu, která je uložen v soukromé proměnné `varValue`a `set` příkaz nastaví hodnotu vlastnosti soukromé proměnné pomocí `value` – klíčové slovo.  
  
3.  Z **souboru** nabídce zvolte **Uložit vše** chcete projekt uložit.  
  
## <a name="testing-your-control"></a>Testování ovládacího prvku  
 Ovládací prvky nejsou samostatné projekty; musí být uložen v kontejneru. Pokud chcete otestovat ovládacího prvku, je nutné zadat testovací projekt, ke spuštění v. Musíte také zajistit ovládacího prvku přístupné pro testovací projekt sestavením (kompilace) ji. V této části bude sestavení ovládacího prvku a otestovat ho ve formuláři Windows.  
  
#### <a name="to-build-your-control"></a>K sestavení ovládacího prvku  
  
1.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     Sestavení by měl být úspěšný bez chyby kompilátoru nebo upozornění.  
  
#### <a name="to-create-a-test-project"></a>Chcete-li vytvořit projekt testů  
  
1.  Na **souboru** nabídky, přejděte k **přidat** a potom klikněte na tlačítko **nový projekt** otevřít **přidat nový projekt** dialogové okno.  
  
2.  Vyberte **Windows** uzlu, ybrat **Visual C#** uzel a klikněte na tlačítko **formulářová aplikace Windows**.  
  
3.  V **název** zadejte `Test`.  
  
4.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** vyberte uzel projektu testu **přidat odkaz** v místní nabídce zobrazíte  **Přidat odkaz na** dialogové okno.  
  
5.  Klikněte na kartu **projekty**. Vaše `ValueButtonLib` projektu budou uvedené v části **název projektu**. Dvakrát klikněte na projekt tak, aby do testovacího projektu přidejte odkaz.  
  
6.  V **Průzkumníku řešení** klikněte pravým tlačítkem na **testovací** a vyberte **sestavení**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Chcete-li přidat ovládací prvek do formuláře  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1.cs** a zvolte **Návrhář zobrazení** z místní nabídky.  
  
2.  V **nástrojů**, klikněte na tlačítko **ValueButtonLib komponenty**. Dvakrát klikněte na panel **ValueButton**.  
  
     A **ValueButton** se zobrazí ve formuláři.  
  
3.  Klikněte pravým tlačítkem myši **ValueButton** a vyberte **vlastnosti** z místní nabídky.  
  
4.  V **vlastnosti** okna, podívejte se na vlastnosti tohoto ovládacího prvku. Všimněte si, že jsou shodné s vlastností vystavovaných třídami standardní tlačítko s tím rozdílem, že je další vlastnost `ButtonValue`.  
  
5.  Nastavte `ButtonValue` vlastnost `5`.  
  
6.  V **všechny formuláře Windows** kartě **nástrojů**, dvakrát klikněte na panel **popisek** přidáte <xref:System.Windows.Forms.Label> ovládací prvek do formuláře.  
  
7.  Přemístěte popisek středu tvaru.  
  
8.  Dvakrát klikněte na panel `valueButton1`.  
  
     **Editor kódu** se otevře `valueButton1_Click` událostí.  
  
9. Vložte následující řádek kódu.  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **testovací**a zvolte **nastavit jako spouštěný projekt** z místní nabídky.  
  
11. Z **ladění** nabídce vyberte možnost **spustit ladění**.  
  
     `Form1` Zobrazí se.  
  
12. Klikněte na tlačítko `valueButton1`.  
  
     Číslice "5" se zobrazí v `label1`ukázku, který `ButtonValue` byla předána vlastnost zděděný ovládací prvek `label1` prostřednictvím `valueButton1_Click` metoda. Proto váš `ValueButton` dědí všechny funkce standardní tlačítko Windows Forms ovládací prvek, ale zpřístupňuje další, vlastní vlastnost.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
