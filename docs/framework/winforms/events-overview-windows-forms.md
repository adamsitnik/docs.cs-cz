---
title: Přehled událostí (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, event handling
- events [Windows Forms], about events
- delegates [Windows Forms], multicast
- delegates [Windows Forms], events and
- multicast event delegates
- Windows Forms controls, events
ms.assetid: 814a6a43-a312-4791-88d8-f75f9a4f8c4c
ms.openlocfilehash: 92942066b5f08ada0154781ae54b5d8494944ca1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963464"
---
# <a name="events-overview-windows-forms"></a>Přehled událostí (Windows Forms)
Událost je akce, na kterou můžete reagovat nebo "zpracovat" v kódu. Události mohou být generovány akcí uživatele, jako je například kliknutí myší nebo stisknutí klávesy. podle kódu programu; nebo systémem.

 Aplikace řízené událostmi spouštějí kód jako odpověď na událost. Každý formulář a ovládací prvek zveřejňuje předdefinovanou sadu událostí, které lze programovat. Pokud dojde k jedné z těchto událostí a v přidružené obslužné rutině události je kód, je vyvolán tento kód.

 Typy událostí vyvolaných objektem se liší, ale mnoho typů je běžné pro většinu ovládacích prvků. Například většina objektů <xref:System.Windows.Forms.Control.Click> zpracuje událost. Pokud uživatel klikne na formulář, je proveden kód v obslužné <xref:System.Windows.Forms.Control.Click> rutině události formuláře.

> [!NOTE]
> K mnoha událostem dochází ve spojení s jinými událostmi. Například v průběhu <xref:System.Windows.Forms.Control.DoubleClick> události <xref:System.Windows.Forms.Control.MouseDown>dojde k událostem, <xref:System.Windows.Forms.Control.MouseUp>a <xref:System.Windows.Forms.Control.Click> .

 Informace o tom, jak vyvolat a zpracovat událost, najdete v tématu [události](../../standard/events/index.md).

## <a name="delegates-and-their-role"></a>Delegáti a jejich role
 Delegáti jsou třídy, které se běžně používají v rámci .NET Framework k sestavení mechanismů pro zpracování událostí. Delegáti jsou zhruba rovni ukazatelům funkce, běžně používané v C++ vizuálů a dalších objektově orientovaných jazycích. Na rozdíl od ukazatelů na funkce jsou však delegáti objektově orientovaný, typově bezpečný a zabezpečený. Kromě toho, kde ukazatel na funkci obsahuje pouze odkaz na konkrétní funkci, se delegát skládá z odkazu na objekt a odkazuje na jednu nebo více metod v rámci objektu.

 Tento model událostí používá *delegáty* ke svázání událostí s metodami, které se používají k jejich zpracování. Delegát umožňuje registrovat jiné třídy pro oznamování událostí zadáním metody obslužné rutiny. Když dojde k události, delegát volá metodu Bound. Další informace o tom, jak definovat delegáty, najdete v tématu [události](../../standard/events/index.md).

 Delegáty mohou být vázány na jedinou metodu nebo na více metod, označovaných jako vícesměrové vysílání. Při vytváření delegáta pro událost (nebo Windows) se obvykle vytvoří událost vícesměrového vysílání. Vzácná výjimka může být událost, která má za následek určitou proceduru (například zobrazení dialogového okna), která by logicky neopakovala více časů na událost. Informace o tom, jak vytvořit delegáta vícesměrového vysílání [, najdete v tématu How to: Kombinovat delegáty (vícesměrové delegáty)](../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

 Delegát vícesměrového vysílání udržuje seznam volání metod, ke kterým je vázán. Delegát vícesměrového vysílání podporuje <xref:System.Delegate.Combine%2A> metodu pro přidání metody do seznamu vyvolání <xref:System.Delegate.Remove%2A> a metodu jejího odebrání.

 Když aplikace zaznamená událost, ovládací prvek vyvolá událost vyvoláním delegáta pro danou událost. Delegát zase volá metodu Bound. V nejběžnějším případě (delegát vícesměrového vysílání) volá delegát každou metodu, která je v seznamu volání, a poskytuje oznámení 1:1. Tato strategie znamená, že ovládací prvek nemusí udržovat seznam cílových objektů pro oznamování událostí – delegát zpracovává veškerou registraci a oznámení.

 Delegáti také umožňují svázat více událostí se stejnou metodou, což umožňuje oznámení typu n:1. Například událost kliknutí na tlačítko a příkaz nabídky-Click může vyvolat stejný delegát, který pak volá jedinou metodu pro zpracování těchto samostatných událostí stejným způsobem.

 Mechanizmus vazby, který se používá s delegáty, je dynamický: delegát může být vázán v době běhu na jakoukoli metodu, jejíž signatura odpovídá obslužné rutině události. Pomocí této funkce můžete nastavit nebo změnit metodu vazby v závislosti na podmínce a dynamicky připojit obslužnou rutinu události k ovládacímu prvku.

## <a name="see-also"></a>Viz také:

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md)
