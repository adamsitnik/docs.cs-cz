---
title: Přehled zabezpečení automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: c74f770f917fc3b2a7d3a18c08270745dac68b12
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422435"
---
# <a name="ui-automation-security-overview"></a>Přehled zabezpečení automatizace uživatelského rozhraní

> [!NOTE]
> Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).

Tento přehled popisuje model zabezpečení pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] v [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>řízení uživatelských účtů

Zabezpečení je hlavní fokus [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] a mezi inovace je možnost uživatelů ke spuštění jako standardní uživatelé (bez oprávnění správce) bez nutně se blokovat spouštění aplikací a služeb, které vyžadují vyšší oprávnění.

V [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], většina aplikací jsou součástí standardní nebo token pro správu. Pokud aplikace nelze identifikovat jako aplikace pro správu, se spustí jako standardní aplikace ve výchozím nastavení. Mohou být spuštěny před aplikaci identifikovat jako správce, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] zobrazí výzvu k souhlasu, spusťte aplikaci jako se zvýšenými oprávněními. Ve výchozím nastavení, se zobrazí výzva k povolení spuštění, i v případě, že uživatel je členem místní skupiny Administrators, protože správce spustit jako standardní uživatele, dokud aplikace nebo součást systému, který vyžaduje přihlašovací údaje pro správu vyžaduje oprávnění ke spuštění.

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>Úloh vyžadujících vyšší úrovní oprávnění

Když se uživatel pokusí provést úlohu, která vyžaduje oprávnění správce, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] zobrazí dialogové okno s dotazem uživatele o souhlas, abyste mohli pokračovat. Toto dialogové okno je chránit z komunikace mezi procesy tak, aby škodlivého softwaru nelze simulovat vstup uživatele. Obdobně obrazovky přihlášení k ploše obvykle přístupné s jinými procesy.

Klienti automatizace uživatelského rozhraní, musí komunikovat s dalšími procesy, některé z nich možná běží na vyšší úrovni oprávnění. Klienti můžou potřebovat přístup k systému dialogových oknech, které nejsou obvykle viditelná pro jiné procesy. Proto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klientů musí být důvěryhodná systému a musí být spuštěna s zvláštní oprávnění.

Aby byl důvěryhodný ke komunikaci s aplikací běžících na vyšší úrovni oprávnění, musí být podepsané aplikace.

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>Soubory manifestu

K získání přístupu k systému chráněné uživatelského rozhraní, musí být sestaveny aplikací se souborem manifestu, který zahrnuje `uiAccess` atribut `requestedExecutionLevel` označte následujícím způsobem:

```xml
<trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
  <security>
    <requestedPrivileges>
      <requestedExecutionLevel
        level="highestAvailable"
        uiAccess="true" />
    </requestedPrivileges>
  </security>
</trustInfo>
```

Hodnota `level` atribut v tomto kódu je pouze příklad.

`uiAccess` je ve výchozím nastavení; "false" To znamená pokud atribut vynecháte nebo pokud neexistuje žádný manifest sestavení, aplikace nebude schopen získat přístup k chráněné uživatelského rozhraní.

Další informace o [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] najdete v článku o podepisování aplikací a k vytvoření sestavení manifesty zabezpečení [Developer doporučené postupy a pokyny pro aplikace v prostředí s nejméně privilegovaný](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480150(v=msdn.10)).
