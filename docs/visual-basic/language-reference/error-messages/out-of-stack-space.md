---
title: Nedostatek místa v zásobníku (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 29dbdf74808fc98bb856483c3fd8e3a09a72113b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925577"
---
# <a name="out-of-stack-space-visual-basic"></a>Nedostatek místa v zásobníku (Visual Basic)
Zásobník představuje pracovní oblast paměti, která zvyšuje nebo snižuje dynamicky s požadavky prováděnému programu. Překročení omezení.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zkontrolujte, že nejsou postupy vnořené příliš hluboko.  
  
2. Zajistěte, aby rekurzivní procedury řádně ukončit.  
  
3. Pokud místní proměnné vyžadují další místní proměnné místa než je k dispozici, zkuste deklarace proměnných na úrovni modulu. Můžete také deklarovat všechny proměnné v postupu statické před `Property`, `Sub`, nebo `Function` – klíčové slovo s `Static`. Nebo můžete použít `Static` příkaz pro deklarování jednotlivých statické proměnné v rámci procedury.  
  
4. Některé z vašich pevné délky řetězců jako řetězce proměnné délky, znovu definujte, jak používat více místa v zásobníku než řetězce proměnné délky řetězce pevné délky. Můžete také definovat řetězec na úrovni modulu, ve kterém nevyžaduje žádné místo v zásobníku.  
  
5. Zkontrolujte počet vnořených `DoEvents` volání, funkcí s použitím `Calls` dialogové okno k zobrazení, které postupy jsou aktivní v zásobníku.  
  
6. Ujistěte se, že jste nezpůsobil "událost v kaskádě" vyvoláte událost, která volá proceduru události již v zásobníku. Událost v kaskádě je podobný postup volání rozhraní neukončený rekurzivní, ale je méně zřejmé, protože při volání jazyka Visual Basic, spíše než explicitní volání konstruktoru v kódu. Použití `Calls` dialogové okno k zobrazení, které postupy jsou aktivní v zásobníku.  
  
## <a name="see-also"></a>Viz také:

- [Okna paměti](/visualstudio/debugger/memory-windows)
