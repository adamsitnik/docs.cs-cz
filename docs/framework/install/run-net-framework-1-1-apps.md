---
title: Spouštění aplikací využívajících .NET Framework 1.1 v systému Windows 8, Windows 8.1 nebo Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aae87b60e207ebe406e863f123e1dc3e56aeb4f7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051939"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Spouštění aplikací využívajících .NET Framework 1.1 v systému Windows 8, Windows 8.1 nebo Windows 10

.NET Framework [!INCLUDE[win8](../../../includes/win8-md.md)]1,1 není podporován v operačních systémech, [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], nebo Windows 10. V některých případech je .NET Framework 1,1 specificky identifikována jako požadovaná pro spuštění aplikace. V těchto případech byste se měli obrátit na nezávislého výrobce softwaru (ISV), aby se aplikace upgradovala, aby běžela v .NET Framework 3,5 SP1 nebo novější verzi. Další informace najdete v tématu [migrace z .NET Framework 1,1](../migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Instalace .NET Framework 1,1 z disku CD nebo stažení softwaru

Nelze ručně nainstalovat [!INCLUDE[win8](../../../includes/win8-md.md)].NET Framework 1,1 na systémy, [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]nebo Windows 10. Již není podporován. Při pokusu o instalaci balíčku se zobrazí následující chybová zpráva: "Instalace nemůže pokračovat, protože tato verze .NET Framework není kompatibilní s dříve nainstalovanou." Chcete-li tento problém vyřešit, nainstalujte [.NET Framework 3,5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Tato verze zahrnuje .NET Framework 2,0 (verze, která následuje .NET Framework 1,1), která je podporovaná v [!INCLUDE[win8](../../../includes/win8-md.md)]systémech, [!INCLUDE[win81](../../../includes/win81-md.md)]a Windows 10. Vždy byste se měli nejdřív pokusit nainstalovat aplikaci, abyste zjistili, jestli bude automaticky aktualizována na novější verzi .NET Framework. Pokud ne, obraťte se na svého nezávislého výrobce softwaru pro aktualizaci aplikace.

## <a name="see-also"></a>Viz také:

- [Migrace z rozhraní .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8](dotnet-35-windows-10.md)
