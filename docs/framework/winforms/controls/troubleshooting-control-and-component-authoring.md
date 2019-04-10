---
title: Řešení potíží s vytvářením ovládacích prvků a komponent
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
ms.openlocfilehash: 3ae8a889bf69913d234e31804335ddb08560c30c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343412"
---
# <a name="troubleshooting-control-and-component-authoring"></a>Řešení potíží s vytvářením ovládacích prvků a komponent
Toto téma uvádí následující běžné problémy, které vznikají při vývoji komponent a ovládacích prvků. Další informace najdete v tématu [programování pomocí komponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).  
  
-   Nelze přidat ovládací prvek na panelu nástrojů  
  
-   Nelze ladit uživatelského ovládacího prvku formulářů Windows nebo komponenty  
  
-   Událost se vyvolá dvakrát v zděděný ovládací prvek nebo komponenty  
  
-   Chyba návrhu: "Nepovedlo se vytvořit komponentu '*název komponenty*."  
  
-   Atribut STAThreadAttribute  
  
-   Ikona komponenty se nezobrazují v panelu nástrojů  
  
## <a name="cannot-add-control-to-toolbox"></a>Nelze přidat ovládací prvek na panelu nástrojů  
 Pokud chcete přidat vlastní ovládací prvek, který jste vytvořili v jiném projektu nebo ovládací prvek třetích stran pro **nástrojů**, musíte to udělat ručně. Pokud projekt obsahuje ovládacího prvku nebo komponenty, měl by se zobrazit v **nástrojů** automaticky. Další informace najdete v tématu [názorný postup: Automatické vyplnění nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>Přidání ovládacího prvku na panelu nástrojů  
  
1. Klikněte pravým tlačítkem myši **nástrojů** a v místní nabídce vyberte **zvolit položky**.  
  
2. V **zvolit položky nástrojů** dialogovém okně přidejte komponentu:  
  
    -   Pokud chcete přidat do součásti rozhraní .NET Framework nebo ovládacího prvku, klikněte na tlačítko **součásti rozhraní .NET Framework** kartu.  
  
         – nebo –  
  
    -   Pokud chcete přidat komponenty modelu COM nebo ovládacího prvku ActiveX, klikněte na tlačítko **komponenty modelu COM** kartu.  
  
3. Pokud váš ovládací prvek je uvedený v dialogovém okně, potvrďte je vybraná a potom klikněte na **OK**.  
  
     Ovládací prvek je přidán do **nástrojů**.  
  
4. Pokud váš ovládací prvek není uveden v dialogovém okně, postupujte takto:  
  
    1.  Klikněte na tlačítko **Procházet** tlačítko.  
  
    2.  Přejděte do složky obsahující soubor .dll, který obsahuje ovládací prvek.  
  
    3.  Vyberte soubor .dll a klikněte na tlačítko **otevřít**.  
  
         V dialogovém okně se zobrazí váš ovládací prvek.  
  
    4.  Potvrďte, že je vybraný ovládací prvek a klikněte na **OK**.  
  
         Váš ovládací prvek je přidán do **nástrojů**.  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Nelze ladit uživatelského ovládacího prvku formulářů Windows nebo komponenty  
 Pokud váš ovládací prvek odvozen z <xref:System.Windows.Forms.UserControl> třídy, můžete ladit jeho chování za běhu pomocí testovacího kontejneru. Další informace najdete v tématu [jak: Testování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Další vlastní ovládací prvky a součásti nejsou samostatné projekty. Musí být hostovaný jako je například projekt aplikace Windows Forms a aplikací. Chcete-li ladit ovládací prvek nebo komponenty, třeba přidat ji do projektu Windows Forms.  
  
#### <a name="to-debug-a-control-or-component"></a>Chcete-li ladit ovládací prvek nebo komponenty  
  
1. Z **sestavení** nabídky, klikněte na tlačítko **sestavit řešení** sestavení potřebného řešení.  
  
2. Z **souboru** nabídce zvolte **přidat**a potom **nový projekt** přidáte projekt testu do vaší aplikace.  
  
3. V **přidat nový projekt** dialogové okno zvolit **aplikace Windows** pro typ projektu.  
  
4. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **odkazy** uzlu pro nový projekt. V místní nabídce klikněte na tlačítko **přidat odkaz** přidáte odkaz na projekt, který obsahuje ovládací prvek nebo komponenty.  
  
5. Vytvořte instanci ovládacího prvku nebo komponenty v testovém projektu. Pokud vaše komponenta je v **nástrojů**, ji můžete přetáhnout do návrhové ploše, nebo můžete vytvořit instanci prostřednictvím kódu programu, jak je znázorněno v následujícím příkladu kódu.  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     Teď můžete ladit ovládacího prvku nebo komponenty jako obvykle.  
  
 Další informace o ladění naleznete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) a [názorný postup: Ovládací prvky ladění vlastního Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>Událost se vyvolá dvakrát v zděděný ovládací prvek nebo komponenty  
 To je pravděpodobně v důsledku duplikovaného `Handles` klauzuli. Další informace najdete v tématu [řešení potíží s zděděné obslužných rutin událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>Chyba návrhu: "Nepovedlo se vytvořit komponentu 'název součásti."  
 Součást nebo ovládací prvek, musíte zadat výchozí konstruktor bez parametrů. Při návrhu prostředí vytvoří instanci součást nebo ovládací prvek, nebude pokoušet o poskytovat žádné parametry pro přetížení konstruktoru, které přijímají parametry.  
  
## <a name="stathreadattribute"></a>Atribut STAThreadAttribute  
 <xref:System.STAThreadAttribute> Informuje common language runtime (CLR), Windows Forms používá jednovláknový apartment modelu. Pokud použijete tento atribut není pro aplikace Windows Forms může dojít k neúmyslnému chování `Main` metody. Například nemusí zobrazit obrázky na pozadí pro ovládací prvky jako <xref:System.Windows.Forms.ListView>. Některé ovládací prvky budete možná muset tento atribut pro správné funkce automatického dokončování a chování a přetažení.  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>Ikona komponenty se nezobrazují v panelu nástrojů  
 Při použití <xref:System.Drawing.ToolboxBitmapAttribute> na vlastní komponentu přidružit ikonu, nezobrazí rastrového obrázku panelu nástrojů pro automaticky generované součásti. Rastrový obrázek zobrazíte načtěte pomocí ovládacího prvku **zvolit položky nástrojů** dialogové okno. Další informace najdete v tématu [jak: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](how-to-provide-a-toolbox-bitmap-for-a-control.md).  
  
## <a name="see-also"></a>Viz také:

- [Vývoj ovládacích prvků Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)
- [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Postupy: Otestování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- [Tvorba komponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))
- [Řešení potíží s vývojem během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
