---
title: Jazyková nezávislost a jazykově nezávislé komponenty
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- language interoperability
- Common Language Specification
- cross-language interoperability
- CLS
- runtime, language interoperability
- common language runtime, language interoperability
ms.assetid: 4f0b77d0-4844-464f-af73-6e06bedeafc6
ms.openlocfilehash: 689ca9f7278dcf91b12bc62b5255a968388bb9f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120759"
---
# <a name="language-independence-and-language-independent-components"></a>Jazyková nezávislost a jazykově nezávislé komponenty

.NET Framework je nezávislý na jazyce. To znamená, že jako vývojář můžete vyvíjet v jednom z mnoha jazyků, které cílí na .NET Framework, C#jako jsou například C++/CLI, Eiffel, F#, ironpythonu, IronRuby, PowerBuilder, Visual Basic, Visual COBOL a Windows PowerShell. Můžete získat přístup k typům a členům knihoven tříd vyvinutých pro .NET Framework bez nutnosti znát jazyk, ve kterém byly původně zapsány, a nemusíte přitom dodržovat žádnou z původních konvencí jazyka. Pokud jste vývojář komponent, k vaší komponentě se dá dostat z aplikace .NET Framework bez ohledu na jeho jazyk.

> [!NOTE]
> Tato první část tohoto článku popisuje vytváření komponent nezávislých na jazyce – to znamená komponenty, které mohou být spotřebovány aplikacemi, které jsou napsané v libovolném jazyce. Můžete také vytvořit jednu komponentu nebo aplikaci ze zdrojového kódu napsaného v několika jazycích. viz [interoperabilita mezi jazyky](#CrossLang) v druhé části tohoto článku.

Aby bylo možné plně spolupracovat s jinými objekty napsanými v libovolném jazyce, musí tyto objekty zveřejnit volajícím pouze ty funkce, které jsou společné pro všechny jazyky. Tato společná sada funkcí je definována specifikací CLS (Common Language Specification), což je sada pravidel, která se vztahují na generovaná sestavení. Specifikace CLS (Common Language Specification) je definována v oddílu I klauzule 7 až 11 ze [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Pokud vaše komponenta odpovídá specifikaci CLS (Common Language Specification), je zaručena, že je kompatibilní se specifikací CLS a je možné k nim přicházet z kódu v sestaveních napsaných v jakémkoli programovacím jazyce, který podporuje specifikaci CLS. Můžete určit, zda vaše komponenta odpovídá specifikaci CLS (Common Language Specification) v době kompilace, použitím atributu <xref:System.CLSCompliantAttribute> pro váš zdrojový kód. Další informace najdete v [atributu CLSCompliantAttribute](#CLSAttribute).

V tomto článku:

- [Pravidla dodržování předpisů CLS](#Rules)

  - [Typy a signatury členů typu](#Types)

  - [Zásady vytváření názvů](#naming)

  - [Převod typu](#conversion)

  - [Pole](#arrays)

  - [Rozhraní](#Interfaces)

  - [Výčty](#enums)

  - [Obecné typy členů](#members)

  - [Přístupnost člena](#MemberAccess)

  - [Obecné typy a členy](#Generics)

  - [Konstruktory](#ctors)

  - [Vlastnosti](#properties)

  - [Události](#events)

  - [Overloads](#overloads)

  - [Výjimky](#exceptions)

  - [Atributy](#attributes)

- [Atribut CLSCompliantAttribute](#CLSAttribute)

- [Vzájemná funkční spolupráce mezi jazyky](#CrossLang)

<a name="Rules"></a>

## <a name="cls-compliance-rules"></a>Pravidla dodržování předpisů CLS

Tato část popisuje pravidla pro vytvoření komponenty kompatibilní se specifikací CLS. Úplný seznam pravidel naleznete v oddílu I klauzule 11 ve [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Specifikace CLS (Common Language Specification) se zabývá všemi pravidly dodržování specifikace CLS, protože se vztahuje na příjemce (vývojáři, kteří mají programově přístup k komponentě, která je kompatibilní se specifikací CLS), architektury (vývojáři, kteří používají kompilátor jazyka k vytvoření Knihovny kompatibilní se specifikací CLS) a zařízení (vývojáři, kteří vytvářejí nástroj, jako je například kompilátor jazyka nebo analyzátor kódu, který vytváří komponenty kompatibilní se specifikací CLS). Tento článek se zaměřuje na pravidla, která se vztahují na rozhraní. Všimněte si ale, že některá pravidla, která platí pro rozšířené, mohou platit také pro sestavení, která jsou vytvořena pomocí reflexe. Emit.

Chcete-li navrhnout komponentu, která je nezávislá na jazyce, stačí použít pravidla pro dodržování specifikace CLS pro veřejné rozhraní vaší komponenty. Vaše soukromá implementace nemusí odpovídat specifikaci.

> [!IMPORTANT]
> Pravidla pro dodržování předpisů CLS platí pouze pro veřejné rozhraní komponenty, nikoli na jeho soukromou implementaci.

Například celá čísla bez znaménka jiná než <xref:System.Byte> nejsou kompatibilní se specifikací CLS. Vzhledem k tomu, že třída `Person` v následujícím příkladu zpřístupňuje vlastnost `Age` typu <xref:System.UInt16>, následující kód zobrazí upozornění kompilátoru.

[!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
[!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]

Třídu `Person` kompatibilní se specifikací CLS můžete nastavit tak, že změníte typ `Age` vlastnosti z <xref:System.UInt16> na <xref:System.Int16>, což je 16bitové podepsané celé číslo kompatibilní se specifikací CLS. Nemusíte měnit typ pole private `personAge`.

[!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
[!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]

Veřejné rozhraní knihovny se skládá z následujících:

- Definice veřejných tříd.

- Definice veřejných členů veřejných tříd a definice členů přístupných k odvozeným třídám (tj. chráněným členům).

- Parametry a návratové typy veřejných tříd a parametry a návratové typy metod, které jsou přístupné pro odvozené třídy.

Pravidla pro dodržování specifikace CLS jsou uvedená v následující tabulce. Text pravidel se bere v platnost od [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), což je Copyright 2012 podle Ecma International. Podrobnější informace o těchto pravidlech najdete v následujících oddílech.

|Kategorie|Další informace naleznete v tématu|Pravidlo|Číslo pravidla|
|--------------|---------|----------|-----------------|
|Usnadnění|[Přístupnost člena](#MemberAccess)|Při přepisu zděděných metod se přístupnost nemění, s výjimkou přepsání metody zděděné z jiného sestavení s přístupností `family-or-assembly`. V takovém případě má přepsání přístup `family`.|10pruhový|
|Usnadnění|[Přístupnost člena](#MemberAccess)|Viditelnost a přístupnost typů a členů musí být takové, aby typy v signatuře kteréhokoli člena byly viditelné a přístupné, kdykoli je samotný člen viditelný a přístupný. Například veřejná metoda, která je viditelná vně sestavení, nesmí obsahovat argument, jehož typ je viditelný pouze v rámci sestavení. Viditelnost a přístupnost typů tvořících instanci obecného typu používaného v podpisu každého člena musí být viditelná a přístupná, kdykoli je samotný člen viditelný a přístupný. Například instance obecného typu přítomná v signatuře člena, který je viditelný mimo jeho sestavení, nesmí mít obecný argument, jehož typ je viditelný pouze v rámci sestavení.|12,5|
|Pole|[Pole](#arrays)|Pole musí mít prvky s typem odpovídajícím specifikaci CLS a všechny dimenze pole musí mít nižší meze nula. Pouze skutečnost, že položka je pole a typ elementu pole musí být požadován pro rozlišení mezi přetíženími. Pokud je přetížení založeno na dvou nebo více typech pole, musí být typy prvků pojmenované typy.|16bitovém|
|Atributy|[Atributy](#attributes)|Atributy musí být typu <xref:System.Attribute?displayProperty=nameWithType>nebo typu, který z něj dědí.|41|
|Atributy|[Atributy](#attributes)|Specifikace CLS umožňuje pouze podmnožinu kódování pro vlastní atributy. Jediné typy, které se zobrazí v těchto kódováních jsou (viz oddíl IV): <xref:System.Type?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Byte?displayProperty=nameWithType>, <xref:System.Int16?displayProperty=nameWithType>, <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.Single?displayProperty=nameWithType>, <xref:System.Double?displayProperty=nameWithType>a jakýkoli typ výčtu založený na typu základního typu Integer kompatibilní se specifikací CLS.|34|
|Atributy|[Atributy](#attributes)|Specifikace CLS neumožňuje veřejně viditelné požadované modifikátory (`modreq`, viz oddíl II), ale umožňuje volitelné modifikátory (`modopt`, viz oddíl II), které nerozumí.|35|
|Konstruktory|[Konstruktory](#ctors)|Konstruktor objektu musí volat konstruktor instance své základní třídy před jakýmkoli přístupem k zděděným datům instance. (To se nevztahuje na typy hodnot, které nemusí mít konstruktory.)|20|
|Konstruktory|[Konstruktory](#ctors)|Konstruktor objektu se nesmí volat kromě v rámci vytváření objektu a objekt se nemůže inicializovat dvakrát.|22|
|Výčty|[Výčty](#enums)|Nadřazený typ výčtu musí být vestavěný celočíselný typ CLS, název pole musí být "value__" a toto pole musí být označeno jako `RTSpecialName`.|čl|
|Výčty|[Výčty](#enums)|Existují dva různé druhy výčtů, které jsou označeny přítomností nebo absence <xref:System.FlagsAttribute?displayProperty=nameWithType> (viz oddíl IV knihovna) vlastní atribut. Jedna představuje pojmenované celočíselné hodnoty; druhý představuje pojmenované bitové příznaky, které lze kombinovat pro vygenerování nepojmenované hodnoty. Hodnota `enum` není omezena na zadané hodnoty.|8|
|Výčty|[Výčty](#enums)|Literální statická pole výčtového typu musí mít typ samotného výčtu.|9|
|Události|[Události](#events)|Metody, které implementují událost, musí být označené `SpecialName` v metadatech.|29|
|Události|[Události](#events)|Přístupnost události a jejích přistupujících objektů se musí shodovat.|30|
|Události|[Události](#events)|Metody `add` a `remove` události musí být buď přítomny, nebo chybět.|čl|
|Události|[Události](#events)|Metody `add` a `remove` pro událost musí mít jeden parametr, jehož typ Určuje typ události a který musí být odvozen od <xref:System.Delegate?displayProperty=nameWithType>.|32|
|Události|[Události](#events)|Události musí dodržovat konkrétní vzor pojmenování. Atribut `SpecialName`, na který odkazuje pravidlo specifikace CLS 29, se ignoruje v odpovídajících porovnáních názvů a musí splňovat pravidla identifikátorů.|33|
|Výjimky|[Výjimky](#exceptions)|Objekty, které jsou vyvolány, musí být typu <xref:System.Exception?displayProperty=nameWithType> nebo typu, který z něj dědí. Nicméně metody kompatibilní se specifikací CLS nejsou požadovány pro blokování šíření jiných typů výjimek.|40|
|Obecné|[Kompatibilita se specifikací CLS: pravidla](#Rules)|Pravidla CLS se vztahují pouze na ty části typu, které jsou přístupné nebo viditelné mimo definiční sestavení.|první|
|Obecné|[Kompatibilita se specifikací CLS: pravidla](#Rules)|Členy typů, které nejsou kompatibilní se specifikací CLS, nesmí být označeny jako kompatibilní se specifikací CLS.|odst|
|Obecné typy|[Obecné typy a členy](#Generics)|Vnořené typy musí mít alespoň tolik obecných parametrů jako nadřazený typ. Obecné parametry ve vnořeném typu odpovídají umístění obecným parametrům v nadřazeném typu.|42|
|Obecné typy|[Obecné typy a členy](#Generics)|Název obecného typu musí kódovat počet parametrů typu deklarovaných pro nevnořený typ, nebo nově zavedený na typ, pokud je vnořený, podle pravidel definovaných výše.|43|
|Obecné typy|[Obecné typy a členy](#Generics)|Obecný typ musí znovu deklarovat dostatečná omezení, aby bylo zaručeno, že jakákoli omezení základního typu nebo rozhraní budou splněna omezeními obecného typu.|4444|
|Obecné typy|[Obecné typy a členy](#Generics)|Typy, které se používají jako omezení u obecných parametrů, samy o nich vyhovují specifikaci CLS.|45|
|Obecné typy|[Obecné typy a členy](#Generics)|Viditelnost a přístupnost členů (včetně vnořených typů) v instanci generického typu se považují za obor pro konkrétní instanci, nikoli jako deklaraci obecného typu jako celku. Za předpokladu, že pravidla viditelnosti a přístupnosti pravidla CLS 12 budou nadále platit.|46|
|Obecné typy|[Obecné typy a členy](#Generics)|Pro každou abstraktní nebo virtuální obecnou metodu musí být použita výchozí konkrétní (neabstraktní) implementace.|47|
|Rozhraní|[Rozhraní](#Interfaces)|Rozhraní kompatibilní se specifikací CLS nesmí vyžadovat definici metod nekompatibilních se specifikací CLS, aby je bylo možné implementovat.|let|
|Rozhraní|[Rozhraní](#Interfaces)|Rozhraní kompatibilní se specifikací CLS nesmějí definovat statické metody ani definovat pole.|čl|
|Členové|[Obecné typy členů](#members)|Globální statická pole a metody nejsou kompatibilní se specifikací CLS.|36|
|Členové|--|Hodnota statického literálu je určena pomocí inicializačních metadat pole. Literál kompatibilní se specifikací CLS musí mít zadanou hodnotu v metadatech inicializace pole, která je přesně stejného typu jako literál (nebo základního typu, pokud je tento literál `enum`).|13,5|
|Členové|[Obecné typy členů](#members)|Omezení vararg není součástí specifikace CLS a jediná konvence volání podporovaná specifikací CLS je standardní spravovaná konvence volání.|15|
|Zásady vytváření názvů|[Zásady vytváření názvů](#naming)|Sestavení se řídí podle přílohy 7 technické sestavy 15 sady Unicode Standard 3.0, která se řídí sadou znaků povolených ke spuštění, a jejich zahrnutí do identifikátorů, které jsou k dispozici online na <https://www.unicode.org/unicode/reports/tr15/tr15-18.html>. Identifikátory musí být v kanonickém formátu definovaném formulářem normalizace Unicode C. Pro účely specifikace CLS jsou dva identifikátory stejné, pokud mapování malých písmen (podle specifikace národního prostředí Unicode rozlišuje malá a velká písmena), jsou stejná. To znamená, že u dvou identifikátorů, které se považují za odlišné v rámci specifikace CLS, se liší ve více než pouhém případě. Chcete-li však přepsat zděděnou definici, rozhraní příkazového řádku vyžaduje použití přesného kódování původní deklarace.|4|
|Přetížení|[Zásady vytváření názvů](#naming)|Všechny názvy zavedené v oboru kompatibilním se specifikací CLS musí být nezávislé na druhu, s výjimkou případů, kdy jsou názvy identické a vyřešeny pomocí přetížení. To znamená, že zatímco CTSallows jeden typ pro použití stejného názvu pro metodu a pole, specifikace CLS nikoli.|5|
|Přetížení|[Zásady vytváření názvů](#naming)|Pole a vnořené typy se liší podle porovnání identifikátorů, i když CTS umožňuje odlišit jedinečné podpisy. Metody, vlastnosti a události, které mají stejný název (podle porovnání identifikátorů), se liší o více než pouze návratovým typem, s výjimkou zadání v pravidle specifikace CLS 39.|6|
|Přetížení|[Overloads](#overloads)|Pouze vlastnosti a metody mohou být přetíženy.|37|
|Přetížení|[Overloads](#overloads)|Vlastnosti a metody mohou být přetíženy pouze na základě počtu a typů parametrů, s výjimkou operátorů převodu s názvem `op_Implicit` a `op_Explicit`, které mohou být také přetíženy na základě jejich návratového typu.|38|
|Přetížení|--|Pokud dva nebo více metod odpovídajících specifikaci CLS mají stejný název a pro konkrétní sadu instancí typu, mají stejný parametr a návratové typy, pak všechny tyto metody musí být sémanticky rovnocenné v těchto instancích typu.|48|
|Typy|[Typ a signatury členů typu](#Types)|<xref:System.Object?displayProperty=nameWithType> je kompatibilní se specifikací CLS. Všechny ostatní třídy odpovídající specifikaci CLS dědí z třídy kompatibilní se specifikací CLS.|listopadu|
|Vlastnosti|[Vlastnosti](#properties)|Metody, které implementují metody getter a setter vlastnosti, musí být označeny `SpecialName` v metadatech.|24|
|Vlastnosti|[Vlastnosti](#properties)|Přistupující objekty vlastnosti musí být všechny statické, všechny virtuální nebo všechny instance.|26|
|Vlastnosti|[Vlastnosti](#properties)|Typ vlastnosti musí být návratový typ getter a typ posledního argumentu setter. Typy parametrů vlastnosti musí být typy parametrů pro metodu getter a typy všech, ale konečný parametr metody setter. Všechny tyto typy musí být kompatibilní se specifikací CLS a nesmí být spravované ukazatele (tj. nesmí být předány odkazem).|dlouhý|
|Vlastnosti|[Vlastnosti](#properties)|Vlastnosti musí splňovat konkrétní vzor pojmenování. Atribut `SpecialName`, na který se odkazuje v pravidle CLS 24, se ignoruje v odpovídajících porovnáních názvů a musí splňovat pravidla identifikátoru. Vlastnost musí mít metodu getter, metodu setter nebo obojí.|28|
|Převod typu|[Převod typu](#conversion)|Pokud je k dispozici buď `op_Implicit`, nebo `op_Explicit`, je k dispozici alternativní způsob poskytnutí tohoto vynucení.|39|
|Typy|[Typ a signatury členů typu](#Types)|Typy zabalené hodnoty nejsou kompatibilní se specifikací CLS.|3|
|Typy|[Typ a signatury členů typu](#Types)|Všechny typy, které se zobrazují v signatuře, musí být kompatibilní se specifikací CLS. Všechny typy tvořící vytvořená instance obecného typu musí být kompatibilní se specifikací CLS.|odst|
|Typy|[Typ a signatury členů typu](#Types)|Typové odkazy nejsou kompatibilní se specifikací CLS.|čtrnáct|
|Typy|[Typ a signatury členů typu](#Types)|Nespravované typy ukazatelů nejsou kompatibilní se specifikací CLS.|sedmnáct|
|Typy|[Typ a signatury členů typu](#Types)|Třídy kompatibilní se specifikací CLS, typy hodnot a rozhraní nevyžadují implementaci členů neodpovídajících specifikaci CLS.|20o|

<a name="Types"></a>

### <a name="types-and-type-member-signatures"></a>Typy a signatury členů typu

Typ <xref:System.Object?displayProperty=nameWithType> je kompatibilní se specifikací CLS a je základní typ všech typů objektů v systému .NET Framework typů. Dědičnost v .NET Framework je buď implicitní (například třída <xref:System.String> implicitně dědí z třídy <xref:System.Object>) nebo explicitní (například třída <xref:System.Globalization.CultureNotFoundException> explicitně dědí z třídy <xref:System.ArgumentException>, která explicitně dědí z <xref:System.SystemException> třída, která explicitně dědí z <xref:System.Exception> třídy). Aby byl odvozený typ kompatibilní se specifikací CLS, musí být jeho základní typ také kompatibilní se specifikací CLS.

Následující příklad ukazuje odvozený typ, jehož základní typ není kompatibilní se specifikací CLS. Definuje základní třídu `Counter`, která jako čítač používá celé číslo bez znaménka 32-bit. Vzhledem k tomu, že třída poskytuje funkce čítače tím, že zabalí unsigned integer, třída je označena jako nekompatibilní se specifikací CLS. V důsledku toho odvozená třída, `NonZeroCounter`, není kompatibilní se specifikací CLS.

[!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
[!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]

Všechny typy, které se zobrazují v podpisech členů, včetně návratového typu metody nebo typu vlastnosti, musí být kompatibilní se specifikací CLS. Kromě toho pro obecné typy:

- Všechny typy, které tvoří obecný typ s instancemi, musí být kompatibilní se specifikací CLS.

- Všechny typy použité jako omezení u obecných parametrů musí být kompatibilní se specifikací CLS.

.NET Framework [běžný typ systému](../../docs/standard/base-types/common-type-system.md) obsahuje řadu předdefinovaných typů, které jsou podporovány přímo modulem CLR (Common Language Runtime) a jsou speciálně kódovány v metadatech sestavení. Z těchto vnitřních typů jsou typy uvedené v následující tabulce kompatibilní se specifikací CLS.

|Typ kompatibilní se specifikací CLS|Popis|
|-------------------------|-----------------|
|<xref:System.Byte>|8 bitů unsigned integer|
|<xref:System.Int16>|16bitové celé číslo se znaménkem|
|<xref:System.Int32>|32 – celé číslo se znaménkem|
|<xref:System.Int64>|64 – celé číslo se znaménkem|
|<xref:System.Single>|Hodnota s plovoucí desetinnou čárkou s jednoduchou přesností|
|<xref:System.Double>|Hodnota s plovoucí desetinnou čárkou s dvojitou přesností|
|<xref:System.Boolean>|Typ hodnoty `true` nebo `false`|
|<xref:System.Char>|Jednotka kódovaného kódu UTF-16|
|<xref:System.Decimal>|Desítkové číslo jiné než plovoucí desetinné čárky|
|<xref:System.IntPtr>|Ukazatel nebo popisovač velikosti platformy definované platformou|
|<xref:System.String>|Kolekce nula, jedna nebo více <xref:System.Char> objektů|

Vnitřní typy uvedené v následující tabulce nejsou kompatibilní se specifikací CLS.

|Neodpovídající typ|Popis|Alternativa odpovídající specifikaci CLS|
|-------------------------|-----------------|--------------------------------|
|<xref:System.SByte>|8bitový datový typ se znaménkem na 8bitové číslo|<xref:System.Int16>|
|<xref:System.TypedReference>|Ukazatel na objekt a jeho typ modulu runtime|Žádné|
|<xref:System.UInt16>|16bitové unsigned integer|<xref:System.Int32>|
|<xref:System.UInt32>|32 – bitová unsigned integer|<xref:System.Int64>|
|<xref:System.UInt64>|64 – bitová unsigned integer|<xref:System.Int64> (může přetečení), <xref:System.Numerics.BigInteger>nebo <xref:System.Double>|
|<xref:System.UIntPtr>|Nepodepsaný ukazatel nebo popisovač|<xref:System.IntPtr>|

Knihovna tříd .NET Framework nebo jiná knihovna tříd může obsahovat jiné typy, které nejsou kompatibilní se specifikací CLS; například:

- Zabalené typy hodnot. Následující C# příklad vytvoří třídu, která má veřejnou vlastnost typu `int*` s názvem `Value`. Vzhledem k tomu, že `int*` je zabalený typ hodnoty, kompilátor jej označí jako nekompatibilní se specifikací CLS.

  [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]

- Typové odkazy, což jsou speciální konstrukce, které obsahují odkaz na objekt a odkaz na typ. Typové odkazy jsou reprezentovány v .NET Framework třídou <xref:System.TypedReference>.

Pokud typ není kompatibilní se specifikací CLS, měli byste použít atribut <xref:System.CLSCompliantAttribute> s hodnotou `isCompliant` `false` na ni. Další informace najdete v části [atributu CLSCompliantAttribute](#CLSAttribute) .

Následující příklad ilustruje problém dodržování specifikace CLS v signatuře metody a při vytváření instancí obecného typu. Definuje třídu `InvoiceItem` s vlastností typu <xref:System.UInt32>, vlastností typu `Nullable(Of UInt32)`a konstruktor s parametry typu <xref:System.UInt32> a `Nullable(Of UInt32)`. Při pokusu o zkompilování tohoto příkladu získáte čtyři upozornění kompilátoru.

[!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
[!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]

Chcete-li odstranit upozornění kompilátoru, nahraďte typy neodpovídající specifikaci CLS ve `InvoiceItem` veřejném rozhraní s vyhovujícími typy:

[!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
[!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]

Kromě specifických typů uvedených v některé kategorie typů nejsou kompatibilní se specifikací CLS. Mezi ně patří nespravované typy ukazatelů a typy ukazatelů na funkce. Následující příklad vygeneruje upozornění kompilátoru, protože používá ukazatel na celé číslo pro vytvoření pole celých čísel.

[!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]

Pro abstraktní třídy kompatibilní se specifikací CLS (to znamená, třídy označené jako `abstract` C# v nebo jako `MustInherit` v Visual Basic) musí být všichni členové třídy také kompatibilní se specifikací CLS.

<a name="naming"></a>

### <a name="naming-conventions"></a>Zásady vytváření názvů

Vzhledem k tomu, že některé programovací jazyky rozlišují velká a malá písmena, se musí identifikátory (například názvy oborů názvů, typů a členů) lišit o více než případu. Dva identifikátory jsou považovány za ekvivalentní, pokud je jejich mapování malých písmen stejné. Následující C# příklad definuje dvě veřejné třídy `Person` a `person`. Protože se liší pouze v případě, C# kompilátor je označí jako nekompatibilní se specifikací CLS.

[!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]

Identifikátory programovacích jazyků, jako jsou názvy oborů názvů, typů a členů, musí být v souladu se [standardem Unicode 3,0, technickým hlášením 15, přílohou 7](https://www.unicode.org/reports/tr15/tr15-18.html). To znamená, že:

- Prvním znakem identifikátoru může být jakékoli velké písmeno Unicode, malé písmeno, název písmene, písmeno, písmeno, jiné písmeno nebo číslo písmen. Informace o kategoriích znaků Unicode naleznete v <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> výčtu.

- Další znaky mohou být z libovolné kategorie jako první znak a mohou také obsahovat značky bez mezer mezi mezerami, kombinováním značek mezer, desetinnými čísly, interpunkční znaménky konektoru a formátovacími kódy.

Před porovnáním identifikátorů byste měli odfiltrovat Formátovací kódy a převést identifikátory na normalizační formu Unicode C, protože jeden znak může být reprezentován více jednotkami kódu zakódovanými v kódování UTF-16. Sekvence znaků, které vytvářejí stejné jednotky kódu ve formě normalizace Unicode C, nejsou kompatibilní se specifikací CLS. Následující příklad definuje vlastnost s názvem `Å`, která se skládá z znaku ANGSTROM SIGN (U + 212B), a druhé vlastnosti s názvem `Å`, která se skládá z znaku velké písmeno latinky A s výše UVEDENým PRSTENci (U + 00C5). Kompilátory C# i Visual Basic označí zdrojový kód jako nekompatibilní se specifikací CLS.

[!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
[!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]

Názvy členů v rámci určitého oboru (například obory názvů v rámci sestavení, typy v rámci oboru názvů nebo členy v rámci typu) musí být jedinečné s výjimkou názvů, které jsou přeloženy prostřednictvím přetížení. Tento požadavek je přísnější než u společného systému typů, což umožňuje více členům v rámci oboru mít stejné názvy, pokud jsou různé druhy členů (například jedna je metoda a jedna je pole). Konkrétně pro členy typu:

- Pole a vnořené typy jsou rozlišeny pouze podle názvu.

- Metody, vlastnosti a události, které mají stejný název, se musí lišit více než pouhým návratovým typem.

Následující příklad znázorňuje požadavek, aby názvy členů musely být v rámci svého oboru jedinečné. Definuje třídu s názvem `Converter`, která obsahuje čtyři členy s názvem `Conversion`. Tři jsou metody a jedna je vlastnost. Metoda, která obsahuje parametr <xref:System.Int64>, je jednoznačně pojmenována, ale tyto dvě metody s parametrem <xref:System.Int32> nejsou, protože návratová hodnota není považována za součást signatury člena. Vlastnost `Conversion` také porušuje tento požadavek, protože vlastnosti nemohou mít stejný název jako přetížené metody.

[!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
[!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]

Jednotlivé jazyky obsahují jedinečná klíčová slova, takže jazyky, které cílí na modul CLR (Common Language Runtime), musí také poskytovat určitý mechanismus pro odkazování na identifikátory (například názvy typů), které se shodují s klíčovými slovy. Například `case` je klíčové slovo v obou C# i Visual Basic. Následující příklad Visual Basic například umožňuje určit třídu s názvem `case` z klíčového slova `case` pomocí počátečních a uzavíracích složených závorek. V opačném případě by tento příklad vytvořil chybovou zprávu "klíčové slovo není platné jako identifikátor" a kompilace se nezdařila.

[!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]

V následujícím C# příkladu je možné vytvořit instanci `case` třídy pomocí symbolu `@` pro odstranění identifikátoru z klíčového slova jazyka. Bez něj C# kompilátor zobrazí dvě chybové zprávy, "očekával se typ" a "neplatný výraz" Case ".

[!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]

<a name="conversion"></a>

### <a name="type-conversion"></a>Převod typu

Specifikace CLS (Common Language Specification) definuje dva operátory převodu:

- `op_Implicit`, která se používá pro rozšiřující převody, které nemají za následek ztrátu dat nebo přesnost. Například struktura <xref:System.Decimal> obsahuje přetížený `op_Implicit` operátor pro převod hodnot integrálních typů a <xref:System.Char> hodnot na hodnoty <xref:System.Decimal>.

- `op_Explicit`, která se používá pro zúžené převody, které mohou vést ke ztrátě velikosti (hodnota je převedena na hodnotu, která má menší rozsah) nebo přesnost. Například struktura <xref:System.Decimal> obsahuje přetížený `op_Explicit` operátor k převedení <xref:System.Double> a <xref:System.Single> hodnot na <xref:System.Decimal> a k převodu <xref:System.Decimal> hodnot na integrální hodnoty, <xref:System.Double>, <xref:System.Single>a <xref:System.Char>.

Ne všechny jazyky ale podporují přetížení operátoru nebo definici vlastních operátorů. Pokud se rozhodnete implementovat tyto operátory převodu, měli byste také poskytnout alternativní způsob, jak provést převod. Doporučujeme zadat `From`*xxx* a `To`*xxx* metody.

Následující příklad definuje implicitní a explicitní převody kompatibilní se specifikací CLS. Vytvoří třídu `UDouble`, která představuje podepsané číslo s dvojitou přesností a plovoucí desetinnou čárkou. Poskytuje implicitní převody z `UDouble` na <xref:System.Double> a explicitní převod z `UDouble` na <xref:System.Single>, <xref:System.Double> na `UDouble`a <xref:System.Single> na `UDouble`. Také definuje metodu `ToDouble` jako alternativu implicitního operátoru převodu a metody `ToSingle`, `FromDouble`a `FromSingle` jako alternativy pro explicitní operátory převodu.

[!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
[!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]

<a name="arrays"></a>

### <a name="arrays"></a>Pole

Pole kompatibilní se specifikací CLS odpovídají následujícím pravidlům:

- Všechny dimenze pole musí mít dolní mez nula. Následující příklad vytvoří pole, které není kompatibilní se specifikací CLS, s dolní mezí jedna. Všimněte si, že navzdory přítomnosti atributu <xref:System.CLSCompliantAttribute> kompilátor nezjistí, že pole vrácené metodou `Numbers.GetTenPrimes` není kompatibilní se specifikací CLS.

  [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
  [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]

- Všechny prvky pole musí obsahovat typy kompatibilní se specifikací CLS. Následující příklad definuje dvě metody, které vracejí pole neodpovídající specifikaci CLS. První vrátí pole hodnot <xref:System.UInt32>. Druhá vrátí <xref:System.Object> pole, které obsahuje hodnoty <xref:System.Int32> a <xref:System.UInt32>. I když kompilátor identifikuje první pole jako nevyhovující z důvodu jeho <xref:System.UInt32>ho typu, nerozpozná, že druhé pole obsahuje prvky, které nejsou kompatibilní se specifikací CLS.

  [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
  [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]

- Rozlišení přetěžování pro metody, které mají parametry pole, je založené na tom, že se jedná o pole a na jejich typu prvku. Z tohoto důvodu je následující definice přetížené metody `GetSquares` kompatibilní se specifikací CLS.

  [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
  [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]

<a name="Interfaces"></a>

### <a name="interfaces"></a>Rozhraní

Rozhraní kompatibilní se specifikací CLS mohou definovat vlastnosti, události a virtuální metody (metody bez implementace). Rozhraní kompatibilní se specifikací CLS nemůže mít následující:

- Statické metody nebo statická pole. Kompilátory C# i Visual Basic generují chyby kompilátoru, pokud definujete statického člena v rozhraní.

- Pole. Kompilátory C# i Visual Basic generují chyby kompilátoru, pokud definujete pole v rozhraní.

- Metody, které nejsou kompatibilní se specifikací CLS. Například následující definice rozhraní zahrnuje metodu, `INumber.GetUnsigned`, která je označena jako nekompatibilní se specifikací CLS. Tento příklad generuje upozornění kompilátoru.

  [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
  [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]

  Vzhledem k tomuto pravidlu nejsou typy kompatibilní se specifikací CLS vyžadovány k implementaci členů, které nedodržují specifikaci CLS. Pokud rozhraní kompatibilní se specifikací CLS zveřejňuje třídu, která implementuje rozhraní nekompatibilní se specifikací CLS, měla by také poskytnout konkrétní implementace všech členů nekompatibilních se specifikací CLS.

Kompilátory jazyka odpovídající specifikaci CLS musí také umožňovat třídě, aby poskytovala samostatné implementace členů, kteří mají stejný název a signaturu ve více rozhraních.  C# A Visual Basic podporují [explicitní implementace rozhraní](../csharp/programming-guide/interfaces/explicit-interface-implementation.md) , které poskytují různé implementace identicky pojmenovaných metod. Visual Basic také podporuje klíčové slovo `Implements`, které umožňuje explicitně určit, které rozhraní a člen určitý člen implementuje. Následující příklad znázorňuje tento scénář definováním `Temperature` třídy, která implementuje rozhraní `ICelsius` a `IFahrenheit` jako explicitní implementace rozhraní.

[!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
[!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]

<a name="enums"></a>

### <a name="enumerations"></a>Výčty

Výčty kompatibilní se specifikací CLS musí dodržovat tato pravidla:

- Podkladový typ výčtu musí být vnitřní celé číslo kompatibilní se specifikací CLS (<xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>nebo <xref:System.Int64>). Například následující kód se pokusí definovat výčet, jehož základní typ je <xref:System.UInt32> a vygeneruje upozornění kompilátoru.

  [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
  [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]

- Typ výčtu musí mít jedno pole instance s názvem `Value__`, které je označeno atributem <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType>. To umožňuje implicitně odkazovat na hodnotu pole.

- Výčet zahrnuje statická pole literálů, jejichž typy se shodují s typem výčtu samotného. Například pokud definujete `State` výčtu s hodnotami `State.On` a `State.Off`, `State.On` a `State.Off` jsou obě literální statická pole, jejichž typ je `State`.

- Existují dva druhy výčtů:

  - Výčet, který představuje sadu vzájemně se vylučujících pojmenovaných celočíselných hodnot. Tento typ výčtu je označen nepřítomností vlastního atributu <xref:System.FlagsAttribute?displayProperty=nameWithType>.

  - Výčet, který představuje sadu bitových příznaků, které lze kombinovat k vygenerování nepojmenované hodnoty. Tento typ výčtu je označen přítomností vlastního atributu <xref:System.FlagsAttribute?displayProperty=nameWithType>.

  Další informace najdete v dokumentaci ke struktuře <xref:System.Enum>.

- Hodnota výčtu není omezena na rozsah zadaných hodnot. Jinými slovy rozsah hodnot ve výčtu je rozsah své základní hodnoty. K určení, zda je zadaná hodnota členem výčtu, lze použít metodu <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType>.

<a name="members"></a>

### <a name="type-members-in-general"></a>Obecné typy členů

Specifikace CLS (Common Language Specification) vyžaduje, aby všechna pole a metody byly dostupné jako členové konkrétní třídy. Proto globální statická pole a metody (tj. statická pole nebo metody, které jsou definovány odděleně od typu) nejsou kompatibilní se specifikací CLS. Pokud se pokusíte zahrnout globální pole nebo metodu do zdrojového kódu, kompilátory C# a Visual Basic generují chybu kompilátoru.

Specifikace CLS (Common Language Specification) podporuje pouze standardní spravovanou konvenci volání. Nepodporuje konvence nespravovaného volání a metody se seznamy argumentů proměnných označenými klíčovým slovem `varargs`. U seznamů argumentů proměnných, které jsou kompatibilní se standardní spravovanou konvencí volání, použijte atribut <xref:System.ParamArrayAttribute> nebo implementaci jednotlivého jazyka, například klíčové slovo `params` v C# a klíčová slova `ParamArray` v Visual Basic.

<a name="MemberAccess"></a>

### <a name="member-accessibility"></a>Přístupnost člena

Přepsání zděděného člena nemůže změnit přístupnost daného člena. Například veřejná metoda v základní třídě nemůže být přepsána soukromou metodou v odvozené třídě. Existuje jedna výjimka: člen `protected internal` (in C#) nebo `Protected Friend` (v Visual Basic) v jednom sestavení, který je přepsán typem v jiném sestavení. V takovém případě je přístup k přepsání `Protected`.

Následující příklad ilustruje chybu, která je generována, když je atribut <xref:System.CLSCompliantAttribute> nastaven na hodnotu `true`a `Human`, což je třída odvozená od `Animal`, se pokusí změnit přístupnost vlastnosti `Species` z veřejného na Private. Příklad se úspěšně zkompiluje, pokud je jeho přístupnost změněno na veřejné.

[!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
[!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]

Typy v signatuře člena musí být přístupné, kdykoli je tento člen přístupný. Například to znamená, že veřejný člen nemůže obsahovat parametr, jehož typ je Private, Protected nebo Internal. Následující příklad ukazuje chybu kompilátoru, která je výsledkem, když konstruktor třídy `StringWrapper` zpřístupňuje interní hodnotu výčtu `StringOperationType`, která určuje, jak má být hodnota řetězce zabalena.

[!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
[!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]

<a name="Generics"></a>

### <a name="generic-types-and-members"></a>Obecné typy a členy

Vnořené typy mají vždy alespoň tolik obecných parametrů jako jejich nadřazený typ. Odpovídají umístění obecným parametrům v nadřazeném typu. Obecný typ může obsahovat také nové obecné parametry.

Vztah mezi parametry obecného typu obsahujícího typu a jeho vnořenými typy mohou být skryty syntaxí jednotlivých jazyků. V následujícím příkladu je obecný typ `Outer<T>` obsahuje dvě vnořené třídy, `Inner1A` a `Inner1B<U>`. Volání metody `ToString`, kterou jednotlivé třídy dědí z <xref:System.Object.ToString%2A?displayProperty=nameWithType>, ukazují, že každá vnořená třída obsahuje parametry typu své nadřazené třídy.

[!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
[!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]

Názvy obecných typů jsou kódovány v *názvu formuláře\`n*, kde *název* je název typu, \` je znakový literál a *n* je počet parametrů deklarovaných u typu, nebo pro vnořené obecné typy počet nově zavedených parametry typu. Toto kódování názvů obecného typu je primárně v zájmu vývojářů, kteří používají reflexi pro přístup k obecným typům specifikace CLS v knihovně.

Pokud jsou omezení aplikována na obecný typ, všechny typy použité jako omezení musí být také kompatibilní se specifikací CLS. Následující příklad definuje třídu s názvem `BaseClass`, která není kompatibilní se specifikací CLS, a obecnou třídu s názvem `BaseCollection`, jejíž parametr typu musí být odvozen od `BaseClass`. Vzhledem k tomu, že `BaseClass` není kompatibilní se specifikací CLS, kompilátor vygeneruje upozornění.

[!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
[!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]

Je-li obecný typ odvozen od obecného základního typu, musí znovu deklarovat jakákoli omezení, aby bylo zaručeno, že jsou také splněna omezení základního typu. Následující příklad definuje `Number<T>`, který může představovat libovolný číselný typ. Definuje také třídu `FloatingPoint<T>`, která představuje hodnotu s plovoucí desetinnou čárkou. Zdrojový kód však nelze kompilovat, protože nepoužívá omezení pro `Number<T>` (Toto T musí být typ hodnoty) k `FloatingPoint<T>`.

[!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
[!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]

Příklad se úspěšně zkompiluje, pokud je omezení přidáno do třídy `FloatingPoint<T>`.

[!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
[!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]

Specifikace CLS (Common Language Specification) ukládá konzervativní model pro vytváření instancí pro vnořené typy a chráněné členy. Otevřené obecné typy nemohou vystavovat pole nebo členy s podpisy, které obsahují konkrétní instanci vnořeného, chráněného obecného typu. Neobecné typy, které rozšíří specifické instance obecné základní třídy nebo rozhraní, nemůžou vystavovat pole nebo členy s podpisy, které obsahují různé instance vnořeného, chráněného obecného typu.

Následující příklad definuje obecný typ, `C1<T>` (nebo `C1(Of T)` v Visual Basic) a chráněnou třídu `C1<T>.N` (nebo `C1(Of T).N` v Visual Basic). `C1<T>` má dvě metody, `M1` a `M2`. `M1` však není kompatibilní se specifikací CLS, protože se pokusí vrátit objekt `C1<int>.N` (nebo `C1(Of Integer).N`) z C1\<T > (nebo `C1(Of T)`). Druhá třída, `C2`, je odvozena od `C1<long>` (nebo `C1(Of Long)`). Má dvě metody `M3` a `M4`. `M3` není kompatibilní se specifikací CLS, protože se pokusí vrátit objekt `C1<int>.N` (nebo `C1(Of Integer).N`) z podtřídy `C1<long>`. Všimněte si, že kompilátory jazyka mohou být ještě více omezující. V tomto příkladu Visual Basic při pokusu o kompilaci `M4`zobrazit chybu.

[!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
[!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]

<a name="ctors"></a>

### <a name="constructors"></a>Konstruktory

Konstruktory v třídách a strukturách odpovídajících specifikaci CLS musí dodržovat tato pravidla:

- Konstruktor odvozené třídy musí volat konstruktor instance své základní třídy před tím, než přistupuje k zděděným datům instance. Tento požadavek je způsoben faktem, že konstruktory základní třídy nejsou děděny jejich odvozenými třídami. Toto pravidlo se nevztahuje na struktury, které nepodporují přímou dědičnost.

  Kompilátory obvykle toto pravidlo vynutil nezávisle na kompatibilitě se specifikací CLS, jak ukazuje následující příklad. Vytvoří třídu `Doctor`, která je odvozena od `Person` třídy, ale třída `Doctor` nemůže volat konstruktor třídy `Person` pro inicializaci zděděných polí instance.

  [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
  [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]

- Nelze volat konstruktor objektu s výjimkou vytvoření objektu. Kromě toho objekt nelze inicializovat dvakrát. Například to znamená, že metody <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> a deserializace, jako je <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> nesmí volat konstruktory.

<a name="properties"></a>

### <a name="properties"></a>Vlastnosti

Vlastnosti v typech odpovídajících specifikaci CLS musí dodržovat tato pravidla:

- Vlastnost musí mít metodu Setter, getter nebo obojí. V sestavení jsou implementovány jako speciální metody, což znamená, že se zobrazí jako samostatné metody (getter má název `get_`*PropertyName* a metoda setter je `set_`*PropertyName*) označena jako `SpecialName` v sestavení mezipaměť. Kompilátory C# a Visual Basic vysazují toto pravidlo automaticky, aniž by bylo nutné použít atribut <xref:System.CLSCompliantAttribute>.

- Typ vlastnosti je návratový typ vlastnosti getter a poslední argument metody setter. Tyto typy musí být kompatibilní se specifikací CLS a argumenty nelze přiřadit vlastnost odkazem (to znamená, že nemohou být spravovány ukazateli).

- Pokud má vlastnost metodu Getter i setter, musí obě být virtuální, obojí i obě instance. Kompilátory C# a Visual Basic automaticky vynutil toto pravidlo pomocí jejich syntaxe definice vlastností.

<a name="events"></a>

### <a name="events"></a>Události

Událost je definována podle jejího názvu a typu. Typ události je delegát, který se používá k označení události. Například událost <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> je typu <xref:System.ResolveEventHandler>. Kromě samotné události představují implementaci události tři metody s názvy založenými na názvu události a jsou v metadatech sestavení označeny jako `SpecialName`:

- Metoda pro přidání obslužné rutiny události s názvem `add_`*EventName*. Například metoda odběru události pro událost <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> má název `add_AssemblyResolve`.

- Metoda pro odebrání obslužné rutiny události s názvem `remove_`*EventName*. Například metoda odebrání pro událost <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> má název `remove_AssemblyResolve`.

- Metoda pro indikaci, že došlo k události s názvem `raise_`*EventName*.

> [!NOTE]
> Většina pravidel specifikace CLS (Common Language Specification) týkajících se událostí je implementována kompilátory jazyka a jsou transparentní pro vývojáře komponent.

Metody pro přidání, odebrání a vyvolání události musí mít stejnou přístupnost. Musí také být všechny statické, instance nebo virtuální. Metody pro přidání a odebrání události mají jeden parametr, jehož typ je typ delegáta události. Metody Add a Remove musí být buď přítomné, nebo obě chybět.

Následující příklad definuje třídu kompatibilní se specifikací CLS s názvem `Temperature`, která vyvolává událost `TemperatureChanged`, pokud se změna teploty mezi dvěma čteními rovná nebo překračuje prahovou hodnotu. Třída `Temperature` explicitně definuje metodu `raise_TemperatureChanged`, aby mohla selektivně provádět obslužné rutiny událostí.

[!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
[!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]

<a name="overloads"></a>

### <a name="overloads"></a>Přetížení

Specifikace CLS (Common Language Specification) ukládá následující požadavky na přetížené členy:

- Členy mohou být přetíženy na základě počtu parametrů a typu libovolného parametru. Konvence volání, návratový typ, vlastní modifikátory použité pro metodu nebo její parametr a zda jsou parametry předány hodnotou nebo odkazem, se nepovažují za rozdíl mezi přetíženími. Příklad naleznete v kódu pro požadavek, aby názvy musí být jedinečné v rámci oboru v části [konvence pojmenování](#naming) .

- Pouze vlastnosti a metody mohou být přetíženy. Pole a události nemohou být přetíženy.

- Obecné metody mohou být přetíženy na základě počtu jejich obecných parametrů.

> [!NOTE]
> Operátory `op_Explicit` a `op_Implicit` jsou výjimky na pravidlo, které návratová hodnota není považována za součást signatury metody pro řešení přetížení. Tyto dva operátory mohou být přetíženy v závislosti na jejich parametrech a jejich návratové hodnotě.

<a name="exceptions"></a>

### <a name="exceptions"></a>Výjimky

Objekty výjimky musí být odvozeny od <xref:System.Exception?displayProperty=nameWithType> nebo z jiného typu odvozeného z <xref:System.Exception?displayProperty=nameWithType>. Následující příklad ukazuje chybu kompilátoru, která je výsledkem, když je použita vlastní třída s názvem `ErrorClass` pro zpracování výjimek.

[!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
[!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]

Chcete-li tuto chybu opravit, třída `ErrorClass` musí dědit z <xref:System.Exception?displayProperty=nameWithType>. Kromě toho musí být přepsána vlastnost `Message`. Následující příklad opravuje tyto chyby k definování `ErrorClass` třídy, která je kompatibilní se specifikací CLS.

[!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
[!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]

<a name="attributes"></a>

### <a name="attributes"></a>Atributy

Sestavení rozhraní In.NET, vlastní atributy poskytují rozšiřitelný mechanismus pro ukládání vlastních atributů a načítání metadat o programovacích objektech, jako jsou sestavení, typy, členy a parametry metody. Vlastní atributy se musí odvozovat z <xref:System.Attribute?displayProperty=nameWithType> nebo z typu odvozeného z <xref:System.Attribute?displayProperty=nameWithType>.

V následujícím příkladu je toto pravidlo porušeno. Definuje třídu `NumericAttribute`, která není odvozena od <xref:System.Attribute?displayProperty=nameWithType>. Všimněte si, že chyba kompilátoru je výsledkem pouze v případě, že je použit atribut, který není kompatibilní se specifikací CLS, nikoli při definování třídy.

[!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
[!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]

Konstruktor nebo vlastnosti atributu kompatibilního se specifikací CLS mohou vystavovat pouze následující typy:

- <xref:System.Boolean>

- <xref:System.Byte>

- <xref:System.Char>

- <xref:System.Double>

- <xref:System.Int16>

- <xref:System.Int32>

- <xref:System.Int64>

- <xref:System.Single>

- <xref:System.String>

- <xref:System.Type>

- Jakýkoli typ výčtu, jehož základní typ je <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>nebo <xref:System.Int64>.

Následující příklad definuje třídu `DescriptionAttribute`, která je odvozena z <xref:System.Attribute>. Konstruktor třídy má parametr typu `Descriptor`, takže třída není kompatibilní se specifikací CLS. Všimněte si, C# že kompilátor generuje upozornění, ale zkompiluje úspěšně, zatímco kompilátor Visual Basic emituje ani upozornění, ani chybu.

[!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
[!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]

<a name="CLSAttribute"></a>

## <a name="the-clscompliantattribute-attribute"></a>Atribut CLSCompliantAttribute

Atribut <xref:System.CLSCompliantAttribute> slouží k označení, zda prvek programu vyhovuje specifikaci CLS (Common Language Specification). Konstruktor <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29?displayProperty=nameWithType> obsahuje jeden povinný parametr `isCompliant`, který označuje, zda je prvek program kompatibilní se specifikací CLS.

V době kompilace kompilátor detekuje nekompatibilní prvky, které se považují za kompatibilní se specifikací CLS, a vygeneruje upozornění. Kompilátor negeneruje upozornění pro typy nebo členy, které jsou explicitně deklarovány tak, že nejsou kompatibilní.

Vývojáři komponent mohou použít atribut <xref:System.CLSCompliantAttribute> dvěma způsoby:

- Pro definování částí veřejného rozhraní vystaveného komponentou, která je kompatibilní se specifikací CLS, a částí, které nejsou kompatibilní se specifikací CLS. Když je atribut použit k označení určitých prvků programu jako kompatibilní se specifikací CLS, jeho použití zaručuje, že tyto prvky jsou přístupné ze všech jazyků a nástrojů, které cílí na .NET Framework.

- Aby bylo zajištěno, že veřejné rozhraní knihovny součástí zpřístupňuje pouze prvky programu, které jsou kompatibilní se specifikací CLS. Pokud prvky nejsou kompatibilní se specifikací CLS, kompilátory většinou vystaví upozornění.

> [!WARNING]
> V některých případech vynutily jazykové kompilátory pravidla kompatibilní se specifikací CLS bez ohledu na to, zda je použit atribut <xref:System.CLSCompliantAttribute>. Například definování statického člena v rozhraní narušuje pravidlo specifikace CLS. V tomto ohledu, pokud definujete člena `static` (in C#) nebo `Shared` (v Visual Basic) v rozhraní, kompilátory C# a Visual Basic zobrazí chybovou zprávu a aplikace nebude zkompilována.

Atribut <xref:System.CLSCompliantAttribute> je označen atributem <xref:System.AttributeUsageAttribute>, který má hodnotu <xref:System.AttributeTargets.All?displayProperty=nameWithType>. Tato hodnota umožňuje použít atribut <xref:System.CLSCompliantAttribute> pro libovolný prvek programu, včetně sestavení, modulů, typů (tříd, struktur, výčtů, rozhraní a delegátů), členů typu (konstruktory, metody, vlastnosti, pole a události), parametry, Obecné parametry a návratové hodnoty. Nicméně v praxi byste měli použít atribut pouze pro sestavení, typy a členy typu. V opačném případě kompilátory ignorují atribut a pokračují v generování upozornění kompilátoru pokaždé, když narazí na nekompatibilní parametr, obecný parametr nebo návratovou hodnotu ve veřejném rozhraní knihovny.

Hodnota atributu <xref:System.CLSCompliantAttribute> dědí z obsažených prvků programu. Například pokud je sestavení označeno jako kompatibilní se specifikací CLS, jeho typy jsou také kompatibilní se specifikací CLS. Pokud je typ označený jako kompatibilní se specifikací CLS, jeho vnořené typy a členy jsou také kompatibilní se specifikací CLS.

Zděděné dodržování předpisů lze explicitně přepsat použitím atributu <xref:System.CLSCompliantAttribute> pro obsažený programový prvek. Například můžete použít atribut <xref:System.CLSCompliantAttribute> s `isCompliant` hodnotou `false` k definování nekompatibilního typu v vyhovujícím sestavení a můžete použít atribut s `isCompliant` hodnotou `true` k definování kompatibilního typu v sestavení, které nedodržuje předpisy. Můžete také definovat nekompatibilní členy v typu, který odpovídá. Nevyhovující typ ale nemůže mít odpovídající členy, takže nemůžete použít atribut s `isCompliant` hodnotou `true` k přepsání dědění z nekompatibilního typu.

Při vývoji komponent byste vždy měli použít atribut <xref:System.CLSCompliantAttribute> k označení, zda vaše sestavení, jeho typy a jeho členové jsou kompatibilní se specifikací CLS.

Vytvoření součástí odpovídajících specifikaci CLS:

1. Pomocí <xref:System.CLSCompliantAttribute> označíte sestavení jako kompatibilní se specifikací CLS.

2. Označte všechny veřejně vystavené typy v sestavení, které nejsou kompatibilní se specifikací CLS, jako nevyhovující.

3. Označte všechny veřejně vystavené členy v typech kompatibilních se specifikací CLS jako nevyhovující.

4. Poskytněte alternativu kompatibilní se specifikací CLS pro členy, které nedodržují specifikaci CLS.

Pokud jste úspěšně označili všechny typy a členy, které nedodržují předpisy, kompilátor by neměl generovat žádná upozornění, která nedodržují předpisy. Měli byste však určit, kteří členové nejsou kompatibilní se specifikací CLS, a seznamte se s alternativami kompatibilními se specifikací CLS v dokumentaci k produktu.

Následující příklad používá atribut <xref:System.CLSCompliantAttribute> k definování sestavení kompatibilního se specifikací CLS a typu, `CharacterUtilities`, který má dva členy nekompatibilní se specifikací CLS. Vzhledem k tomu, že oba členy jsou označeny atributem `CLSCompliant(false)`, kompilátor nevydá žádná upozornění. Třída také poskytuje alternativu odpovídající specifikaci CLS pro obě metody. Obvykle bychom přidali dvě přetížení do metody `ToUTF16` pro zajištění alternativ odpovídajících specifikaci CLS. Nicméně vzhledem k tomu, že metody nemohou být přetíženy na základě návratové hodnoty, názvy metod odpovídajících specifikaci CLS se liší od názvů nevyhovujících metod.

[!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
[!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]

Pokud vyvíjíte aplikaci místo knihovny (tj. Pokud nezveřejňujete typy nebo členy, které mohou být spotřebovány jinými vývojáři aplikací), dodržování předpisů CLS prvků programu, které vaše aplikace spotřebovává, je důležité pouze v případě, že je váš jazyk nepodporuje. . V takovém případě kompilátor jazyka vygeneruje chybu, pokud se pokusíte použít element, který není kompatibilní se specifikací CLS.

<a name="CrossLang"></a>

## <a name="cross-language-interoperability"></a>Vzájemná funkční spolupráce mezi jazyky

Jazyková nezávislost má několik možných významů. Jeden z nich, který je popsaný v článku [nezávislá na Nezávislostech jazyka a jazykově nezávislé součásti](../../docs/standard/language-independence-and-language-independent-components.md), zahrnuje plynulé využívání typů napsaných v jednom jazyce z aplikace napsané v jiném jazyce. Druhý význam, který je hlavním cílem tohoto článku, zahrnuje sloučení kódu napsaného ve více jazycích do jediného sestavení rozhraní .NET Framework.

Následující příklad znázorňuje interoperabilitu mezi jazyky vytvořením knihovny tříd s názvem Utilities.dll, která obsahuje dvě třídy `NumericLib` a `StringLib`. Třída `NumericLib` je napsána v jazyce C# a třída `StringLib` je napsána v jazyce Visual Basic. Zde je zdrojový kód pro StringUtil.vb, který obsahuje jeden člen, `ToTitleCase`, ve své třídě `StringLib`.

[!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]

Zde je zdrojový kód pro NumberUtil.cs, který definuje třídu `NumericLib` se dvěma členy `IsEven` a `NearZero`.

[!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]

Chcete-li zabalit dvě třídy do jednoho sestavení, musíte je zkompilovat do modulů. Pro kompilaci zdrojového kódu jazyka Visual Basic do modulu použijte tento příkaz:

```console
vbc /t:module StringUtil.vb
```

Další informace o syntaxi příkazového řádku kompilátoru Visual Basic naleznete v tématu [sestavování z příkazového řádku](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Pro kompilaci zdrojového kódu jazyka C# do modulu použijte tento příkaz:

```console
csc /t:module NumberUtil.cs
```

Další informace o syntaxi příkazového řádku C# kompilátoru najdete v tématu [sestavování z příkazového řádku pomocí CSc. exe](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).

Pak použijte [Možnosti linkeru](/cpp/build/reference/linker-options) ke kompilaci dvou modulů do sestavení:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Následující příklad následně volá metody `NumericLib.NearZero` a `StringLib.ToTitleCase`. Kód jazyka Visual Basic i kód jazyka C# může přistupovat k metodám v obou třídách.

[!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
[!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]

Pro kompilaci kódu jazyka Visual Basic použijte tento příkaz:

```console
vbc example.vb /r:UtilityLib.dll
```

Chcete-li C#kompilovat s, změňte název kompilátoru z **Vbc** na **CSC**a změňte příponu souboru z. vb na. cs:

```console
csc example.cs /r:UtilityLib.dll
```

## <a name="see-also"></a>Viz také:

- <xref:System.CLSCompliantAttribute>
