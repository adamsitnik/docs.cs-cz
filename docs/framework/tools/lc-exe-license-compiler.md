---
title: Lc.exe (kompilátor licencí)
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 17ab7317ff1147dc79fae4ef3068cd9bc2143907
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774208"
---
# <a name="lcexe-license-compiler"></a>Lc.exe (kompilátor licencí)
License Compiler čte textové soubory, které obsahují licenční informace a vytváří binární soubor, který může být integrován jako prostředek do spustitelného souboru modulu CLR (Common Language Runtime).  
  
 Textový soubor .licx se automaticky vygeneruje nebo aktualizuje prostřednictvím Návrháře formulářů Windows pokaždé, když je do formuláře přidán licencovaný ovládací prvek. Jako část kompilace bude systém projektu transformovat textový soubor .licx na binární prostředek .licenses, který podporuje licencování ovládacích prvků .NET. Binární prostředek bude poté vložen do výstupu projektu.  
  
 Křížová kompilace mezi 32 bity a 64 bity není podporována, jestliže při sestavování projektu použijete License Compiler. Důvodem je, že License Compiler musí načíst sestavení, přičemž načítání 64bitových sestavení z 32bitové aplikace není povoleno a naopak. V tomto případě použijte License Compiler z příkazového řádku k ruční kompilaci licence a zadejte odpovídající architekturu.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/complist:** *název souboru*|Určuje název souboru, který obsahuje seznam licencovaných součástí, jež chcete zahrnout do souboru .licenses. Jednotlivé komponenty se odkazují pomocí úplného názvu, vždy pouze jedna komponenta na řádek.<br /><br /> Uživatelé příkazového řádku mohou určit samostatný soubor pro každý formulář v projektu. Lc.exe akceptuje více vstupních souborů a vytváří jeden soubor .licenses.|  
|**/h**[**ELP**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/i:** *modul*|Určuje moduly, které obsahují součásti uvedené v souboru **/complist** . Pokud chcete zadat víc než jeden modul, použijte několik příznaků **/i** .|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/OutDir:** *cesta*|Určuje adresář, do kterého má být umístěn výstupní soubor .licenses.|  
|**/target:** *targetPE*|Určuje spustitelný soubor, pro který je generován soubor .licenses.|  
|**/v**|Určuje režim podrobného vypisování; zobrazuje informace o průběhu kompilace.|  
|*soubor* @|Určuje soubor odpovědi (. rsp).|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="example"></a>Příklad  
  
1. Pokud používáte licencovaný ovládací prvek `MyCompany.Samples.LicControl1` obsažený v `Samples.DLL` v aplikaci s názvem `HostApp.exe` *,* můžete vytvořit `HostAppLic.txt`, který obsahuje následující.  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. Pomocí následujícího příkazu vytvořte soubor. licenses s názvem `HostApp.exe.licenses`.  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. Sestavte `HostApp.exe` včetně souboru. licenses jako prostředku. Pokud vytváříte aplikace C#, měli byste k sestavení aplikace použít následující příkaz.  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 Následující příkaz zkompiluje `myApp.licenses` ze seznamu licencovaných komponent určených `hostapplic.txt`, `hostapplic2.txt` a `hostapplic3.txt`. Argument `modulesList` Určuje moduly, které obsahují licencované součásti.  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a>Příklad souboru odezvy  
 Následující výpis ukazuje příklad souboru odpovědi `response.rsp`. Další informace o souborech odpovědí naleznete v tématu [soubory odpovědí](/visualstudio/msbuild/msbuild-response-files).  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
```  
  
 Následující příkazový řádek používá soubor `response.rsp`.  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Al.exe (linker sestavení)](al-exe-assembly-linker.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
