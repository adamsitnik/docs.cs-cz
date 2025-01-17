---
title: Portové operace v rozhraní .NET Framework s jazykem Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 10488f896ff7c6761e831d2a8af52249a19cf7d6
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524382"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Portové operace v rozhraní .NET Framework s jazykem Visual Basic

K sériovým portům počítače můžete přistupovat pomocí tříd .NET Framework v oboru názvů <xref:System.IO.Ports?displayProperty=nameWithType>. Nejdůležitější třída, <xref:System.IO.Ports.SerialPort>, poskytuje rozhraní pro synchronní a vstupně-výstupní operace řízené událostmi, přístup k stavům PIN a přerušení a přístup k vlastnostem sériového ovladače. Může být zabalen do objektu <xref:System.IO.Stream>, který je přístupný prostřednictvím vlastnosti <xref:System.IO.Ports.SerialPort.BaseStream>. Balení <xref:System.IO.Ports.SerialPort> v objektu <xref:System.IO.Stream> umožňuje sériovému portu, který má být k dispozici v třídách, které používají datové proudy. Obor názvů obsahuje výčty, které zjednodušují řízení sériových portů.

Nejjednodušší způsob, jak vytvořit objekt <xref:System.IO.Ports.SerialPort>, je prostřednictvím metody <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.

> [!NOTE]
> Třídy .NET Framework nemůžete použít k přímému přístupu k jiným typům portů, jako jsou paralelní porty, porty USB a tak dále.

## <a name="enumerations"></a>Výčty

Tato tabulka uvádí a popisuje hlavní výčty používané pro přístup k sériovému portu:

|Výčet|Popis|
|---|---|
|<xref:System.IO.Ports.Handshake>|Určuje protokol řízení použitý při vytváření komunikace sériového portu pro objekt <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.Parity>|Určuje paritní bit pro objekt <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.SerialData>|Určuje typ znaku, který byl přijat na sériovém portu objektu <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.SerialError>|Určuje chyby, ke kterým dochází u objektu <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.SerialPinChange>|Určuje typ změny, ke kterému došlo u objektu <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.StopBits>|Určuje počet stop bitů používaných pro objekt <xref:System.IO.Ports.SerialPort>.|

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Přístup k portům počítače](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
