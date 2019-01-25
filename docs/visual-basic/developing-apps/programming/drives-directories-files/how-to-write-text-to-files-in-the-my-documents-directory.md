---
title: 'Postupy: Zápis textu do souborů adresáři MyDocuments v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 6e1e53f6eb0e14afa82bde95637c1e4473391bd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595055"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Postupy: Zápis textu do souborů adresáři MyDocuments v jazyce Visual Basic
`My.Computer.FileSystem.SpecialDirectories` Objekt umožňuje přístup k adresářům speciální, například **MyDocuments** adresáře.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Psaní nové textové soubory v adresáři Moje dokumenty  
  
1.  Použití `My.Computer.FileSystem.SpecialDirectories.MyDocuments` vlastnost zadat cestu.  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  Použití `WriteAllText` způsob zápisu textu do zadaného souboru.  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Nahraďte `test.txt` s názvem souboru chcete zapsat.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento kód znovu vyvolá všechny výjimky, které mohou nastat při zápisu textu do souboru. Snížíte pravděpodobnost, že výjimky pomocí ovládacích prvků Windows Forms, jako [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) a [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) součásti, které omezují výběr uživatele na platný název souboru. Pomocí těchto ovládacích prvků není spolehlivá, ale. Systém souborů můžete změnit mezi časem uživatel vybere soubor a čas, který spouští kód. Zpracování výjimek je proto téměř vždy nezbytné při práci se soubory.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud používáte v kontextu částečným vztahem důvěryhodnosti, kód může vyvolat výjimku, protože nedostatečná oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
 Tento příklad vytvoří nový soubor. Pokud aplikace potřebuje vytvořit soubor, tato aplikace potřebuje vytvořit oprávnění pro složku. Oprávnění se nastavují pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze oprávnění, a menší oprávnění k zápisu. Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze oprávnění ke čtení pro jeden soubor, nikoli k udělení oprávnění vytvořit pro složku. Navíc je bezpečnější zapsat data do uživatelské složky než do kořenové složky nebo **Program Files** složky. Další informace najdete v tématu [Přehled technologie ACL](https://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
