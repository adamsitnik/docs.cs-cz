---
title: Přehled automatizace uživatelského rozhraní TextPattern
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
ms.openlocfilehash: 15638e7da99ef15be58052849bf0675cc21941c9
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180166"
---
# <a name="ui-automation-textpattern-overview"></a>Přehled automatizace uživatelského rozhraní TextPattern

> [!NOTE]
> Tato dokumentace je určená pro .NET Framework vývojářů, kteří chtějí používat spravované třídy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).

Tento přehled popisuje, jak použít [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k vystavení textového obsahu, včetně formátů a atributů stylu, textových ovládacích prvků v @no__t -1CH podporovaných platformách. Tyto ovládací prvky zahrnují, ale nejsou omezené na, .NET Framework Microsoft <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> a také jejich ekvivalenty [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)].

Vystavení textového obsahu ovládacího prvku je provedeno pomocí vzoru ovládacího prvku <xref:System.Windows.Automation.TextPattern>, který představuje obsah kontejneru textu jako textový Stream. Naopak <xref:System.Windows.Automation.TextPattern> vyžaduje podporu třídy <xref:System.Windows.Automation.Text.TextPatternRange> k zobrazení atributů formátu a stylu. <xref:System.Windows.Automation.Text.TextPatternRange> podporuje <xref:System.Windows.Automation.TextPattern> tím, že představuje souvislý nebo vícenásobný nesouvislý text v kontejneru textu s kolekcí koncových bodů <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> a <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>. @no__t – 0 podporuje funkce, jako je výběr, porovnání, načítání a procházení.

> [!NOTE]
> Třídy <xref:System.Windows.Automation.TextPattern> neposkytují způsob, jak vkládat nebo upravovat text. V závislosti na ovládacím prvku však lze to provést [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> nebo přímým vstupem klávesnice. Příklad naleznete v [ukázce TextPattern INSERT text](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText) .

Funkce popsané v tomto přehledu jsou důležité pro dodavatele s asistenčními technologiemi a jejich koncové uživatele. Technologie pro usnadnění můžou pomocí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] shromažďovat úplné informace o formátování textu pro uživatele a poskytovat programovou navigaci a výběr textu pomocí <xref:System.Windows.Automation.Text.TextUnit> (znak, Word, řádek nebo odstavec).

<a name="UI_Automation_TextPattern_vs__Cicero"></a>

## <a name="ui-automation-textpattern-vs-text-services-framework"></a>ROZHRANÍ .NET Automation TextPattern vs. Text Services Framework

Rozhraní TSF (text Services Framework) je jednoduché a škálovatelné systémové rozhraní, které umožňuje využívat služby přirozeného jazyka a pokročilý Textový vstup na ploše a v aplikacích. Kromě poskytování rozhraní pro aplikace k zveřejnění jejich textového úložiště podporuje také metadata pro toto úložiště textu.

TSF však byl navržen pro aplikace, které vyžadují vložení vstupu do kontextových scénářů, zatímco <xref:System.Windows.Automation.TextPattern> je řešení jen pro čtení (s omezením uvedeným výše), které je určeno k zajištění optimalizovaného přístupu k úložišti textu pro čtečky obrazovky a Braillovo písmo. signalizac.

V krátkých a přístupných technologiích, které vyžadují přístup jen pro čtení k úložišti textu, může použít <xref:System.Windows.Automation.TextPattern>, ale bude potřebovat složitější funkce TSF pro kontext, který je v kontextu.

<a name="Control_Types"></a>

## <a name="control-types"></a>Typy ovládacích prvků

### <a name="text"></a>Text

Textový ovládací prvek je základní prvek reprezentující text na obrazovce.

Samostatný ovládací prvek textu lze použít jako popisek nebo statický text na formuláři. Textové ovládací prvky mohou být také obsaženy v rámci struktury <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> nebo <xref:System.Windows.Automation.ControlType.DataItem>.

> [!NOTE]
> Textové ovládací prvky se nemusí zobrazit v zobrazení obsahu stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (viz [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)). Je to proto, že textové ovládací prvky se často zobrazují prostřednictvím vlastnosti název jiného ovládacího prvku. Například text, který se používá k označení ovládacího prvku pro úpravy, je přístupný prostřednictvím vlastnosti Name ovládacího prvku pro úpravy. Vzhledem k tomu, že je ovládací prvek pro úpravy v zobrazení obsahu stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], není nutné, aby byl prvek textu v tomto zobrazení stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Jediný text, který se zobrazí v zobrazení obsahu, je text, který není redundantní informace. To umožňuje všem asistenčním technologiím rychle filtrovat pouze ty informace, které jejich uživatelé potřebují.

### <a name="edit"></a>Upravit

Ovládací prvky pro úpravy umožňují uživateli zobrazit a upravit jeden řádek textu.

> [!NOTE]
> Jeden řádek textu může v některých scénářích rozložení obtékat.

### <a name="document"></a>Databáze dokumentů

Ovládací prvky dokumentu umožňují uživateli přejít na více stránek textu a získat z nich informace.

<a name="TextPattern_Client_API_s"></a>

## <a name="textpattern-client-apis"></a>Klientská rozhraní API pro TextPattern

|||
|-|-|
|`System.Windows.Automation.TextPattern Class`|Vstupní bod pro model textu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].<br /><br /> Tato třída také obsahuje dva naslouchací procesy událostí <xref:System.Windows.Automation.TextPattern>, <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> a <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|
|`System.Windows.Automation.Text.TextPatternRange Class`|Reprezentace rozsahu textu v rámci kontejneru textu, který podporuje <xref:System.Windows.Automation.TextPattern>.<br /><br /> Klienti automatizace uživatelského rozhraní by měli mít pozor na aktuální platnosti rozsahu textu vytvořeného pomocí <xref:System.Windows.Automation.Text.TextPatternRange>. Pokud je původní text v ovládacím prvku text úplně nahrazen novým textem, aktuální rozsah textu se změní na neplatný. Rozsah textu ale může mít i určitou životaschopnost, pokud se změní jenom část původního textu a podkladový ovládací prvek textu spravuje svůj text "ukazatel" s kotvami (nebo koncovými body) místo s absolutním umístěním znaků.<br /><br /> Klienti mohou naslouchat <xref:System.Windows.Automation.TextPattern.TextChangedEvent> pro oznámení o změnách v textovém obsahu, se kterými pracují.|
|`System.Windows.Automation.AutomationTextAttribute Class`|Slouží k identifikaci formátovacích atributů oblasti textu.|

<a name="TextPattern_Provider_API_s"></a>

## <a name="textpattern-provider-apis"></a>Rozhraní API pro poskytovatele TextPattern

Prvky uživatelského rozhraní nebo ovládací prvky, které podporují <xref:System.Windows.Automation.TextPattern> implementací rozhraní <xref:System.Windows.Automation.Provider.ITextProvider> a <xref:System.Windows.Automation.Provider.ITextRangeProvider>, a to buď nativně, nebo prostřednictvím proxy serverů [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], jsou schopné vystavit podrobné informace o atributu pro libovolný text, který obsahuje kromě poskytování robustního. navigační možnosti.

Zprostředkovatel <xref:System.Windows.Automation.TextPattern> nemusí podporovat všechny atributy textu, pokud ovládací prvek nemá podporu pro všechny konkrétní atributy.

Poskytovatel <xref:System.Windows.Automation.TextPattern> musí podporovat funkce <xref:System.Windows.Automation.TextPattern.GetSelection%2A> a <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A>, pokud ovládací prvek podporuje výběr textu nebo umístění textového kurzoru (nebo systémového kurzoru) v oblasti textu. Pokud ovládací prvek tuto funkci nepodporuje, nemusí podporovat žádnou z těchto metod. Ovládací prvek však musí vystavit typ výběru textu, který podporuje implementací vlastnosti <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A>.

Poskytovatel <xref:System.Windows.Automation.TextPattern> musí vždycky podporovat konstanty <xref:System.Windows.Automation.Text.TextUnit> <xref:System.Windows.Automation.Text.TextUnit.Character> a <xref:System.Windows.Automation.Text.TextUnit.Document>, jakož i všechny další konstanty <xref:System.Windows.Automation.Text.TextUnit>, které podporuje.

> [!NOTE]
> Poskytovatel může přeskočit podporu konkrétního <xref:System.Windows.Automation.Text.TextUnit> odložením k nejbližšímu největšímu <xref:System.Windows.Automation.Text.TextUnit> podporovanému v následujícím pořadí: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page> a <xref:System.Windows.Automation.Text.TextUnit.Document>.

|||
|-|-|
|`ITextProvider Interface`|Zpřístupňuje metody, vlastnosti a atributy, které podporují <xref:System.Windows.Automation.TextPattern> v klientských aplikacích (viz <xref:System.Windows.Automation.Provider.ITextProvider>).|
|`ITextRangeProvider Interface`|Představuje rozsah textu v poskytovateli textu (viz <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|
|`System.Windows.Automation.TextPatternIdentifiers Class`|Obsahuje hodnoty, které se používají jako identifikátory pro poskytovatele textu (viz <xref:System.Windows.Automation.TextPatternIdentifiers>).|

<a name="Security"></a>

## <a name="security"></a>Zabezpečení

Architektura [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] byla navržena s ohledem na zabezpečení (viz [Přehled zabezpečení automatizace uživatelského rozhraní](ui-automation-security-overview.md)). Třídy TextPattern popsané v tomto přehledu ale vyžadují určité konkrétní požadavky na zabezpečení.

- poskytovatelé textu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] poskytují rozhraní jen pro čtení a neposkytují možnost měnit stávající text v ovládacím prvku.

- Klienti automatizace uživatelského rozhraní můžou použít jenom [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], pokud jsou plně důvěryhodní. Příkladem může být plocha chráněného přihlašování, kde se můžou spouštět jenom známé a důvěryhodné aplikace.

- Vývojáři zprostředkovatelů automatizace uživatelského rozhraní by si měli být vědomi, že všechny informace, které zvolí k vystavení v ovládacích prvcích prostřednictvím [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], jsou v podstatě veřejné a plně přístupné pro jiný kód. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] neposkytuje žádné úsilí k určení věrohodnosti žádného klienta automatizace uživatelského rozhraní a proto by zprostředkovatel automatizace uživatelského rozhraní neměl zveřejnit chráněný obsah nebo citlivé textové informace (například pole hesla).

- Jedna z nejvýznamnějších změn v zabezpečení pro [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] je široce označována jako "zabezpečený vstup", která zahrnuje technologie, jako jsou například minimální privilegované (nebo omezené) uživatelské účty (LUA) a izolace úrovně oprávnění uživatelského rozhraní (UIPI).

  - UIPI zabrání jednomu programu v řízení a/nebo sledovat další "privilegovaný" program, který znemožňuje útokům prostřednictvím zpráv v okně mezi procesy, které jsou falešné na vstupu uživatele.

  - LUA nastaví omezení pro oprávnění aplikací, které používají uživatelé ve skupině Administrators. Aplikace nemusí nutně mít oprávnění správce, ale místo toho se spustí s nejmenšími potřebnými oprávněními. V důsledku toho můžou být v LUA scénářích vynutila určitá omezení. Nejpřesnější zkracování řetězců (včetně řetězců TextPattern), kde může být nutné omezit velikost řetězců načítaných z aplikací na úrovni správce, aby nemusely přidělovat paměť k bodu zakázání aplikace.

<a name="Performance"></a>

## <a name="performance"></a>Výkon

Vzhledem k tomu, že TextPattern spoléhá na většinu funkcí volání mezi procesy, neposkytuje mechanismus ukládání do mezipaměti za účelem zvýšení výkonu při zpracování obsahu. To je na rozdíl od jiných vzorů ovládacích prvků v [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], ke kterým lze přistupovat pomocí metod <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>.

Jedním z cílem pro zlepšení výkonu je zajištění, že se klienti automatizace uživatelského rozhraní snaží načíst středně velké bloky textu pomocí <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Například volání GetText (1) bude mít za následek přístupy mezi procesy pro každý znak, zatímco jedno volání GetText (-1) bude mít za následek jeden z přístupů mezi procesy, ale může mít vysokou latenci v závislosti na velikosti poskytovatele textu.

<a name="Glossary"></a>

## <a name="textpattern-terminology"></a>Terminologie TextPattern

**Atribut**\
Formátování charakteristické oblasti textu (například <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> nebo <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).

**Degenerovat @no__t rozsahu**-1
Negenerovaný rozsah je prázdný text nebo textový rozsah s nulovým znakem. Pro účely vzoru ovládacího prvku TextPattern je textový kurzor (nebo systémový blikající kurzor) považován za negenerovaný rozsah. Pokud není vybraný žádný text, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> vrátí do textového kurzoru text degenerovaný rozsah a <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> by vrátilo jako počáteční koncový bod degenerovaný rozsah. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> a <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> mohou vracet degenerované rozsahy, když poskytovatel textu nemůže najít žádné oblasti textu, které odpovídají dané podmínce. Tento degenerovaný rozsah lze použít jako počáteční koncový bod v rámci poskytovatele textu. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A> a <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> vrátí nulový odkaz (`Nothing` v Microsoft Visual Basic .NET), aby nedocházelo k záměně se zjištěným rozsahem oproti negenerovanému rozsahu.

**Vložený objekt**\
V textovém modelu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] existují dva typy vložených objektů. Jsou tvořeny textovými prvky obsahu, jako jsou hypertextové odkazy nebo tabulky, a ovládací prvky, jako jsou obrázky a tlačítka. Podrobnější informace najdete v tématu [přístup k vloženým objektům pomocí automatizace uživatelského rozhraní](access-embedded-objects-using-ui-automation.md).

**Koncový bod**\
Absolutní <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> nebo <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> bod textového rozsahu v rámci textového kontejneru.

![TextPatternRangeEndpoints &#40;začátek a konec&#41;.](./media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints") Následující příklad ilustruje sadu počátečních a koncových bodů.

**TextRange**\
Reprezentace rozsahu textu s počátečním a koncovým bodem v kontejneru textu včetně všech přidružených atributů a funkcí.

<xref:System.Windows.Automation.Text.TextUnit>\
Předem definovaná jednotka textu (znak, Word, řádek nebo odstavec), která se používá k procházení logických segmentů textového rozsahu.

## <a name="see-also"></a>Další informace najdete v tématech

- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md)
- [Rozhraní Text Services Framework](/windows/desktop/api/_tsf/)
