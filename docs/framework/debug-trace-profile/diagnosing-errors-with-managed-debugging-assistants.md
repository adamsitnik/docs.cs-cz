---
title: Diagnostikování chyb pomocí asistentů spravovaného ladění
ms.date: 08/14/2018
f1_keywords:
- EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6cb2a240a2e7e82b7015eb7a6d99c2117fa63045
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052889"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a>Diagnostikování chyb pomocí asistentů spravovaného ladění

Asistenti spravovaného ladění (MDA) jsou pomůcky pro ladění, které spolupracují s modulem CLR (Common Language Runtime) k poskytování informací o stavu modulu runtime. Pomocníci generují informativní zprávy o událostech modulu runtime, které nemůžete jinak zachytávat. MDA můžete použít k izolaci chyb aplikace, ke kterým dochází při přechodu mezi spravovaným a nespravovaným kódem.

Všechny MDA můžete [Povolit nebo zakázat](#enable-and-disable-mdas) přidáním klíče do registru systému Windows nebo nastavením proměnné prostředí. Můžete povolit konkrétní MDA pomocí nastavení konfigurace aplikace. V konfiguračním souboru aplikace můžete nastavit další nastavení konfigurace pro konkrétní MDA. Vzhledem k tomu, že jsou tyto konfigurační soubory analyzovány při načtení modulu runtime, je nutné povolit modul MDA před spuštěním spravované aplikace. Nemůžete ho povolit pro aplikace, které už jsou spuštěné.

V následující tabulce jsou uvedeny Mday dodávané s .NET Framework:

|||
|-|-|
|[asynchronousThreadAbort](asynchronousthreadabort-mda.md)|[bindingFailure](bindingfailure-mda.md)|
|[callbackOnCollectedDelegate](callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](contextswitchdeadlock-mda.md)|
|[dangerousThreadingAPI](dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](datetimeinvalidlocalformat-mda.md)|
|[dirtyCastAndCallOnInterface](dirtycastandcalloninterface-mda.md)|[disconnectedContext](disconnectedcontext-mda.md)|
|[dllMainReturnsFalse](dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](exceptionswallowedoncallfromcom-mda.md)|
|[failedQI](failedqi-mda.md)|[fatalExecutionEngineError](fatalexecutionengineerror-mda.md)|
|[gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)|
|[illegalPrepareConstrainedRegion](illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](invalidapartmentstatechange-mda.md)|
|[invalidCERCall](invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](invalidfunctionpointerindelegate-mda.md)|
|[invalidGCHandleCookie](invalidgchandlecookie-mda.md)|[invalidIUnknown](invalidiunknown-mda.md)|
|[invalidMemberDeclaration](invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](invalidoverlappedtopinvoke-mda.md)|
|[invalidVariant](invalidvariant-mda.md)|[jitCompilationStart](jitcompilationstart-mda.md)|
|[loaderLock](loaderlock-mda.md)|[loadFromContext](loadfromcontext-mda.md)|
|[marshalCleanupError](marshalcleanuperror-mda.md)|[marshaling](marshaling-mda.md)|
|[memberInfoCacheCreation](memberinfocachecreation-mda.md)|[moduloObjectHashcode](moduloobjecthashcode-mda.md)|
|[nonComVisibleBaseClass](noncomvisiblebaseclass-mda.md)|[notMarshalable](notmarshalable-mda.md)|
|[openGenericCERCall](opengenericcercall-mda.md)|[overlappedFreeError](overlappedfreeerror-mda.md)|
|[pInvokeLog](pinvokelog-mda.md)|[pInvokeStackImbalance](pinvokestackimbalance-mda.md)|
|[raceOnRCWCleanup](raceonrcwcleanup-mda.md)|[reentrancy](reentrancy-mda.md)|
|[releaseHandleFailed](releasehandlefailed-mda.md)|[reportAvOnComRelease](reportavoncomrelease-mda.md)|
|[streamWriterBufferedDataLost](streamwriterbuffereddatalost-mda.md)|[virtualCERCall](virtualcercall-mda.md)|

Ve výchozím nastavení .NET Framework aktivuje podmnožinu MDA pro všechny spravované ladicí programy. Můžete zobrazit výchozí sadu v sadě Visual Studio výběrem**Možnosti nastavení výjimek** **systému Windows** > v nabídce **ladění** a následným rozbalením seznamu **asistentů spravovaného ladění** .

![Okno Nastavení výjimek v aplikaci Visual Studio](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a>Povolit a zakázat MDA

MDA můžete povolit a zakázat pomocí klíče registru, proměnné prostředí a nastavení konfigurace aplikace. Chcete-li použít nastavení konfigurace aplikace, musíte povolit buď klíč registru, nebo proměnnou prostředí.

> [!TIP]
> Místo zakázání MDA můžete aplikaci Visual Studio zabránit v zobrazení dialogového okna MDA vždy, když se přijme oznámení MDA. To provedete tak, že v nabídce **ladění** zvolíte možnost**Nastavení výjimek** **systému Windows** > , rozbalíte seznam **asistenti spravovaného ladění** a potom zaškrtnutím nebo zrušením zaškrtnutí políčka **přerušit při vyvolání** pro jednotlivý MDA.

### <a name="registry-key"></a>Klíč registru

Pokud chcete povolit MDA, přidejte **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\MDA** podklíč (typ REG_SZ, hodnota 1) v registru systému Windows. Zkopírujte následující příklad do textového souboru s názvem *MDAEnable. reg*. Otevřete Editor registru systému Windows (Regedit. exe) a v nabídce **soubor** vyberte **importovat**. Vyberte soubor *MDAEnable. reg* , který povolí MDA na tomto počítači. Nastavení podklíče na řetězcovou hodnotu **1** (ne hodnota DWORD **1**) umožňuje číst nastavení MDA ze souboru *ApplicationName. přípon*. MDA. config. Například konfigurační soubor MDA pro Poznámkový blok by měl název Notepad. exe. MDA. config.

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

Pokud je v počítači spuštěná 32 aplikace na 64 operačním systému, klíč MDA by měl být nastaven jako následující:

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

Další informace najdete v tématu [nastavení konfigurace specifické pro aplikaci](#application-specific-configuration-settings) . Nastavení registru lze přepsat proměnnou prostředí COMPLUS_MDA. Další informace naleznete v tématu [Proměnná prostředí](#environment-variable) .

Pokud chcete zakázat MDA, nastavte podklíč MDA na **hodnotu 0** (nula) pomocí Editoru registru Windows.

Ve výchozím nastavení jsou některé MDA povolené, když spustíte aplikaci, která je připojená k ladicímu programu, a to i bez přidání klíče registru. Tyto asistenty můžete zakázat spuštěním souboru *MDADisable. reg* , jak je popsáno výše v této části.

### <a name="environment-variable"></a>Proměnná prostředí

Aktivaci MDA můžete také ovládat pomocí proměnné prostředí COMPLUS_MDA, která přepisuje klíč registru. COMPLUS_MDA řetězec rozlišuje malá a velká písmena, čárkami oddělený seznam názvů MDA nebo jiné speciální řetězce ovládacích prvků. Od spravovaného nebo nespravovaného ladicího programu je ve výchozím nastavení povolená sada MDA. To se provádí implicitně předem vydaným seznamem MDA, který je ve výchozím nastavení povolený, v části Debuggery na hodnotu proměnné prostředí nebo klíče registru. Speciální řetězce ovládacích prvků jsou následující:

- `0`-Deaktivuje všechny MDA.

- `1`-Přečte nastavení MDA z *ApplicationName*. MDA. config.

- `managedDebugger`– Explicitně aktivuje všechny MDA, které jsou implicitně aktivované při spuštění spravovaného spustitelného souboru v ladicím programu.

- `unmanagedDebugger`– Explicitně aktivuje všechny MDA, které jsou implicitně aktivované při spuštění nespravovaného spustitelného souboru v ladicím programu.

Pokud existují konfliktní nastavení, přepíše předchozí nastavení poslední nastavení:

- `COMPLUS_MDA=0`zakáže všechny MDA, včetně těch, které jsou implicitně povolené v rámci ladicího programu.

- `COMPLUS_MDA=gcUnmanagedToManaged`povoluje `gcUnmanagedToManaged` se kromě všech MDA, které jsou implicitně povoleny v rámci ladicího programu.

- `COMPLUS_MDA=0;gcUnmanagedToManaged`povoluje `gcUnmanagedToManaged` , ale zakáže MDA, které by jinak byly implicitně povoleny v rámci ladicího programu.

### <a name="application-specific-configuration-settings"></a>Nastavení konfigurace specifické pro aplikaci

V konfiguračním souboru MDA pro aplikaci můžete povolit, zakázat a nakonfigurovat některé pomocníky jednotlivě. Pokud chcete povolit použití konfiguračního souboru aplikace pro konfiguraci MDA, musí být nastaven buď klíč registru MDA, nebo proměnná prostředí COMPLUS_MDA. Konfigurační soubor aplikace je obvykle umístěn ve stejném adresáři jako spustitelný soubor aplikace (. exe). Název souboru má formát *ApplicationName*. MDA. config; například Notepad. exe. MDA. config. Asistenti, kteří jsou povoleni v konfiguračním souboru aplikace, mohou mít atributy nebo prvky specificky navržené pro řízení chování tohoto asistenta.

Následující příklad ukazuje, jak povolit a nakonfigurovat [zařazování](marshaling-mda.md):

```xml
<mdaConfig>
  <assistants>
    <marshaling>
      <methodFilter>
        <match name="*"/>
      </methodFilter>
      <fieldFilter>
        <match name="*"/>
      </fieldFilter>
    </marshaling>
  </assistants>
</mdaConfig>
```

`Marshaling` MDA generuje informace o spravovaném typu, který je zařazen do nespravovaného typu pro každý spravovaný a nespravovaný přechod v aplikaci. MDA může také filtrovat názvy polí metody a struktury, které jsou zadány v podřízených prvcích methodFilter a **FieldFilter** v uvedeném pořadí. `Marshaling`

Následující příklad ukazuje, jak povolit více MDA pomocí jejich výchozích nastavení:

```xml
<mdaConfig>
  <assistants>
    <illegalPrepareConstrainedRegion />
    <invalidCERCall />
    <openGenericCERCall />
    <virtualCERCall />
  </assistants>
</mdaConfig>
```

> [!IMPORTANT]
> Pokud v konfiguračním souboru zadáte více než jednoho pomocníka, je nutné je uvést v abecedním pořadí. `virtualCERCall` Například pokud chcete povolit `invalidCERCall` i MDA `<invalidCERCall />` , musíte `<virtualCERCall />` přidat položku před zadáním. Pokud položky nejsou v abecedním pořadí, zobrazí se Neošetřená neplatná zpráva o výjimce konfiguračního souboru.

## <a name="mda-exceptions"></a>MDA – výjimky

Když je povolený MDA, je aktivní, a to i v případě, že váš kód není spuštěný v ladicím programu. Je-li událost MDA vyvolána, když není k dispozici ladicí program, zpráva o události je uvedena v dialogovém okně Neošetřená výjimka, i když se nejedná o neošetřenou výjimku. Chcete-li se vyhnout dialogovému oknu, odeberte nastavení MDA-povolování, když váš kód není spuštěn v ladicím prostředí.

Když se váš kód spustí v integrovaném vývojovém prostředí (IDE) sady Visual Studio, můžete se vyhnout dialogovému oknu výjimky, která se zobrazí pro konkrétní události MDA. Chcete-li to provést, v nabídce **ladění** vyberte možnost**Nastavení výjimek** **systému Windows** > . V okně **Nastavení výjimek** rozbalte seznam **asistenti spravovaného ladění** a potom zrušte zaškrtnutí políčka **přerušit při vyvolání** pro jednotlivý MDA. Pomocí tohoto dialogového okna můžete také *Povolit* zobrazení dialogových oken s výjimkou MDA.

## <a name="mda-output"></a>Výstup MDA

Výstup MDA je podobný následujícímu příkladu, který zobrazuje výstup z `PInvokeStackImbalance` MDA:

**Volání funkce PInvoke ' MDATest! MDATest. program:: StdCall zrušil vyvážení zásobníku. To je pravděpodobně způsobeno tím, že spravovaný podpis PInvoke neodpovídá nespravovanému cílovému podpisu. Ověřte, že konvence volání a parametry signatury PInvoke odpovídají cílovému nespravovanému podpisu.**

## <a name="see-also"></a>Viz také:

- [Ladění, trasování a profilace](index.md)
