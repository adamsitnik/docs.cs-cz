---
title: Začínáme se službou Azure Queue Storage s využitím F#
description: Fronty Azure poskytují spolehlivé a asynchronní zasílání zpráv mezi součástmi aplikace. Cloudové zasílání zpráv umožňuje nezávisle škálovat komponenty vaší aplikace.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: a09cbdd4b995e34177c110ce91b02162bb19dfa8
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423849"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Začínáme s úložištěm Azure Queue pomocí jazyka F\#

Azure Queue Storage poskytuje cloudové zprávy mezi součástmi aplikace. V navrhování aplikací pro škálování jsou součásti aplikace často odděleny, takže je lze škálovat nezávisle. Queue Storage zajišťuje asynchronní zasílání zpráv pro komunikaci mezi součástmi aplikace, ať už jsou spuštěné v cloudu, v desktopovém prostředí, na místním serveru nebo na mobilním zařízení. Queue Storage také podporuje správu asynchronních úloh a vytváření pracovních toků procesů.

### <a name="about-this-tutorial"></a>O tomto kurzu

V tomto kurzu se dozvíte F# , jak napsat kód pro některé běžné úlohy pomocí služby Azure Queue Storage. Mezi zahrnuté úlohy patří vytváření a odstraňování front a přidávání, čtení a odstraňování zpráv fronty.

Koncepční přehled služby Queue Storage najdete v [příručce .NET pro úložiště Queue](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Požadavky

Pokud chcete použít tuto příručku, musíte nejdřív [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).
Pro tento účet budete taky potřebovat přístupový klíč k úložišti.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F# skriptu a spuštění F# Interactive

Ukázky v tomto článku se dají použít buď v F# aplikaci, nebo ve F# skriptu. Chcete-li F# vytvořit skript, vytvořte soubor s příponou `.fsx`, například `queues.fsx`ve vašem F# vývojovém prostředí.

V dalším kroku pomocí [Správce balíčků](package-management.md) , jako je [paket](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) , nainstalujte balíček `WindowsAzure.Storage` a odkaz `WindowsAzure.Storage.dll` ve svém skriptu pomocí direktivy `#r`.

### <a name="add-namespace-declarations"></a>Přidat deklarace oboru názvů

Do horní části `queues.fsx` souboru přidejte následující příkazy `open`:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Získání připojovacího řetězce

Pro tento kurz budete potřebovat připojovací řetězec Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [Konfigurace připojovacích řetězců úložiště](/azure/storage/storage-configure-connection-string).

V tomto kurzu do skriptu zadáte svůj připojovací řetězec, například:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

To však **nedoporučujeme** pro skutečné projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy buďte opatrní, abyste chránili klíč účtu úložiště. Vyhněte se distribuci jiným uživatelům, pevným kódováním nebo uložením v souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Klíč můžete znovu vygenerovat pomocí webu Azure Portal, pokud se domníváte, že je možné, že došlo k ohrožení zabezpečení.

Pro reálné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru. Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Použití Azure Configuration Manager je volitelné. Můžete také použít rozhraní API, jako je .NET Framework typ `ConfigurationManager`.

### <a name="parse-the-connection-string"></a>Analyzovat připojovací řetězec

K analýze připojovacího řetězce použijte:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Tato akce vrátí `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Vytvoření klienta Služba front

Třída `CloudQueueClient` umožňuje načítat fronty uložené v úložišti front. Tady je jeden ze způsobů, jak vytvořit klienta služby:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Nyní jste připraveni napsat kód, který čte data z a zapisuje data do fronty úložiště.

## <a name="create-a-queue"></a>Vytvoření fronty

Tento příklad ukazuje, jak vytvořit frontu, pokud ještě neexistuje:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Vložení zprávy do fronty

Chcete-li vložit zprávu do existující fronty, vytvořte nejprve novou `CloudQueueMessage`. Dále zavolejte metodu `AddMessage`. `CloudQueueMessage` lze vytvořit buď pomocí řetězce (ve formátu UTF-8), nebo pole `byte`, například takto:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Prohlížet další zprávu

Můžete prohlížet zprávy před frontou, aniž byste je odebrali z fronty, voláním metody `PeekMessage`.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Získat další zprávu ke zpracování

Zprávu můžete načíst na začátku fronty ke zpracování voláním metody `GetMessage`.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Později označíte úspěšné zpracování zprávy pomocí `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Změna obsahu zprávy ve frontě

Obsah načtené zprávy můžete změnit na místě ve frontě. Pokud zpráva představuje pracovní úlohu, můžete tuto funkci použít k aktualizaci stavu pracovní úlohy. Následující kód aktualizuje zprávu fronty novými obsahem a nastaví časový limit viditelnosti na prodloužení dalších 60 sekund. Tím se uloží stav práce, která je přidružená ke zprávě, a poskytne klientovi další minutu, aby pokračoval v práci na této zprávě. Pomocí této techniky můžete sledovat víceúrovňové pracovní postupy u zpráv ve frontě, aniž byste museli začít od začátku, pokud krok zpracování selže kvůli selhání hardwaru nebo softwaru. Obvykle byste zachovali počet opakování i v případě, že se zpráva znovu pokusí o více než pár časů, takže byste ji odstranili. To je chráněno proti zprávě, která při každém zpracování vyvolá chybu aplikace.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Zruší zařazení další zprávy do fronty.

Kód z fronty odřadí zprávu z fronty ve dvou krocích. Když zavoláte `GetMessage`, dostanete další zprávu ve frontě. Zpráva vrácená z `GetMessage` bude neviditelná pro jakýkoliv jiný kód, který čte zprávy z této fronty. Ve výchozím nastavení tato zpráva zůstane po dobu 30 sekund neviditelná. Chcete-li dokončit odebrání zprávy z fronty, je nutné také volat `DeleteMessage`. Tento dvoustupňový proces odebrání zprávy zaručuje, že pokud váš kód nedokáže zpracovat zprávu z důvodu selhání hardwaru nebo softwaru, může jiná instance kódu získat stejnou zprávu a zkusit to znovu. Váš kód volá `DeleteMessage` hned po zpracování zprávy.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Použití asynchronních pracovních postupů s rozhraními API služby Common Queue Storage

Tento příklad ukazuje, jak použít asynchronní pracovní postup s běžnými rozhraními API služby Queue Storage.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Další možnosti pro zprávy o zrušení fronty

Existují dva způsoby, jak můžete přizpůsobit načítání zpráv z fronty.
Nejprve můžete získat dávku zpráv (až do 32). Za druhé můžete nastavit delší nebo kratší časový limit neviditelnosti, což umožňuje, aby váš kód měl více nebo méně času na úplné zpracování každé zprávy. Následující příklad kódu používá `GetMessages` k získání 20 zpráv v jednom volání a pak zpracovává každou zprávu. Nastaví také časový limit neviditelnosti na pět minut pro každou zprávu. Všimněte si, že 5 minut začne u všech zpráv současně, takže po uplynutí 5 minut od volání `GetMessages`se všechny zprávy, které nebyly odstraněny, opět zobrazí.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Získat délku fronty

Můžete získat odhad počtu zpráv ve frontě. Metoda `FetchAttributes` požádá Služba front o načtení atributů fronty, včetně počtu zpráv. Vlastnost `ApproximateMessageCount` vrací poslední hodnotu získanou metodou `FetchAttributes` bez volání Služba front.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Odstranění fronty

Pokud chcete odstranit frontu a všechny zprávy, které jsou v ní obsažené, zavolejte metodu `Delete` u objektu Queue.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Další kroky

Teď, když jste se naučili základní informace o službě Queue Storage, získáte další informace o složitějších úlohách úložiště pomocí těchto odkazů.

- [Rozhraní API pro Azure Storage pro .NET](/dotnet/api/overview/azure/storage)
- [Poskytovatel typu Azure Storage](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog týmu Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Konfigurace připojovacích řetězců Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Referenční informace pro službu Azure Storage Services REST API](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
