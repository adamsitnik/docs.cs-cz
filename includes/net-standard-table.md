| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1.5]              | [1.6]              | [2.0]               |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2.0                 |
| .NET Framework <sup>1</sup>| 4.5    | 4.5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5.4                 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 |
| Univerzální platforma pro Windows | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              |

<sup>1 uvedené verze pro rozhraní .NET Framework se vztahují na .NET Core 2.0 SDK a novější verze nástrojů. Starší verze použít jiné mapování pro .NET Standard 1.5 nebo novější. Je možné [stáhnout nástroje pro .NET Core tools for Visual Studio 2015](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md) pokud nejde upgradovat na Visual Studio 2017.</sup>

<sup>2 verze zde uvedené představují pravidla, která NuGet používá k určení, zda danou knihovnu .NET Standard platí. Když bude považovat za NuGet rozhraní .NET Framework 4.6.1 jako podpora .NET Standard 1.5 prostřednictvím 2.0, existuje několik výhrad využívání knihovny .NET Standard, které byly vytvořeny pro tyto verze z projektů .NET Framework 4.6.1. Pro projekty .NET Framework, které je potřeba použít tyto knihovny doporučujeme upgradovat projekt na cílové rozhraní .NET Framework 4.7.2 nebo vyšší.</sup>

- Sloupce, které představují verze .NET Standard. Každá buňka záhlaví je odkaz na dokument, který ukazuje, které rozhraní API je teď přidáno ve verzi .NET Standard.
- Řádky představují různé implementace .NET.
- Určuje číslo verze v každé buňce *minimální* verzi implementace budete potřebovat k cílení na tuto verzi rozhraní .NET Standard.
- Interaktivní tabulky, najdete v části [.NET Standard verze](https://immo.landwerth.net/netstandard-versions/#).

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1.5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
