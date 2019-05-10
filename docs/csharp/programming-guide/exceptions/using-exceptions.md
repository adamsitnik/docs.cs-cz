---
title: Použití výjimek - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 9ab6c5029518cbe5deb0f2c5a16c99992022d7a3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595470"
---
# <a name="using-exceptions-c-programming-guide"></a>Použití výjimek (Průvodce programováním v C#)
V jazyce C# jsou chyby v programu v době běhu šířena přes program pomocí mechanizmu nazývány výjimkami. Výjimky jsou vyvolaných kódem, který dojde k chybě a zachytit kód, který můžete chybu opravit. Výjimky mohou být vyvolány pomocí rozhraní .NET Framework common language runtime (CLR) nebo kód v programu. Jakmile je vyvolána výjimka, rozšíří zásobníkem volání do `catch` se nachází příkaz pro výjimku. Nezachycených výjimek jsou zpracovány rutinou obecná výjimka poskytuje systém, který se zobrazí dialogové okno.  
  
 Výjimky jsou reprezentované pomocí třídy odvozené od <xref:System.Exception>. Tato třída identifikuje typ výjimky a obsahuje vlastnosti, které mají podrobnosti o výjimce. Došlo k výjimce zahrnuje vytvoření instance třídy výjimky odvozené, volitelně konfigurace vlastností výjimky a pak pomocí aktivační objekt `throw` – klíčové slovo. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Poté, co je vyvolána výjimka, modul runtime ověří aktuální příkaz Přesvědčte se, zda je v rámci `try` bloku. Pokud se jedná, některé `catch` bloky přidružené `try` bloku se zkontroluje, zda lze zachytit výjimku. `Catch` bloky obvykle určují typy výjimek; Pokud typ `catch` blok je stejného typu jako výjimky nebo základní třídu výjimky, `catch` bloku může zpracovat metodu. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Pokud příkaz, který vyvolá výjimku, není v rozsahu `try` bloku nebo, pokud `try` blok, který ji obklopuje nemá odpovídající `catch` bloku, modul runtime kontroluje volání metody pro `try` příkazu a `catch` bloky. Modul runtime bude pokračovat až do volání zásobníku, vyhledávání kompatibilní `catch` bloku. Po `catch` bloku je nalezen a spuštěn, řízení je předáno další příkaz, po který `catch` bloku.  
  
 A `try` příkaz může obsahovat více než jednu `catch` bloku. První `catch` je proveden příkaz, který dokáže zpracovat výjimky; všechny následující `catch` příkazy, i v případě, že jsou kompatibilní, jsou ignorovány. Proto catch bloky by měla být vždy seřazené od nejvíce konkrétní (nebo nejvíce odvozenému) nejméně specifická. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Před `catch` blok je spuštěn, modul runtime kontroluje `finally` bloky. `Finally` bloky povolit programátorovi, aby vyčistit všechny nejednoznačný stav, který by mohl být přetrvávající ze přerušené `try` bloku nebo uvolnit všem externím prostředkům (například obslužné rutiny grafiky, připojení k databázi nebo datové proudy souborů) bez čekání uvolňování paměti kolekce v modulu runtime pro dokončení objekty. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 Pokud `WriteByte()` došlo k výjimce, kód ve druhé `try` blok, který se pokusí znovu otevřete soubor selže, pokud `file.Close()` není volána, a soubor zůstane uzamčen. Protože `finally` bloky provádějí i v případě, že je vyvolána výjimka, `finally` blok v předchozím příkladu povolí pro soubor, který má být správně uzavřena, a pomáhá zabránit chybu.  
  
 Pokud žádné kompatibilní `catch` bloku se nachází v zásobníku volání po dojde k výjimce, nenastane některá z tři věci:  
  
- Je-li výjimka v rámci finalizační metodu, finalizační metoda byla přerušena a základní finalizační metodu, pokud existuje, je volána.  
  
- Pokud obsahuje zásobník volání statického konstruktoru nebo inicializátoru statické pole <xref:System.TypeInitializationException> je vyvolána výjimka s původní výjimky přiřazené <xref:System.Exception.InnerException%2A> vlastnost novou výjimku.  
  
- Pokud je dosaženo začátku vlákno, vlákno ukončeno.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)
