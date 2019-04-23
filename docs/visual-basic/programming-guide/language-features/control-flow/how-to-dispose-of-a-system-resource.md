---
title: 'Postupy: Odstranění systémového prostředku (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: e3594db036edc3a6288b0373737c1ee26a691a57
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341904"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="b7318-102">Postupy: Odstranění systémového prostředku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7318-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="b7318-103">Můžete použít `Using` bloku zaručí, že systém odstraňuje prostředku při opuštění bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="b7318-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="b7318-104">To je užitečné, pokud používáte systémového prostředku, která spotřebovává velké množství paměti, nebo jiné komponenty také chcete použít.</span><span class="sxs-lookup"><span data-stu-id="b7318-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="b7318-105">K uvolnění připojení databáze. Po dokončení se s ním kódu</span><span class="sxs-lookup"><span data-stu-id="b7318-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="b7318-106">Nezapomeňte zadat odpovídající [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro připojení k databázi na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="b7318-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="b7318-107">Vytvoření `Using` blokovat s `Using` a `End Using` příkazy.</span><span class="sxs-lookup"><span data-stu-id="b7318-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="b7318-108">Uvnitř bloku vložte kód, který se zabývá připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="b7318-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="b7318-109">Deklarace připojení a vytvořte její instanci v rámci `Using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="b7318-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="b7318-110">Systém odstraňuje prostředků bez ohledu na to, jak ukončení bloku i v případě neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="b7318-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="b7318-111">Všimněte si, že nemáte přístup `sqc` z mimo `Using` blokovat, protože jeho rozsah je omezen na blok.</span><span class="sxs-lookup"><span data-stu-id="b7318-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="b7318-112">Tento stejný postup můžete použít na systémový prostředek, jako je například popisovač souboru nebo obálky COM.</span><span class="sxs-lookup"><span data-stu-id="b7318-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="b7318-113">Můžete použít `Using` blokovat, pokud chcete mít jistotu ponechat prostředek k dispozici pro jiné komponenty po zavření `Using` bloku.</span><span class="sxs-lookup"><span data-stu-id="b7318-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7318-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7318-114">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="b7318-115">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="b7318-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="b7318-116">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="b7318-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="b7318-117">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="b7318-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="b7318-118">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="b7318-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="b7318-119">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="b7318-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="b7318-120">Příkaz Using</span><span class="sxs-lookup"><span data-stu-id="b7318-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
