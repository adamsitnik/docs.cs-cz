---
title: 'Postupy: Nastavení entit jako serializovatelných'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 40a0b4d5a49f88af1bedcbefdd117f6c000b791d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793564"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="eae1d-102">Postupy: Nastavení entit jako serializovatelných</span><span class="sxs-lookup"><span data-stu-id="eae1d-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="eae1d-103">Při generování kódu můžete označit entity jako serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="eae1d-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="eae1d-104">Třídy entit jsou upraveny <xref:System.Runtime.Serialization.DataContractAttribute> atributem a sloupcem <xref:System.Runtime.Serialization.DataMemberAttribute> s atributem.</span><span class="sxs-lookup"><span data-stu-id="eae1d-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="eae1d-105">Vývojáři, kteří používají Visual Studio, mohou pro tento účel použít Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="eae1d-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="eae1d-106">Pokud používáte nástroj příkazového řádku SQLMetal, použijte možnost **/Serialization** s `unidirectional` argumentem.</span><span class="sxs-lookup"><span data-stu-id="eae1d-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="eae1d-107">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="eae1d-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eae1d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="eae1d-108">Example</span></span>  
 <span data-ttu-id="eae1d-109">Následující příkazové řádky SQLMetal vytváří soubory s serializovatelnými entitami.</span><span class="sxs-lookup"><span data-stu-id="eae1d-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="eae1d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eae1d-110">See also</span></span>

- [<span data-ttu-id="eae1d-111">Serializace</span><span class="sxs-lookup"><span data-stu-id="eae1d-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="eae1d-112">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="eae1d-112">Creating the Object Model</span></span>](creating-the-object-model.md)
