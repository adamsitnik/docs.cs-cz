---
title: Hello World – váš první program pomocí sady Visual Studio ve Windows nebo v systému C# Mac – Průvodce programováním
ms.custom: seodec18
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: edab64bf02a2b60cce21af536d2da98193dea9a1
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196213"
---
# <a name="hello-world----your-first-program"></a>Hello World – první program

V tomto článku použijete Visual Studio k vytvoření tradičního "Hello World!" editoru. Visual Studio je profesionální integrované vývojové prostředí (IDE) s řadou funkcí navržených pro vývoj pro .NET. K vytvoření tohoto programu použijete pouze několik funkcí v aplikaci Visual Studio. Další informace o aplikaci Visual Studio naleznete v tématu [Začínáme with C#Visual ](/visualstudio/ide/quickstart-csharp-console).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>Vytvoření nové aplikace

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

Spusťte Visual Studio. Ve Windows se zobrazí následující obrázek:

![Úvodní obrazovka sady Visual Studio ve Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

Vyberte **vytvořit nový projekt** v pravém dolním rohu obrázku. Visual Studio zobrazí dialogové okno **Nový projekt** :

![Obrazovka nového projektu v aplikaci Visual Studio ve Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> Pokud jste spustili aplikaci Visual Studio poprvé, seznam **naposledy použitých šablon projektů** je prázdný.

V dialogovém okně Nový projekt zvolte možnost Konzolová aplikace (.NET Core) a potom stiskněte tlačítko **Další**. Zadejte název vašeho projektu, například HelloWorld, a pak stiskněte **vytvořit**.

Visual Studio otevře projekt. Už je základní "Hello World!". případě. Spusťte projekt stisknutím `Ctrl` + `F5`. Visual Studio sestaví projekt a převede zdrojový kód na spustitelný soubor. Potom spustí příkazové okno, které spustí vaši novou aplikaci. V okně byste měli vidět následující text:

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

Stisknutím klávesy zavřete okno.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Spusťte Visual Studio pro Mac. Na Macu se zobrazí následující obrázek:

![Úvodní obrazovka sady Visual Studio na Macu](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> Pokud Visual Studio pro Macte poprvé, seznam **posledních projektů** je prázdný.

V pravém horním rohu obrázku vyberte **Nový** . Visual Studio pro Mac zobrazí dialog **Nový projekt** :

![Obrazovka nového projektu v aplikaci Visual Studio na Macu](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

V dialogovém okně Nový projekt vyberte .NET Core a Konzolová aplikace a pak klikněte na **Další**. Bude nutné vybrat cílovou architekturu. Ve výchozím nastavení je to v pořádku, takže stiskněte tlačítko Další. Zadejte název vašeho projektu, například HelloWorld, a pak stiskněte **vytvořit**. Můžete použít výchozí umístění projektu. Nepřidávat tento projekt do správy zdrojových kódů.

Visual Studio pro Mac otevře projekt. Už je základní "Hello World!". případě. Stiskněte `Ctrl` + `Fn` + `F5` ke spuštění projektu. Visual Studio pro Mac sestavit projekt a převod zdrojového kódu na spustitelný soubor. Potom spustí příkazové okno, které spustí vaši novou aplikaci. V okně byste měli vidět následující text:

```console
Hello World!

Press any key to close this window . . .
```

Ukončete relaci stisknutím klávesy.

---

## <a name="elements-of-a-c-program"></a>Prvky C# programu

Pojďme se podívat na důležité části tohoto programu. První řádek obsahuje komentář. Znaky `//` převedou zbytek čáry na komentář.

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Můžete také odkomentovat blok textu uzavřením mezi `/*` a `*/` znaky. To je ukázáno v následujícím příkladu.

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

C# Konzolová aplikace musí obsahovat metodu `Main`, ve které ovládací prvek začíná a končí. Metoda `Main` je místo, kde vytvoříte objekty a spustíte jiné metody.

Metoda `Main` je [statická](../../language-reference/keywords/static.md) metoda, která se nachází uvnitř třídy nebo struktury. V předchozím "Hello World!" například se nachází ve třídě s názvem `Hello`. Metodu `Main` lze deklarovat jedním z následujících způsobů:

- Může vracet `void`. To znamená, že váš program nevrací hodnotu.

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Může také vracet celé číslo. Celé číslo je **ukončovací kód** vaší aplikace.

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- U obou návratových typů může vzít v úvahu argumenty.

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

-nebo-

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Parametr metody `Main`, `args`, je pole `string`, které obsahuje argumenty příkazového řádku, které se používají k vyvolání programu.

Další informace o tom, jak používat argumenty příkazového řádku, naleznete v příkladech v části [Main () a argumenty příkazového řádku](../main-and-command-args/index.md).

## <a name="input-and-output"></a>Vstup a výstup

C#programy obecně používají vstupní a výstupní služby, které poskytuje knihovna run-time .NET Framework. Příkaz `System.Console.WriteLine("Hello World!");` používá metodu <xref:System.Console.WriteLine%2A>. Toto je jedna z metod výstupu třídy <xref:System.Console> v běhové knihovně. Zobrazuje parametr řetězce na standardním výstupním streamu následovaný novým řádkem. Další metody <xref:System.Console> jsou k dispozici pro různé vstupní a výstupní operace. Pokud zadáte direktivu `using System;` na začátku programu, můžete přímo použít <xref:System> třídy a metody bez jejich úplného zařazení. Například můžete volat `Console.WriteLine` místo `System.Console.WriteLine`:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Další informace o metodách vstupu a výstupu naleznete v tématu <xref:System.IO>.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Ukázky a kurzy](../../../samples-and-tutorials/index.md)
- [Argumenty Main() a příkazového řádku](../main-and-command-args/index.md)
- [Začínáme pomocí vizuáluC#](/visualstudio/ide/quickstart-csharp-console)
