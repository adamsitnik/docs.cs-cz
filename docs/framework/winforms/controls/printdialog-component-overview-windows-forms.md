---
title: PrintDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 2478990e3cec00df9a748dbd9875485e5f060ed7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211759"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog – přehled komponenty (Windows Forms)

Windows Forms [PrintDialog](printdialog-component-windows-forms.md) komponenta je předem nakonfigurované dialogové okno umožňuje vybrat tiskárnu, zvolte stránky k tisku a určit další nastavení související s tiskem v aplikacích založených na Windows. Použijte jako jednoduchým řešením pro tiskárnu a výběr nastavení související s tiskem namísto dialogové okno Vlastní konfigurace. Můžete povolit uživatelům tisknout mnoho částí své dokumenty: vytisknout všechny vybrané stránce rozsah tisku a Tisk výběru. Pomocí standardní dialogová okna Windows, můžete vytvořit aplikace, jejichž základní funkce je okamžitě uživatelé znají. <xref:System.Windows.Forms.PrintDialog> Komponenta dědí z <xref:System.Windows.Forms.CommonDialog> třídy.

## <a name="working-with-the-component"></a>Práce s komponentou

Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna v době běhu. Tato součást obsahuje vlastnosti, které se týkají buď jedné tiskové úlohy (<xref:System.Drawing.Printing.PrintDocument> třídy) nebo nastavení jednotlivých tiskáren (<xref:System.Drawing.Printing.PrinterSettings> třídy). Jeden z následujících, pak může sdílet více tiskáren.

Když se přidá do formuláře, <xref:System.Windows.Forms.PrintDialog> součást se zobrazí v hlavním panelu v dolní části Návrháře formulářů Windows v sadě Visual Studio.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.PrintDialog>
- [Komponenta PrintDialog](printdialog-component-windows-forms.md)
