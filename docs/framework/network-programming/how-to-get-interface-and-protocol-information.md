---
title: 'Postupy: Získání informace o rozhraní a protokolu'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: fd88d26c-4063-495e-a253-736ac3e6b23f
ms.openlocfilehash: e70afa6b3633a5868491e421c7e8e44bf9f3e895
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624582"
---
# <a name="how-to-get-interface-and-protocol-information"></a>Postupy: Získání informace o rozhraní a protokolu
Tento příklad znázorňuje způsob čtení statistik protokolu TCP pro síťové rozhraní.  
  
## <a name="example"></a>Příklad  
  
```  
public static void ShowTcpStatistics(NetworkInterfaceComponent version)  
{  
    IPGlobalProperties properties =  
          IPGlobalProperties.GetIPGlobalProperties();  
    TcpStatistics tcpstat = null;  
    Console.WriteLine("");  
    switch (version)  
    {  
        case NetworkInterfaceComponent.IPv4:  
             tcpstat = properties.GetTcpIPv4Statistics();  
            Console.WriteLine("TCP/IPv4 Statistics:");  
            break;  
        case NetworkInterfaceComponent.IPv6:  
            tcpstat = properties.GetTcpIPv6Statistics();  
            Console.WriteLine("TCP/IPv6 Statistics:");  
            break;  
        default:  
            throw new ArgumentException("version");  
            break;  
    }  
    Console.WriteLine("  Minimum Transmission Timeout. : {0}",   
        tcpstat.MinimumTransmissionTimeout);  
    Console.WriteLine("  Maximum Transmission Timeout. : {0}",   
        tcpstat.MaximumTransmissionTimeout);  
  
    Console.WriteLine("  Connection Data:");  
    Console.WriteLine("      Current : {0}",   
    tcpstat.CurrentConnections);  
    Console.WriteLine("      Cumulative : {0}",   
        tcpstat.CumulativeConnections);  
    Console.WriteLine("      Initiated  : {0}",   
        tcpstat.ConnectionsInitiated);  
    Console.WriteLine("      Accepted : {0}",   
        tcpstat.ConnectionsAccepted);  
    Console.WriteLine("      Failed Attempts : {0}",   
        tcpstat.FailedConnectionAttempts);  
    Console.WriteLine("      Reset : {0}",   
        tcpstat.ResetConnections);  
  
    Console.WriteLine("");  
    Console.WriteLine("  Segment Data:");  
    Console.WriteLine("      Received  ................... : {0}",   
        tcpstat.SegmentsReceived);  
    Console.WriteLine("      Sent : {0}",   
        tcpstat.SegmentsSent);  
    Console.WriteLine("      Retransmitted : {0}",   
        tcpstat.SegmentsResent);  
  
    Console.WriteLine("");  
}  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy **System.Net** oboru názvů.
