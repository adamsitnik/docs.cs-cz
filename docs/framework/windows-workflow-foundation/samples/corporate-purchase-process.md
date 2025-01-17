---
title: Proces nákupu v podniku
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: d019c1915e691fcba00fa8f1b0884a898ce02fab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951524"
---
# <a name="corporate-purchase-process"></a>Proces nákupu v podniku
V této ukázce se dozvíte, jak vytvořit velmi základní nákupní proces založený na požadavcích na návrhy (RFP) s automatickým výběrem nejlepšího návrhu. Kombinuje <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601> aavlastníaktivitukvytvořenípracovníhopostupu,<xref:System.Activities.Statements.ForEach%601> který představuje proces.

 Tato ukázka obsahuje klientskou aplikaci ASP.NET, která umožňuje interakci s procesem v podobě různých účastníků (jako původní žadatel nebo konkrétní dodavatel).

## <a name="requirements"></a>Požadavky

- Visual Studio 2012.

- [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].

## <a name="demonstrates"></a>Demonstruje

- Vlastní aktivity.

- Složení aktivit.

- Záložky.

- Dočasné.

- Schematized Persistence.

- Probíhá.

- Rozteč.

- Hostování [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v různých klientech (ASP.NET webové aplikace a aplikace WinForms).

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>Popis procesu  
 Tato ukázka předvádí implementaci programovací model Windows Workflow Foundationho (WF) programu pro shromáždění návrhů od dodavatelů pro obecnou firmu.  
  
1. Zaměstnanec společnosti X vytvoří žádost o návrh (RFP).  
  
    1. Typy zaměstnanců v názvu a popisu RFP  
  
    2. Zaměstnanec vybírá dodavatele, kteří chce pozvat k odeslání návrhů.  
  
2. Zaměstnanec návrh odešle.  
  
    1. Vytvoří se instance pracovního postupu.  
  
    2. Pracovní postup čeká, až všichni dodavatelé odešlou své návrhy.  
  
3. Po přijetí všech návrhů pracovní postup projde všechny přijaté návrhy a vybere ten nejlepší.  
  
    1. Každý dodavatel má reputaci (Tato ukázka uchovává seznam reputace v VendorRepository.cs).  
  
    2. Celková hodnota návrhu je určena hodnotou (hodnota zadaná dodavatelem) * (zaznamenaná pověst dodavatele)/100.  
  
4. Původní žadatel uvidí všechny odeslané návrhy. Nejlepší návrh se zobrazí ve speciální části sestavy.  
  
## <a name="process-definition"></a>Definice procesu  
 Základní logika ukázky používá <xref:System.Activities.Statements.ParallelForEach%601> aktivitu, která čeká na nabídky od každého dodavatele (pomocí vlastní aktivity, která vytvoří záložku) a zaregistruje návrh dodavatele jako RFP ( <xref:System.Activities.Statements.InvokeMethod> s použitím aktivity).  
  
 Ukázka pak projde všechny přijaté návrhy uložené v `RfpRepository`, vypočítá upravenou hodnotu ( <xref:System.Activities.Statements.Assign> pomocí aktivity a <xref:System.Activities.Expressions> aktivit) a pokud je upravená hodnota lepší než předchozí nejlepší nabídka, přiřadí novou hodnotu jako nejlepší nabídku (pomocí <xref:System.Activities.Statements.If> aktivit a <xref:System.Activities.Statements.Assign> ).  
  
## <a name="projects-in-this-sample"></a>Projekty v této ukázce  
 Tato ukázka obsahuje následující projekty.  
  
|Project|Popis|  
|-------------|-----------------|  
|Společné|Objekty entit použité v rámci procesu (žádost o návrh, dodavatel a návrh dodavatele).|  
|WfDefinition|Definice procesu (jako [!INCLUDE[wf1](../../../../includes/wf1-md.md)] program) a hostitel (`PurchaseProcessHost`) používané klientskými aplikacemi pro vytváření a používání instancí pracovního postupu procesu nákupu.|  
|Webový klient|Klientská aplikace ASP.NET, která umožňuje uživatelům vytvářet a přispívat do instancí procesu nákupu. Používá vlastního hostitele k interakci s modulem pracovního postupu.|  
|WinFormsClient|Klientská aplikace model Windows Forms, která umožňuje uživatelům vytvářet a přispívat do instancí procesu nákupu. Používá vlastního hostitele k interakci s modulem pracovního postupu.|  
  
### <a name="wfdefinition"></a>WfDefinition  
 Následující tabulka obsahuje popis nejdůležitějších souborů v projektu WfDefinition.  
  
|Soubor|Popis|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|Rozhraní pro hostitele pracovního postupu.|  
|PurchaseProcessHost.cs|Implementace hostitele pro pracovní postup. Hostitel vyabstrakce Podrobnosti modulu runtime pracovního postupu a používá se ve všech klientských aplikacích pro načítání, spouštění a interakci s `PurchaseProcess` instancemi pracovního postupu.|  
|PurchaseProcessWorkflow.cs|Aktivita, která obsahuje definici pracovního postupu procesu nákupu (je odvozena od <xref:System.Activities.Activity>).<br /><br /> Aktivity, které jsou <xref:System.Activities.Activity> odvozeny od funkce vytváření sestavením existujících vlastních aktivit a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] aktivit z knihovny aktivit. Sestavování těchto aktivit je nejzákladnější způsob, jak vytvořit vlastní funkce.|  
|WaitForVendorProposal.cs|Tato vlastní aktivita je odvozena <xref:System.Activities.NativeActivity> z a vytvoří pojmenovanou záložku, kterou musí dodavatel obnovit později při odeslání návrhu.<br /><br /> Aktivity, které jsou <xref:System.Activities.NativeActivity>odvozeny z, podobně jako <xref:System.Activities.CodeActivity>ty, které jsou odvozeny <xref:System.Activities.NativeActivity.Execute%2A>z, vytvoří imperativní funkce přepsáním, ale také mají přístup ke všem funkcím <xref:System.Activities.ActivityContext> modulu runtime pracovního postupu prostřednictvím rozhraní, které získá. předáno do `Execute` metody. Tento kontext má podporu pro plánování a zrušení podřízených aktivit, nastavení zón bez trvalého uložení (bloky spuštění, během kterých modul runtime neuchovává data pracovního postupu, například v rámci atomických transakcí), a <xref:System.Activities.Bookmark> objekty (popisovače pro obnovení pozastavených pracovních postupů.|  
|TrackingParticipant.cs|<xref:System.Activities.Tracking.TrackingParticipant> Který přijímá všechny události sledování a ukládá je do textového souboru.<br /><br /> Sledování účastníků je přidáno do instance pracovního postupu jako rozšíření.|  
|XmlWorkflowInstanceStore.cs|Vlastní <xref:System.Runtime.DurableInstancing.InstanceStore> , který ukládá aplikace pracovního postupu do souborů XML.|  
|XmlPersistenceParticipant.cs|Vlastní <xref:System.Activities.Persistence.PersistenceParticipant> , který uloží instanci žádosti o návrh do souboru XML.|  
|AsyncResult.cs/CompletedAsyncResult.cs|Pomocné třídy pro implementaci asynchronního vzoru v součástech trvalosti.|  
  
### <a name="common"></a>Společné  
 Následující tabulka obsahuje popis nejdůležitějších tříd v rámci společného projektu.  
  
|Třída|Popis|  
|-----------|-----------------|  
|Dodavatele|Dodavatel, který odešle návrhy v žádosti o návrhy.|  
|RequestForProposal|Žádost o návrhy (RFP) je pozvánka pro dodavatele, kteří odešlou návrhy na konkrétní komoditu nebo službu.|  
|VendorProposal|Návrh, který dodavatel odeslal na konkrétní RFP.|  
|VendorRepository|Úložiště dodavatelů. Tato implementace obsahuje kolekci instancí dodavatele a metod pro vystavení těchto instancí v paměti.|  
|RfpRepository|Úložiště požadavků pro návrhy. Tato implementace obsahuje použití LINQ to XML k dotazování souboru XML požadavků pro návrh vygenerovaný schematized persistencí. |  
|IOHelper|Tato třída zpracovává všechny problémy související s vstupně-výstupními operacemi (složky, cesty a tak dále).|  
  
### <a name="web-client"></a>Webový klient  
 Následující tabulka obsahuje popis nejdůležitějších webových stránek v projektu webového klienta.  
  
|Soubor|Popis|  
|-|-|  
|CreateRfp.aspx|Vytvoří a odešle nový požadavek na návrhy.|  
|Default.aspx|Zobrazuje všechny aktivní a dokončené žádosti o návrhy.|  
|GetVendorProposal.aspx|Získá návrh od dodavatele v konkrétní žádosti o návrhy. Tato stránka je používána pouze dodavateli.|  
|ShowRfp.aspx|Zobrazit všechny informace o žádosti o návrhy (obdržené návrhy, data, hodnoty a další informace). Tuto stránku používá pouze tvůrce žádosti o návrh.|  
  
### <a name="winforms-client"></a>Klient WinForms  
 Následující tabulka obsahuje popis nejdůležitějších forem v projektu Windows Forms.  
  
|Formulář|Popis|  
|-|-|  
|NewRfp|Vytvoří a odešle nový požadavek na návrhy.|  
|ShowProposals|Zobrazit všechny aktivní a dokončené žádosti o návrhy. **Poznámka:**  Po vytvoření nebo úpravě žádosti o návrh možná budete muset kliknout na tlačítko **aktualizovat** v uživatelském rozhraní a zobrazit změny provedené na této obrazovce.|  
|SubmitProposal|Získejte návrh od dodavatele v konkrétní žádosti o návrhy. Toto okno používají pouze dodavatelé.|  
|ViewRfp|Zobrazit všechny informace o žádosti o návrhy (obdržené návrhy, data, hodnoty a další informace). Toto okno je používáno pouze tvůrcem žádosti o návrhy.|  
  
### <a name="persistence-files"></a>Soubory trvalosti  
 V následující tabulce jsou uvedeny soubory generované zprostředkovatelem trvalosti (`XmlPersistenceProvider`), které jsou umístěny v cestě k dočasné složce aktuálního systému (pomocí <xref:System.IO.Path.GetTempPath%2A>). Trasovací soubor se vytvoří v aktuální cestě spuštění.  
  
|Název souboru|Popis|Cesta|  
|-|-|-|  
|RFPs. XML|Soubor XML se všemi aktivními a dokončenými požadavky pro návrhy.|<xref:System.IO.Path.GetTempPath%2A>|  
|InstanceId|Tento soubor obsahuje všechny informace o instanci pracovního postupu.<br /><br /> Tento soubor je vygenerován implementací trvalosti schematized (PersistenceParticipant v XmlPersistenceProvider).|<xref:System.IO.Path.GetTempPath%2A>|  
|[instanceId].tracking|Textový soubor se všemi událostmi, ke kterým došlo v konkrétní instanci.<br /><br /> Tento soubor je vygenerovaný nástrojem TrackingParticipant.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess. Tracing. nástroji tracelog. txt|Trasovací soubor vygenerovaný pracovním postupem na základě parametrů konfigurace v souborech App. config nebo Web. config.|Aktuální cesta spuštění|  
  
#### <a name="to-use-this-sample"></a>Použití této ukázky  
  
1. Pomocí sady Visual Studio 2010 otevřete soubor řešení PurchaseProcess. sln.  
  
2. Chcete-li spustit projekt webového klienta, otevřete **Průzkumník řešení** a klikněte pravým tlačítkem na projekt **webového klienta** . Vyberte **nastavit jako spouštěný projekt**.  
  
3. Chcete-li spustit projekt klienta WinForms, otevřete **Průzkumník řešení** a klikněte pravým tlačítkem myši na projekt **klienta WinForms** . Vyberte **nastavit jako spouštěný projekt**.  
  
4. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
5. Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.  
  
### <a name="web-client-options"></a>Možnosti webového klienta  
  
- **Vytvořit nový RFP**: Vytvoří nový požadavek na návrhy (RFP) a spustí pracovní postup pro nákupní proces.  
  
- **Aktualizovat**: Aktualizuje seznam aktivních a dokončených RFPs v hlavním okně.  
  
- **Zobrazit**: Zobrazuje obsah existující RFP. Dodavatelé mohou odeslat své návrhy (Pokud je pozvánka nebo RFPa není dokončená).  
  
- Zobrazit jako: Uživatel může k RFP přistupovat pomocí různých identit, a to tak, že v aktivní RFPs mřížce vybere požadovaného účastníka v poli **Zobrazit jako** pole se seznamem.  
  
### <a name="winforms-client-options"></a>Možnosti klienta WinForms  
  
- **Vytvořit RFP**: Vytvoří nový požadavek na návrhy (RFP) a spustí pracovní postup pro nákupní proces.  
  
- **Aktualizovat**: Aktualizuje seznam aktivních a dokončených RFPs v hlavním okně.  
  
- **Zobrazit RFP**: Zobrazuje obsah existující RFP. Dodavatelé mohou odeslat své návrhy (Pokud je pozvaní nebo RFP není dokončená)  
  
- **Připojit jako**: Uživatel může k RFP přistupovat pomocí různých identit, a to tak, že v aktivní RFPs mřížce vybere požadovaného účastníka v poli **Zobrazit jako** pole se seznamem.
