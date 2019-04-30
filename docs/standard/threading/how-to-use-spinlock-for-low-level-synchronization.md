---
title: 'Postupy: použití SpinLock nízké úrovně synchronizace'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff604b94ecef1ffec5fe9845df7c5ba35f5857d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934430"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Postupy: použití SpinLock nízké úrovně synchronizace

Následující příklad ukazuje, jak používat <xref:System.Threading.SpinLock>. V tomto příkladu kritický oddíl provádí minimální množství práce, je vhodným kandidátem pro <xref:System.Threading.SpinLock>. Zvýšení práce s krátkým zvyšuje výkon <xref:System.Threading.SpinLock> oproti standardní zámku. Je však bod, ve kterém bude dražší než standardní zámek struktuře SpinLock. Pokud chcete zobrazit, jaký typ zámku poskytuje lepší výkon ve svém programu můžete použít funkce v nástrojích pro profilaci profilace souběžného zpracování. Další informace najdete v tématu [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> můžou být užitečné při zámek sdíleného prostředku není budete mít velmi dlouho. V takových případech na vícejádrových počítačích může být efektivnější blokovaná vlákna aktivovat pro několik cyklů, dokud se zámek je uvolněn. Která umožňuje, vlákno není stát blokované, což je proces náročnou na procesor. <xref:System.Threading.SpinLock> pokryjte za určitých podmínek, aby se zabránilo starvation logických procesorů nebo inverzi priority v systémech s technologií Hyper-Threading se zastaví.  
  
 V tomto příkladu <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> třídy, které vyžaduje synchronizaci uživatelů pro vícevláknový přístup. V aplikacích, které jsou cíleny rozhraní .NET Framework verze 4, Další možností je použít <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, který nevyžaduje žádné uzamčení uživatele.  
  
 Všimněte si použití `false` (`False` v jazyce Visual Basic) při volání funkce <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>. To poskytuje nejlepší výkon. Zadejte `true` (`True` v jazyce Visual Basic) na architektury IA64 používat ohrazení paměti, která vyprázdní vyrovnávací paměti zápis k zajištění, že zámek je teď k dispozici pro ostatní vlákna ukončíte.  
  
## <a name="see-also"></a>Viz také:

- [Práce s vlákny funkce a objekty](threading-objects-and-features.md)
- [Lock – příkaz (C#)](../../csharp/language-reference/keywords/lock-statement.md)
- [SyncLock – příkaz (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
