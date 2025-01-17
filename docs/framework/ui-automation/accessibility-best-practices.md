---
title: Osvědčené postupy pro usnadnění
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: 92bad8b5ad556d79480a5b4da489d070545701da
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291399"
---
# <a name="accessibility-best-practices"></a>Osvědčené postupy pro usnadnění
> [!NOTE]
> Tato dokumentace je určená pro .NET Framework vývojářů, kteří chtějí používat spravované třídy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Implementace následujících osvědčených postupů v ovládacích prvcích nebo aplikacích vylepší přístupnost uživatelům, kteří používají zařízení s podporou technologie Assist. Mnohé z těchto osvědčených postupů se zaměřují na dobrý @no__tý návrh – 0. Každý osvědčený postup zahrnuje informace o implementaci pro ovládací prvky a aplikace [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. V mnoha případech je práce, která splňuje tyto osvědčené postupy, již obsažena v ovládacích prvcích [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a>Programový přístup  
 Programový přístup zahrnuje jistotu, že všechny prvky [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jsou označeny, jsou zpřístupněny hodnoty vlastností a jsou vyvolány vhodné události. U standardních ovládacích prvků [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] je většina této práce prováděna prostřednictvím <xref:System.Windows.Automation.Peers.AutomationPeer>. Vlastní ovládací prvky vyžadují další práci, aby bylo zajištěno, že je programový přístup správně implementován.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Povolit programový přístup ke všem prvkům uživatelského rozhraní a textu  
 Prvky uživatelského rozhraní (UI) by měly povolit programový přístup. Pokud je [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] standardním ovládacím prvkem [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], je v ovládacím prvku zahrnutá podpora pro programový přístup. Pokud je ovládací prvek vlastní ovládací prvek – ovládací prvek, který byl podtřídou ze společného ovládacího prvku nebo ovládacího prvku, který byl podtřídou z ovládacího prvku – potom je nutné ověřit implementaci <xref:System.Windows.Automation.Peers.AutomationPeer> pro oblasti, které mohou být potřeba upravit.  
  
 Pomocí tohoto osvědčeného postupu umožníte dodavatelům asistenční technologie identifikovat a manipulovat prvky [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vašeho produktu.  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Vložení názvů, názvů a popisů do objektů uživatelského rozhraní, rámců a stránek  
 Technologie pro usnadnění, zejména čtečky obrazovky, používají název k pochopení umístění rámce, objektu nebo stránky v navigačním schématu. Proto musí být název velmi popisný. Například název webové stránky "Webová stránka společnosti Microsoft" je nepoužitý v případě, že uživatel přešel do určité oblasti. Popisný název je zásadní pro uživatele, kteří jsou nevidomí a jsou závislé na obrazovkách obrazovky. Podobně platí, že u ovládacích prvků [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] jsou <xref:System.Windows.Automation.AutomationProperties.NameProperty> a <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> důležité pro zařízení s podporou technologie Assist.  
  
 Pomocí tohoto osvědčeného postupu lze technologiím pro usnadnění identifikovat a manipulovat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] v ukázkových ovládacích prvcích a aplikacích.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Zajistěte, aby se programové události aktivovaly všemi aktivitami uživatelského rozhraní.  
 Pomocí tohoto osvědčeného postupu mohou technologie pro usnadnění naslouchat změnám [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a upozornit uživatele na tyto změny.  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a>Uživatelská nastavení  
 Osvědčeným postupem v této části jsou zajištěny, že ovládací prvky nebo aplikace nepřepisují uživatelská nastavení.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Dodržování všech nastavení pro celý systém a nekoliduje s funkcemi přístupnosti  
 Uživatelé mohou použít ovládací panely k nastavení některých příznaků v rámci systému. Další příznaky lze nastavit programově. Tato nastavení by se neměla měnit pomocí ovládacích prvků nebo aplikací. Aplikace musí také podporovat nastavení přístupnosti jejich hostitelského operačního systému.  
  
 Pomocí tohoto osvědčeného postupu umožníte uživatelům nastavit nastavení usnadnění a zjistit, že tato nastavení nebudou aplikace měnit.  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a>Návrh vizuálního uživatelského rozhraní  
 Osvědčené postupy v této části zajišťují, aby ovládací prvky nebo aplikace efektivně používaly barvy a obrázky a mohly je používat technologie pro usnadnění.  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a>Nepoužívejte barvy pevného kódu.  
 Lidé, kteří mají barevně nevidomé, mají nízkou vizi nebo používají černou a bílou obrazovku, nemusí být schopni používat aplikace s pevně zakódovanými barvami.  
  
 Následující osvědčené postupy umožňují uživatelům upravovat kombinace barev na základě jednotlivých potřeb.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Podpora Vysoký kontrast a všech atributů systémových zobrazení  
 Aplikace by neměly rušit nebo zakázat nastavení kontrastu na úrovni systému, výběr barev nebo jiná nastavení a atributy zobrazení na úrovni systému. Nastavení pro systém, které přijala uživatel, vylepší přístupnost aplikací, takže by tyto aplikace neměly být vypnuté ani zakázané aplikacemi. K zajištění správného kontrastu by měla být použita barva v jejich správné kombinaci v popředí na pozadí. Nesouvisející barvy by neměly být smíšené a barvy by neměly být obrácené.  
  
 Mnoho uživatelů vyžaduje určité kombinace s vysokým kontrastem, jako je bílý text na černém pozadí. Vykreslení těchto obrácených, jako černý text na bílém pozadí způsobí, že se pozadí doplní přes popředí a může pro některé uživatele ztížit čtení.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Ujistěte se, že se všechna uživatelská rozhraní správně škálují podle nastavení DPI.  
 Zajistěte, aby všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] mohly správně škálovat podle nastavení bodů na palec (dpi). Také zajistěte, aby se prvky [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vešly na obrazovku 1024 x 768 a 120 bodů na palec (dpi).  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Navigace  
 Osvědčené postupy v této části zajišťují, že navigace byla řešena pro ovládací prvky a aplikace.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Zadání rozhraní klávesnice pro všechny prvky uživatelského rozhraní  
 Tabulátory zarážky, zejména při pečlivém naplánování, poskytují uživatelům jiný způsob, jak přejít na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplikace by měly poskytovat následující rozhraní klávesnice:  
  
- zarážky tabulátoru pro všechny ovládací prvky, se kterými může uživatel pracovat, jako jsou tlačítka, odkazy nebo seznamy  
  
- pořadí logických karet  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a>Zobrazení fokusu klávesnice  
 Uživatelé musí znát, který objekt má fokus klávesnice, aby mohl předpokládat účinek jejich klávesových úhozů. Chcete-li zvýraznit fokus klávesnice, použijte barvy, písma nebo grafiku, například obdélníky nebo zvětšení. Chcete-li audibly zvýraznit fokus klávesnice, změňte hlasitost, sklon nebo tónovou kvalitu.  
  
 Aby nedocházelo k nejasnostem, aplikace by měly skrýt všechny indikátory fokusu vizuálů a tmavé volby, které se nacházejí v neaktivních oknech (nebo podoknech)  
  
 Aplikace by měly s fokusem klávesnice provádět následující akce:  
  
- jedna položka by měla mít vždycky fokus klávesnice.  
  
- fokus klávesnice by měl být viditelný a zjevný  
  
- výběry nebo prioritní položky by měly být vizuálně zvýrazněny  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Podpora navigačních standardů a výkonných navigačních schémat  
 Různé aspekty navigace na klávesnici poskytují různým způsobům, jak uživatelům přejít [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplikace by měly poskytovat následující rozhraní klávesnice:  
  
- Klávesové zkratky a podtržené přístupové klávesy pro všechny příkazy, nabídky a ovládací prvky  
  
- Klávesové zkratky pro důležité odkazy  
  
- všechny položky nabídky mají přístupový klíč. všechna tlačítka mají přístupové klávesy, všechny příkazy mají klávesu akcelerátoru.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Neumožnit umístění myši v konfliktu s navigací klávesnice  
 Umístění myši by nemělo být v konfliktu s navigací klávesnice. Pokud je například myš umístěná někde došlo a uživatel přejde pomocí klávesnice, neměli byste kliknout na tlačítko myši, pokud ho uživatel iniciuje.  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a>Rozhraní Multimodal  
 Osvědčené postupy v této části zajišťují, aby aplikace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zahrnovala alternativy pro vizuální prvky.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Poskytněte uživatelem vybrané ekvivalenty pro prvky, které nejsou textové  
 Pro každý netextový prvek poskytněte uživatelsky vybraný ekvivalent pro text, přepisy nebo popisy zvuku, jako je například alternativní text, popisky nebo vizuální zpětná vazba.  
  
 Netextové prvky se týkají široké škály [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvků, včetně obrázků, oblastí rozvržení obrázků, animací, apletů, rámců, skriptů, grafických tlačítek, zvuků, samostatných zvukových souborů a videa. Netextové prvky jsou důležité, pokud obsahují vizuální informace, řeč nebo obecné zvukové informace, ke kterým uživatel potřebuje mít přístup, aby bylo možné pochopit obsah [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Použití barev, ale také k zadání alternativ barev  
 Pomocí barev můžete vylepšit, zdůraznit nebo znovu iterovat informace zobrazené jiným způsobem, ale nekomunikují informace pouze pomocí samotné barvy. Uživatelé, kteří mají barevně nevidomé nebo mají černobílé zobrazení, potřebují alternativy barev.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Použití standardních vstupních rozhraní API u volání nezávislých na zařízení  
 Volání nezávislá na zařízení zajišťují rovnost funkcí klávesnice a myši a zároveň poskytují technologii pro usnadnění s potřebnými informacemi o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
## <a name="see-also"></a>Další informace najdete v tématech

- <xref:System.Windows.Automation.Peers>
- [Ukázka vlastního ovládacího prvku NumericUpDown s motivem a podporou automatizace uživatelského rozhraní](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [Pokyny pro návrh uživatelského rozhraní klávesnice](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
