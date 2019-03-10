---
title: Pokyny k migraci
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 405ed0dcbd730f08b84ad0b40008c4d77b02e26f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719673"
---
# <a name="migration-guidance"></a>Pokyny k migraci
V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], společnost Microsoft vydává druhý hlavní verze Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)] byla vydána v [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (to zahrnuté typy v oborech názvů System.Workflow.* barvy; dnes označovány jako WF3) a vylepšení v [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. WF3 je také součástí [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ale existuje souběžně s novou technologií pracovního postupu (typy v System.Activities.\* oborů názvů; označuje jako WF4). Při zvažování, kdy se má přijmout WF4, je potřeba nejprve uznávají řídit načasování.  
  
-   WF3 je plně podporován součástí [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
-   WF3 aplikace spouštět [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] beze změny a i nadále mít přitom plnou podporu.  
  
-   Je možné vytvořit nové WF3 aplikace a existující aplikace lze upravovat v sadě Visual Studio 2012 a jsou plně podporovány.  
  
 Proto rozhodnutí přijmout rozhraní .NET Framework 4 je oddělený od rozhodnout a přesunout do WF4 (System.Activities.*) z WF3 (System.Workflow.\*). Toto téma obsahuje odkazy na pokyny k migraci pracovního postupu, který poskytuje informace o práci s WF3 a WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>WF migrace dokumenty White Paper a návody  
 [Přehled migrace WF](https://go.microsoft.com/fwlink/?LinkId=153873) téma poskytuje komplexní přehled o vztah mezi strategie WF3 a WF4 a migrace. Témata Průvodce vyhledáváním přejít k podrobnostem konkrétní témata.  
  
 [Přehled migrace WF](https://go.microsoft.com/fwlink/?LinkId=153873)  
 Popisuje vztah mezi WF3 a WF4 a volby, které už máte uživatelem nebo potenciální pracovního postupu technologie v rozhraní .NET 4.  
  
 [Migrace pracovního postupu: Osvědčené postupy pro vývoj WF3](https://go.microsoft.com/fwlink/?LinkId=153852)  
 Tento článek popisuje postup návrhu WF3 artefakty, takže je možné snadno migrovat do WF4.  
  
 [WF pokyny: pravidla](https://go.microsoft.com/fwlink/?LinkId=153854)  
 Popisuje, jak přenést související pravidla investice vpřed do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] řešení.  
  
 [WF pokyny: Stavového stroje](https://go.microsoft.com/fwlink/?LinkId=153855)  
 Tento článek popisuje tok řízení WF4 modelování chybí aktivit stavového stroje.  
  
 Všimněte si, že tyto pokyny platí jenom pro projekty pracovního postupu, které jsou cíleny na rozhraní .NET Framework 4. Pracovní postupy stavového stroje byly přidány ve verzi Update 1 platformy .NET 4.0.1 a byly součástí rozhraní .NET Framework 4.5. Další informace o pracovní postupy stavu počítače v prostředí .NET 4.0.1 - 4.0.3 a rozhraní .NET Framework 4.5, naleznete v tématu [aktualizace 4.0.1 pro funkce rozhraní Microsoft .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) a [pracovní postupy stavu počítače](state-machine-workflows.md).  
  
 [Kuchařka pro migraci pracovního postupu: Vlastní aktivity](https://go.microsoft.com/fwlink/?LinkId=153856)  
 Poskytuje příklady a pokyny pro změnu návrhu WF3 na WF4 vlastní aktivity.  
  
 [Kuchařka pro migraci pracovního postupu: Pokročilé vlastní aktivity](https://go.microsoft.com/fwlink/?LinkId=275560)  
 Obsahuje pokyny pro změnu návrhu pokročilé WF3 vlastní, které používají fronty WF3 a plán podřízené aktivity jako WF4 vlastní aktivity.  
  
 [Kuchařka pro migraci pracovního postupu: Pracovní postupy](https://go.microsoft.com/fwlink/?LinkId=153858)  
 Poskytuje příklady a pokyny pro změnu návrhu pracovních postupů WF3 na WF4.  
  
 [Kuchařka pro migraci pracovního postupu: Workflow Hosting](https://go.microsoft.com/fwlink/?LinkId=275561)  
 Obsahuje pokyny pro změnu návrhu WF3 hostitelský kód jako kód WF4 hostování. Cílem je pokrývají klíčové rozdíly mezi WF3 a WF4 hostování pracovního postupu.  
  
 [Kuchařka pro migraci pracovního postupu: Sledování pracovního postupu](https://go.microsoft.com/fwlink/?LinkId=275562)  
 Obsahuje pokyny pro změnu návrhu WF3 sledování kódu a konfigurace pomocí ekvivalentní WF4 sledování kódu a konfigurace.  
  
 [WF pokyny: Služby pracovních postupů](https://go.microsoft.com/fwlink/?LinkId=275564)  
 Obsahuje příklad objektově orientovaný podrobné pokyny pro změnu návrhu pracovních postupů, které implementují Windows Communication Foundation (WCF) webové služby (obvykle označuje jako služeb pracovních postupů) vytvořené v WF3 WF4, použít pro běžné scénáře pro out-of-box aktivity.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Activities.Statements.Interop>
