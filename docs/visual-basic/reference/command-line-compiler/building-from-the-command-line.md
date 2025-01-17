---
title: Sestavení z příkazového řádku (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: 719ca45403ea56a655f06dbfea7c0fb7e32b34f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046432"
---
# <a name="building-from-the-command-line-visual-basic"></a>Sestavení z příkazového řádku (Visual Basic)

Visual Basic projekt se skládá z jednoho nebo více samostatných zdrojových souborů. Během procesu známého jako kompilace jsou tyto soubory společně umístěny do jednoho balíčku – jeden spustitelný soubor, který lze spustit jako aplikaci.

Visual Basic poskytuje kompilátor příkazového řádku jako alternativu k kompilování programů z integrovaného vývojového prostředí (IDE) sady Visual Studio. Kompilátor příkazového řádku je určený pro situace, kdy nevyžadujete úplnou sadu funkcí v rozhraní IDE – například při použití nebo psaní počítačů s omezeným systémovou pamětí nebo prostorem úložiště.

Chcete-li kompilovat zdrojové soubory z integrovaného vývojového prostředí sady Visual Studio, v nabídce **sestavení** klikněte na příkaz **sestavit** .

> [!TIP]
> Při sestavování souborů projektu pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio můžete zobrazit informace o přidruženém příkazu **Vbc** a jeho přepínačích v okně výstup. Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavte a spusťte](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a pak nastavte **Podrobnosti výstupu sestavení projektu MSBuild** na **normální** nebo vyšší úroveň podrobností. Další informace najdete v tématu [jak: Zobrazit, Uložit a nakonfigurovat soubory](/visualstudio/ide/how-to-view-save-and-configure-build-log-files)protokolu sestavení.

Soubory projektu (. vbproj) můžete kompilovat na příkazovém řádku pomocí nástroje MSBuild. Další informace najdete v tématu [reference](/visualstudio/msbuild/msbuild-command-line-reference) k příkazovému řádku [a návod: Pomocí nástroje](/visualstudio/msbuild/walkthrough-using-msbuild)MSBuild.

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: Vyvolat kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) \
Popisuje, jak vyvolat kompilátor příkazového řádku v příkazovém řádku systému MS-DOS nebo z konkrétního podadresáře.

[Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) \
Poskytuje seznam ukázkových příkazových řádků, které můžete upravit pro vlastní použití.

## <a name="related-sections"></a>Související oddíly

[Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md) \
Obsahuje seznam možností kompilátoru uspořádaných podle abecedy nebo podle účelu.

[Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) \
Popisuje, jak zkompilovat konkrétní oddíly kódu.

[Sestavování a čištění projektů a řešení v aplikaci Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) \
Popisuje, jak uspořádat, co bude zahrnuto v různých sestaveních, zvolit vlastnosti projektu a zajistit, aby se projekty vytvořily ve správném pořadí.
