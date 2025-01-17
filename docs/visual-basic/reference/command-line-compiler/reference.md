---
title: -Reference (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 8f144dbd9376f15ac92e283472dac786a6972045
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775608"
---
# <a name="-reference-visual-basic"></a>-Reference (Visual Basic)
Způsobí, že kompilátor provede informace o typech v zadaných sestaveních, které jsou k dispozici pro projekt, který právě kompilujete.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-reference:fileList  
```

or

```console
-r:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`fileList`|Požadováno. Seznam názvů souborů sestavení oddělených čárkami. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek.|  
  
## <a name="remarks"></a>Poznámky  
 Soubory, které importujete, musí obsahovat metadata sestavení. Mimo sestavení jsou viditelné pouze veřejné typy. Možnost [-addmodule –](../../../visual-basic/reference/command-line-compiler/addmodule.md) Importuje metadata z modulu.  
  
 Pokud odkazujete na sestavení (sestavení A), které odkazuje na jiné sestavení (sestavení B), musíte odkazovat na sestavení B, pokud:  
  
- Typ ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.  
  
- Je vyvoláno pole, vlastnost, událost nebo metoda, které mají návratový typ nebo typ parametru ze sestavení B.  
  
 Pomocí [-LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) Určete adresář, ve kterém je umístěn jeden nebo více odkazů na sestavení.  
  
 Aby kompilátor rozpoznal typ v sestavení (ne v modulu), musí být vynucen přeložit typ. Jedním z příkladů toho, jak to lze provést, je definovat instanci typu. Další způsoby jsou k dispozici pro překlad názvů typů v sestavení pro kompilátor. Například Pokud převezmete z typu v sestavení, název typu je poté pro kompilátor znám.  
  
 Ve výchozím nastavení se používá soubor odezvy Vbc. rsp, který odkazuje na běžně používaná .NET Framework sestavení. Pokud nechcete, aby kompilátor používal Vbc. rsp, použijte `-noconfig`.  
  
 Krátká forma `-reference` je `/r`.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje zdrojový soubor `Input.vb` a referenční sestavení z `Metad1.dll` a `Metad2.dll` k výrobě `Out.exe`.  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
