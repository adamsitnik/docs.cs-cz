---
title: 'Postupy: vytváření entit serializovatelných'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 5e9d078ed2daacfa48b09693f533e9aade613281
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002707"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="f6255-102">Postupy: vytváření entit serializovatelných</span><span class="sxs-lookup"><span data-stu-id="f6255-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="f6255-103">Při generování kódu můžete označit entity jako serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="f6255-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="f6255-104">Třídy entit jsou upraveny pomocí atributu <xref:System.Runtime.Serialization.DataContractAttribute> a sloupce s atributem <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f6255-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="f6255-105">Vývojáři, kteří používají Visual Studio, mohou pro tento účel použít Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="f6255-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="f6255-106">Pokud používáte nástroj příkazového řádku SQLMetal, použijte možnost **/Serialization** s argumentem `unidirectional`.</span><span class="sxs-lookup"><span data-stu-id="f6255-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="f6255-107">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="f6255-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6255-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6255-108">Example</span></span>  
 <span data-ttu-id="f6255-109">Následující příkazové řádky SQLMetal vytváří soubory s serializovatelnými entitami.</span><span class="sxs-lookup"><span data-stu-id="f6255-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6255-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6255-110">See also</span></span>

- [<span data-ttu-id="f6255-111">Serializace</span><span class="sxs-lookup"><span data-stu-id="f6255-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="f6255-112">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="f6255-112">Creating the Object Model</span></span>](creating-the-object-model.md)
