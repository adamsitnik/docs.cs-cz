---
title: Obsah sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- assemblies [.NET Core]
- single-file assemblies
- multifile assemblies [.NET Framework]
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: 9ca12ee4bd993db3dd200a3b340c220ce5188796
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122535"
---
# <a name="assembly-contents"></a>Obsah sestavení
Obecně platí, že statické sestavení se může skládat ze čtyř prvků:

- [Manifest sestavení](manifest.md), který obsahuje metadata sestavení.

- Zadejte metadata.  

- Kód jazyka MSIL (Microsoft Intermediate Language), který implementuje typy. Je generován kompilátorem z jednoho nebo více souborů zdrojového kódu.

- Sada prostředků.  

Vyžaduje se pouze manifest sestavení, ale k sestavení všech smysluplných funkcí je nutné zadat buď typy, nebo prostředky.

Následující ilustrace znázorňuje tyto prvky seskupené do jednoho fyzického souboru.

![Diagram, který zobrazuje sestavení s jedním souborem s názvem MyAssembly. dll.](./media/contents/single-file-assembly.gif)

Na tomto obrázku všechny tři soubory patří do sestavení, jak je popsáno v manifestu sestavení obsaženém v MyAssembly. dll. Do systému souborů jsou tři samostatné soubory. Soubor Util.netmodule byl zkompilován jako modul, protože neobsahuje žádné informace o sestavení. Při vytváření sestavení byl manifest sestavení přidán do knihovny MyAssembly.dll, čímž je naznačen vztah se soubory Util.netmodule a Graphic.bmp.

Při navrhování zdrojového kódu se při rozhodování o tom, jak rozdělit funkce aplikace do jednoho nebo více souborů, provést explicitní rozhodnutí. Při navrhování .NET Framework kódu provedete podobná rozhodnutí týkající se dělení funkcí do jednoho nebo více sestavení.

## <a name="see-also"></a>Viz také:

- [Sestavení v .NET](index.md)
- [Manifest sestavení](manifest.md)
- [Požadavky na zabezpečení sestavení](security-considerations.md)
