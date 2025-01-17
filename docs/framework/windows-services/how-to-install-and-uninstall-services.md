---
title: 'Postupy: instalace a odinstalace služeb systému Windows'
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 38fc0172b5f97561d69fe495237e95597d7b9727
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003131"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Postupy: instalace a odinstalace služeb systému Windows

Pokud vyvíjíte službu pro Windows s .NET Framework, můžete rychle nainstalovat aplikaci služby pomocí nástroje příkazového řádku [*Installutil. exe*](../tools/installutil-exe-installer-tool.md) nebo [PowerShellu](/powershell/scripting/overview). Vývojáři, kteří chtějí uvolnit službu systému Windows, kterou mohou uživatelé instalovat a odinstalovat, by měli používat program InstallShield. Další informace najdete v tématu [Vytvoření instalačního balíčku (klient Windows)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).

> [!WARNING]
> Pokud chcete odinstalovat službu z počítače, neprovádějte postup v tomto článku. Místo toho Zjistěte, který program nebo softwarový balíček službu nainstaloval, a pak zvolte možnost **aplikace** v nastavení pro odinstalaci tohoto programu. Všimněte si, že mnoho služeb je nedílnou součástí Windows. Pokud je odstraníte, může to způsobit nestabilitu systému.

Chcete-li použít kroky v tomto článku, musíte nejprve přidat do služby systému Windows Instalační program služby. Další informace najdete v tématu [Návod: Vytvoření aplikace služby systému Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

Nemůžete spustit projekty služby Windows přímo z vývojového prostředí sady Visual Studio stisknutím klávesy F5. Předtím, než můžete spustit projekt, je nutné nainstalovat službu do projektu.

> [!TIP]
> Pomocí **Průzkumník serveru** můžete ověřit, že jste nainstalovali nebo odinstalovali vaši službu. Další informace najdete v tématu [Jak používat Průzkumník serveru v aplikaci Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually-using-installutilexe-utility"></a>Ruční instalace služby pomocí nástroje InstallUtil. exe

1. V nabídce **Start** vyberte adresář sady **Visual Studio \<*verze*>** a pak vyberte **Developer Command Prompt pro vs \<*verze*>** .

     Zobrazí se Developer Command Prompt pro Visual Studio.

2. Přejděte do adresáře, kde se nachází kompilovaný spustitelný soubor projektu.

3. Spusťte *Installutil. exe* z příkazového řádku s spustitelným souborem vašeho projektu jako parametr:

    ```console
    installutil <yourproject>.exe
    ```

     Pokud používáte Developer Command Prompt pro Visual Studio, musí být *Installutil. exe* v systémové cestě. V opačném případě ji můžete přidat do cesty nebo použít úplnou cestu k jejímu vyvolání. Tento nástroj se instaluje s .NET Framework v *%windir%\Microsoft.NET\Framework [64] \\ < framework_version @ no__t-2*.

     Příklad:
     - Pro 32 verze .NET Framework 4 nebo 4,5 a novější, pokud je instalační adresář systému Windows *C:\Windows*, je výchozí cesta *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - Pro 64-bitovou verzi .NET Framework 4 nebo 4,5 a novější je výchozí cesta *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a>Ruční odinstalace služby pomocí nástroje InstallUtil. exe

1. V nabídce **Start** vyberte adresář sady **Visual Studio \<*verze*>** a pak vyberte **Developer Command Prompt pro vs \<*verze*>** .

     Zobrazí se Developer Command Prompt pro Visual Studio.

2. Spusťte *Installutil. exe* z příkazového řádku s výstupem vašeho projektu jako parametr:

    ```console
    installutil /u <yourproject>.exe
    ```

3. Po odstranění spustitelného souboru pro službu může být služba v registru stále k dispozici. V takovém případě pomocí příkazu [sc delete](/windows-server/administration/windows-commands/sc-delete) odeberte položku služby z registru.

### <a name="install-your-service-manually-using-powershell"></a>Ruční instalace služby pomocí PowerShellu

1. V nabídce **Start** vyberte adresář **Windows PowerShell** a pak vyberte **Windows PowerShell**.

2. Přejděte do adresáře, kde se nachází kompilovaný spustitelný soubor projektu.

3. Spusťte rutinu [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) s výstupem vašeho projektu a názvem služby jako parametry:

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a>Ruční odinstalace služby pomocí PowerShellu

1. V nabídce **Start** vyberte adresář **Windows PowerShell** a pak vyberte **Windows PowerShell**.

2. Spusťte rutinu [**remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) s názvem vaší služby jako parametr:

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. Po odstranění spustitelného souboru pro službu může být služba v registru stále k dispozici. V takovém případě pomocí příkazu [sc delete](/windows-server/administration/windows-commands/sc-delete) odeberte položku služby z registru.

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a>Viz také:

- [Úvod do aplikací služby systému Windows](../windows-services/introduction-to-windows-service-applications.md)
- [Postupy: vytváření služeb systému Windows](../windows-services/how-to-create-windows-services.md)
- [Postupy: Přidání instalačních programů do aplikace služby](../windows-services/how-to-add-installers-to-your-service-application.md)
- [InstallUtil. exe (instalační nástroj)](../tools/installutil-exe-installer-tool.md)
