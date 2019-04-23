---
title: 'Postupy: Přístup ke službě z aplikace pracovního postupu'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 178fb04244cb3e5075722877fdd3e2b5a92b8502
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59309313"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Postupy: Přístup ke službě z aplikace pracovního postupu
Toto téma popisuje, jak volat služby pracovních postupů z konzolové aplikace pracovního postupu. To závisí na dokončení [jak: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tématu. I když toto téma popisuje, jak volat z aplikace pracovního postupu služby pracovního postupu, stejně jako je možné volat jakékoli služby Windows Communication Foundation (WCF) z aplikace pracovního postupu.

### <a name="create-a-workflow-console-application-project"></a>Vytvoření projektu konzolové aplikace pracovního postupu

1. Start Visual Studio 2012.

2. Načtení projektu MyWFService, kterou jste vytvořili v [jak: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tématu.

3. Klikněte pravým tlačítkem myši **MyWFService** řešení **Průzkumníka řešení** a vyberte **přidat**, **nový projekt**. Vyberte **pracovního postupu** v **nainstalované šablony** a **Konzolová aplikace pracovního postupu** ze seznamu typů projektů. Pojmenujte projekt MyWFClient a použijte výchozí umístění, jak je znázorněno na následujícím obrázku.

     ![Přidat dialogové okno nového projektu](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     Klikněte na tlačítko **OK** tlačítka Zavřít **přidat dialogové okno nového projektu**.

4. Po vytvoření projektu Workflow1.xaml soubor je otevřen v návrháři. Klikněte na tlačítko **nástrojů** kartě otevřít sadu nástrojů, pokud není již otevřete a klikněte na ikonu připínáčku nechat otevřené okno nástrojů.

5. Stisknutím klávesy **Ctrl**+**F5** k sestavení a spuštění služby. Stejně jako dříve spustili serveru ASP.NET Development Server a Internet Explorer zobrazí na stránce nápovědy WCF. Všimněte si, že identifikátor URI pro tuto stránku jako je nutné použít v dalším kroku.

     ![Zobrazování stránky nápovědy WCF a identifikátor URI aplikace Internet Explorer](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6. Klikněte pravým tlačítkem myši **MyWFClient** projekt **Průzkumníka řešení** a vyberte **přidat** > **odkaz na službu**. Klikněte na tlačítko **Discover** tlačítko Prohledat aktuální řešení pro všechny služby. Klikněte na tlačítko trojúhelníku vedle Service1.xamlx v seznamu služeb. Klikněte na tlačítko trojúhelníku vedle Service1 seznamu kontraktů implementovaných službou Service1. Rozbalte **Service1** uzlu **služby** seznamu. Echo operace se zobrazí v **operace** seznamu, jak je znázorněno na následujícím obrázku.

     ![Přidat Dialog odkaz na službu](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     Ponechte výchozí obor názvů a klikněte na **OK** zrušíte **přidat odkaz na službu** dialogového okna. Zobrazí se následující dialogové okno.

     ![Přidat odkaz na upozornění služby dialog](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     Klikněte na tlačítko **OK** zavřete dialogové okno. Dále stisknutím kombinace kláves CTRL + SHIFT + B, abyste mohli sestavit řešení. Názvem Všimněte si, že na panelu nástrojů byla přidána nová část **MyWFClient.ServiceReference1.Activities**. Rozbalením tohoto oddílu a Všimněte si, že odezvu aktivitu, která byla přidána, jak je znázorněno na následujícím obrázku.

     ![Echo aktivity v sadě nástrojů](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7. Přetáhnout myší <xref:System.Activities.Statements.Sequence> aktivity na plochu návrháře. Je v části **tok řízení** části panelu nástrojů.

8. S <xref:System.Activities.Statements.Sequence> aktivity v fokus, klikněte **proměnné** propojit a přidat proměnnou s řetězcem s názvem `inString`. Zadejte výchozí hodnotu proměnné `"Hello, world"` a proměnné řetězce s názvem `outString` jak je znázorněno v následujícím diagramu.

     ![Přidat proměnnou inString](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. Přetáhnout myší **Echo** aktivitu <xref:System.Activities.Statements.Sequence>. V okně Vlastnosti vytvořit vazbu `inMsg` argument `inString` proměnné a `outMsg` argument `outString` proměnné, jak je znázorněno na následujícím obrázku. Tím se předají hodnotu `inString` proměnné pro operace a přijímá návratovou hodnotu a umístí jej do `outString` proměnné.

     ![Připojení k proměnné argumenty](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. Přetáhnout myší **WriteLine** aktivity níže **Echo** aktivita k zobrazení řetězec vrácený voláním služby. **WriteLine** aktivita je umístěna v **primitiv** uzlu v sadě nástrojů. Vytvoření vazby **Text** argument **WriteLine** aktivitu `outString` proměnné tak, že zadáte `outString` do textového pole na **WriteLine** aktivity. Pracovní postup by teď měl vypadat jako na následujícím obrázku.

     ![Pracovní postup klientů](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. Klikněte pravým tlačítkem na řešení MyWFService a vyberte **nastavit projekty po spuštění...** . Vyberte **více projektů po spuštění** přepínací tlačítka a vyberte **Start** pro každý projekt v **akce** sloupce, jak je znázorněno na následujícím obrázku.

     ![Možnosti projektů při spuštění](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. Stiskněte kombinaci kláves Ctrl + F5 spusťte službu a klienta. Vývojový Server ASP.NET je hostitelem služby, aplikace Internet Explorer zobrazí na stránce nápovědy WCF a klientská aplikace pracovního postupu se spustí v okně konzoly a zobrazí řetězec vrácený ze služby ("Hello, world").

## <a name="see-also"></a>Viz také:

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Postupy: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Z pracovního postupu v projektu webové služby WCF](https://go.microsoft.com/fwlink/?LinkId=207725)
