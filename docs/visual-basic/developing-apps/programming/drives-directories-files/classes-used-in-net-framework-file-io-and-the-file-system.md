---
title: Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: f9d898756b6b17ae69d1af7dd747c20a26d88417
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348004"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework (Visual Basic)
Následující tabulky uvádějí třídy běžně používané pro soubor rozhraní .NET Framework vstupně-výstupních operací zařazených do kategorií do souboru vstupně-výstupních tříd, použitý k vytvoření datových proudů třídy a třídy používané pro čtení a zápis do datových proudů.  
  
Ucelenější seznam najdete v tématu [– přehled knihovny tříd](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Základní vstupně-výstupních tříd pro soubory, disky a adresáře  
 Následující tabulka uvádí a popisuje hlavní třídy používané pro soubor vstupně-výstupních operací.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Poskytuje statické metody pro vytváření, přesouvání a vytváření výčtů adresářů a podadresářů.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Poskytuje instanční metody pro vytváření, přesouvání a vytváření výčtů adresářů a podadresářů.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Poskytuje instanční metody pro vytváření, přesouvání a vytváření výčtů jednotky.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Poskytuje statické metody pro vytváření, kopírování, odstraňování, přesouvání a otevírání souborů a pomáhá při vytváření `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Definuje konstanty pro čtení, zápisu a přístup pro čtení a zápis do souboru.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Poskytuje atributy pro soubory a adresáře například `Archive`, `Hidden`, a `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Poskytuje statické metody pro vytváření, kopírování, odstraňování, přesouvání a otevírání souborů a pomáhá při vytváření `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Určuje, jak je soubor otevřen. Tento parametr je zadán v mnoha konstruktory pro `FileStream` a `IsolatedStorageFileStream`a `Open` metody <xref:System.IO.File> a <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Definuje konstanty pro řízení typ přístupu, které může mít jiné datové proudy souborů na stejný soubor.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Poskytuje metody a vlastnosti pro zpracování řetězců adresářů.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Řídí přístup k souborům a složkám tak, že definujete <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> a <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> oprávnění.|  
  
## <a name="classes-used-to-create-streams"></a>Třídy používané k vytvoření datových proudů  
 Následující tabulka uvádí a popisuje hlavní třídy používané k vytvoření datových proudů.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Přidává další vrstvu ke čtení a zápisu operace na jiný datový proud vyrovnávací paměti.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Podporuje náhodný přístup k souborům prostřednictvím jeho <xref:System.IO.FileStream.Seek%2A> metoda. <xref:System.IO.FileStream> ve výchozím nastavení otevře souborů synchronně, ale také podporuje asynchronní operace.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Vytvoří datový proud, jehož záložní úložiště je paměť, nikoli soubor.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Poskytuje základní datový proud s daty pro přístup k síti.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Definuje datový proud, který odkazuje datových proudů na kryptografické transformace.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Třídy používané pro čtení a zápis do datových proudů  
 V následující tabulce jsou uvedeny konkrétní třídy používané pro čtení a zápis do souborů s datovými proudy.  
  
|**Třída**|**Popis**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Čtení kódovaných řetězců a primitivní datové typy z <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Zapíše zakódované řetězce a primitivní datové typy <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Přečte znaky z <xref:System.IO.FileStream>s použitím <xref:System.IO.StreamReader.CurrentEncoding%2A> pro převod znaků na bajty a zpět. <xref:System.IO.StreamReader> má konstruktor, který se pokusí zjistit správný <xref:System.IO.StreamReader.CurrentEncoding%2A> pro daný datový proud, podle přítomnosti <xref:System.IO.StreamReader.CurrentEncoding%2A>-konkrétní preambule, jako je například značku pořadí bajtů.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Zapíše znaků, které mají `FileStream`s použitím <xref:System.IO.StreamWriter.Encoding%2A> pro převod znaků na bajty.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Přečte znaky z `String`. Výstup může být buď datový proud v jakémkoli kódování nebo `String`.|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Zapíše znaků, které mají `String`. Výstup může být buď datový proud v jakémkoli kódování nebo `String`.|  
  
## <a name="see-also"></a>Viz také:

- [Skládání streamů](../../../../standard/io/composing-streams.md)
- [Vstup/výstup souborů a streamů](../../../../standard/io/index.md)
- [Asynchronní vstupně-výstupní operace se soubory](../../../../standard/io/asynchronous-file-i-o.md)
- [Základy vstupně-výstupní operace souboru rozhraní .NET Framework a systému souborů (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
