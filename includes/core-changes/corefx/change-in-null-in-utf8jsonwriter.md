---
ms.openlocfilehash: 7c39fe7ffd59fa7a5564bb45f32a6a2fbe0ddb33
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117148"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a>Změna v sémantikě `(string)null` v Utf8JsonWriter

V rozhraní .NET Core 3,0 Preview 7 je řetězec s hodnotou null považován za prázdný řetězec v <xref:System.Text.Json.Utf8JsonWriter>. Počínaje rozhraním .NET Core 3,0 Preview 8 vygeneruje řetězec null výjimku při použití jako názvu vlastnosti a vygeneruje token JSON s hodnotou null, pokud se používá jako hodnota.

#### <a name="change-description"></a>Změnit popis

V rozhraní .NET Core 3,0 Preview 7 `null` byl řetězec při psaní názvů vlastností a při psaní hodnot `""` považován za obojí.  

Počínaje rozhraním .NET Core 3,0 `null` Preview 8 je název vlastnosti `ArgumentNullException`vyvolána a `null` hodnota je považována za volání <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> nebo <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.

Vezměte v úvahu následující kód:

```csharp
string propertyName1 = null;
string propertyValue1 = null;
string propertyName2 = "prop2";
string propertyValue2 = null;
string simpleValue1 = null;

using (Utf8JsonWriter writer = new Utf8JsonWriter(stream))
{
    writer.WriteStartArray();

    writer.WriteStartObject();
    writer.WriteString(propertyName1, propertyValue1);
    writer.WriteString(propertyName2, propertyValue2);
    writer.WriteEndObject();

    writer.WriteStringValue(simpleValue1);

    writer.WriteEndArray();
}
```

Pokud spustíte s .NET Core 3,0 Preview 7, modul pro zápis vytvoří následující výstup:

```js
[{"":"","prop2":""},""]
```

Počínaje rozhraním .NET Core 3,0 Preview 8 volání `writer.WriteString(propertyName1, propertyValue1)` <xref:System.ArgumentNullException>vyvolá výjimku.  Pokud `propertyName1 = null` je`propertyName1 = string.Empty`nahrazeno, výstup by nyní byl:

```js
[{"":null,"prop2":null},null]
```

Tato změna byla provedena pro lepší zarovnání se očekáváním volajícího pro `null` hodnoty.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 8

#### <a name="recommended-action"></a>Doporučená akce

Při psaní názvů vlastností a hodnot pomocí <xref:System.Text.Json.Utf8JsonWriter> třídy:

- Zajistěte`null` , aby jako názvy vlastností byly použity jiné než řetězce.

- Pokud je požadované předchozí chování, použijte volání slučování s hodnotou null; například `writer.WriteString(propertyName1 ?? "", propertyValue1)`.

- Pokud zápis `null` literálu `null` pro řetězcovou hodnotu není žádoucí, použijte `writer.WriteString(propertyName2, propertyValue2 ?? "")`volání slučování s hodnotou null, například.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Char%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Char})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)`

-->
