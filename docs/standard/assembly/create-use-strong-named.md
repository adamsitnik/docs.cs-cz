---
title: Vytvoření a použití ssemblies se silným názvem
ms.date: 08/19/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, about strong-named assemblies
- strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, scenarios
- assemblies [.NET Framework], strong-named
- strong-named assemblies, loading into trusted application domains
- assembly binding, strong-named
ms.assetid: ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55869c107d245738df3af5ca9bb1b22195e90024
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973318"
---
# <a name="create-and-use-strong-named-assemblies"></a>Vytváření a používání sestavení se silným názvem

Silný název se skládá z identity sestavení – jednoduchý textový název, číslo verze a informace o jazykové verzi (Pokud je k dispozici) – plus veřejný klíč a digitální podpis. Je vygenerován ze souboru sestavení pomocí odpovídajícího privátního klíče. (Soubor sestavení obsahuje manifest sestavení, který obsahuje názvy a hodnoty hash všech souborů, které tvoří sestavení.)

> [!WARNING]
> Nespoléhá se na silné názvy zabezpečení. Poskytují pouze jedinečnou identitu.

Sestavení se silným názvem může používat pouze typy z jiných sestavení se silným názvem. V opačném případě by došlo k ohrožení integrity sestavení se silným názvem.

> [!NOTE]
> I když .NET Core podporuje sestavení se silným názvem a všechna sestavení v knihovně .NET Core jsou podepsaná, většina sestavení třetích stran nepotřebuje silné názvy. Další informace najdete v tématu [podepisování silného názvu](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) na GitHubu.

## <a name="strong-name-scenario"></a>Scénář se silným názvem

Následující scénář popisuje proces podepisování sestavení silným názvem a pozdějšího odkazování na něj tímto názvem.

1. Sestavení A je vytvořeno se silným názvem pomocí jedné z následujících metod:

    - Použití vývojového prostředí, které podporuje vytváření silných názvů, jako je například Visual Studio.

    - Vytvoření páru kryptografických klíčů pomocí [nástroje Strong Name (Sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md) a přiřazení páru klíčů k sestavení pomocí kompilátoru příkazového řádku nebo [linkeru sestavení (Al. exe)](../../framework/tools/al-exe-assembly-linker.md). Windows SDK poskytuje sn. exe i Al. exe.

2. Vývojové prostředí nebo nástroj podepíše hodnotu hash souboru obsahujícího manifest sestavení pomocí privátního klíče vývojáře. Tento digitální podpis je uložen v přenositelném spustitelném souboru (PE), který obsahuje manifest sestavení A.

3. Sestavení B je příjemcem sestavení A. Referenční oddíl manifestu sestavení B obsahuje token, který představuje veřejný klíč sestavení A. Token je část úplného veřejného klíče a používá se místo toho, aby ušetřil místo samotný klíč.

4. Modul CLR ověří podpis silného názvu, pokud je sestavení umístěno v globální mezipaměti sestavení (GAC). Při vytváření vazby pomocí silného názvu za běhu porovná modul common language runtime klíč uložený v manifestu sestavení B s klíčem použitým k vygenerování silného názvu pro sestavení A. Pokud jsou kontroly zabezpečení .NET Framework úspěšné a vazba je úspěšná, sestavení B zaručí, že bity sestavení A nebyly úmyslně manipulovány a že tyto bity skutečně pochází od vývojářů sestavení A.

> [!NOTE]
> Tento scénář neřeší problémy důvěryhodnosti. Sestavení mohou mít kromě silného názvu také úplné signatury technologie Microsoft Authenticode. Podpisy Authenticode obsahují certifikát, který vytváří vztah důvěryhodnosti. Je důležité si uvědomit, že silné názvy nevyžadují, aby byl kód podepsán tímto způsobem. Silné názvy poskytují pouze jedinečnou identitu.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>Obejít ověření podpisu důvěryhodných sestavení

Počínaje verzí .NET Framework 3,5 Service Pack 1 nejsou signatury se silným názvem ověřovány, když je sestavení načteno do domény aplikace s plnou důvěryhodností, jako je například výchozí aplikační doména pro `MyComputer` zónu. To se označuje jako funkce obcházení silného názvu. V prostředí s úplným vztahem důvěryhodnosti požadavky <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsaná, plně důvěryhodná sestavení, bez ohledu na jejich podpis. Funkce obcházení silného názvu brání zbytečné režii při ověřování signatury silného názvu v plně důvěryhodném sestavení v této situaci, což umožňuje rychlejší načítání sestavení.

Funkce obcházení se vztahuje na jakékoli sestavení, které je podepsáno silným názvem a které má následující vlastnosti:

- Plně důvěryhodné bez <xref:System.Security.Policy.StrongName> legitimace (například má `MyComputer` legitimaci zóny).

- Načteno do plně důvěryhodného <xref:System.AppDomain>.

- Načteno z umístění pod <xref:System.AppDomainSetup.ApplicationBase%2A> vlastností. <xref:System.AppDomain>

- Nepodepsaná se zpožděním.

Tato funkce se dá zakázat pro jednotlivé aplikace nebo pro počítač. Viz [jak: Zakažte funkci](disable-strong-name-bypass-feature.md)obcházení silného názvu.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Postupy: Vytvoření páru klíčů veřejného a soukromého](create-public-private-key-pair.md)|Popisuje, jak vytvořit pár kryptografických klíčů pro podepsání sestavení.|
|[Postupy: Podepsat sestavení silným názvem](sign-strong-name.md)|Popisuje, jak vytvořit sestavení se silným názvem.|
|[Rozšířené silné názvy](enhanced-strong-naming.md)|Popisuje vylepšení pro silné názvy v .NET Framework 4,5.|
|[Postupy: Odkazování na sestavení se silným názvem](reference-strong-named.md)|Popisuje, jak odkazovat na typy nebo prostředky v sestavení se silným názvem v době kompilace nebo v době běhu.|
|[Postupy: Zakázat funkci obcházení silného názvu](disable-strong-name-bypass-feature.md)|Popisuje, jak zakázat funkci, která obchází ověřování podpisů se silným názvem. Tuto funkci je možné zakázat pro všechny nebo pro konkrétní aplikace.|
|[Vytváření sestavení](create.md)|Poskytuje přehled o jednom souboru a vícesouborové sestavení.|
|[Jak zpozdit podepsání sestavení v aplikaci Visual Studio](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Vysvětluje, jak podepsat sestavení se silným názvem poté, co bylo sestavení vytvořeno.|
|[SN. exe (Nástroj pro silný název)](../../framework/tools/sn-exe-strong-name-tool.md)|Popisuje nástroj, který je součástí .NET Framework, který pomáhá vytvářet sestavení se silnými názvy. Tento nástroj poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.|
|[Al. exe (linker sestavení)](../../framework/tools/al-exe-assembly-linker.md)|Popisuje nástroj, který je součástí .NET Framework, který generuje soubor s manifestem sestavení z modulů nebo souborů prostředků.|