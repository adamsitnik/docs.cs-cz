---
title: Načtení dat pomocí mnoho sloupců ze souboru CSV pro machine learning zpracování – ML.NET
description: Zjistěte, jak načíst data data s mnoha sloupci ze souboru CSV pro použití v modelu strojového učení, vytváření, trénování a vyhodnocování s ML.NET
ms.date: 01/28/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 2ac672cf0d8c8906164c17d74c0214adeca360a9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289403"
---
# <a name="load-data-with-many-columns-from-a-csv-file-for-machine-learning-processing---mlnet"></a>Načtení dat pomocí mnoho sloupců ze souboru CSV pro machine learning zpracování – ML.NET

`TextLoader` slouží k načtení dat z textových souborů. Je třeba zadat sloupců dat, jejich typy a jejich umístění v textovém souboru.

Pokud vstupní soubor obsahuje mnoho sloupců stejného typu a vždy použít současně, přečtěte si je jako *vektoru sloupec*. Tato strategie výsledků ve schématu vyčištění dat a zabraňuje náklady zbytečně výkon, jak je znázorněno v následujícím příkladu:

[Příklad souboru](https://github.com/dotnet/machinelearning/tree/master/test/data/generated_regression_dataset.csv):

```console
-2.75,0.77,-0.61,0.14,1.39,0.38,-0.53,-0.50,-2.13,-0.39,0.46,140.66
-0.61,-0.37,-0.12,0.55,-1.00,0.84,-0.02,1.30,-0.24,-0.50,-2.12,148.12
-0.85,-0.91,1.81,0.02,-0.78,-1.41,-1.09,-0.65,0.90,-0.37,-0.22,402.20
0.28,1.05,-0.24,0.30,-0.99,0.19,0.32,-0.95,-1.19,-0.63,0.75,443.51
```

Čtení tohoto souboru pomocí `TextLoader`:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextReader(
    columns: new TextLoader.Column[]
    {
    // We read the first 10 values as a single float vector.
        new TextLoader.Column("FeatureVector",DataKind.R4,0,9),
        // Separately, read the target variable.
        new TextLoader.Column("Target",DataKind.R4,10)
    },
    // Default separator is tab, but we need a semicolon.
    separatorChar: ';',
    hasHeader: true
);

// Now read the file (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var data = reader.Read(dataPath);
```    