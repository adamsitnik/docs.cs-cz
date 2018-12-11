---
title: Testování publikované výstup s dotnet test
description: Zjistěte, jak spustit testy na publikované knihovny, místo na zdrojový kód, pomocí příkazu dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 9d842f26336d0ddf5375d49676523086bb632684
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239524"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testování publikované výstup s dotnet test

Je možné spustit testy na výstupu už byla publikována s použitím `dotnet vstest` příkazu. Bude to fungovat u xUnit, MSTest a NUnit testy. Jednoduše vyhledejte soubor knihovny DLL, která byla součástí publikovaný výstup a spusťte:

```
dotnet vstest <MyPublishedTests>.dll
```

kde `<MyPublishedTests>` je název publikované testovacího projektu.

## <a name="example"></a>Příklad

Následující příkazy ukazují, spouštění testů na publikované knihovny DLL.

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Poznámka: Pokud vaše aplikace cílí na rozhraní než `netcoreapp` můžete nadále spouštět `dotnet vstest` příkaz předáním s příznakem framework cíleného rozhraní. Například, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. Ve verzi Visual Studio 2017 Update 5 je automaticky rozpoznán požadované rozhraní.

## <a name="see-also"></a>Viz také:
- [Testování částí pomocí příkazu dotnet test a xUnit](unit-testing-with-dotnet-test.md)
- [Testování částí pomocí příkazu dotnet test a NUnit](unit-testing-with-nunit.md)
- [Testování částí pomocí příkazu dotnet test a MSTest](unit-testing-with-mstest.md)
