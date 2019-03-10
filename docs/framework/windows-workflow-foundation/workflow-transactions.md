---
title: Transakce pracovního postupu
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: cb2a72bb24640d214170c52b8b3bf0a328d3f775
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714616"
---
# <a name="workflow-transactions"></a><span data-ttu-id="95ed7-102">Transakce pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="95ed7-102">Workflow Transactions</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="95ed7-103">poskytuje podporu pro účastní <xref:System.Transactions> transakce pomocí <xref:System.Activities.Statements.TransactionScope> aktivity k určení oboru transakce jednotku práce.</span><span class="sxs-lookup"><span data-stu-id="95ed7-103">provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="95ed7-104">Zatímco <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> musí být explicitně Dokončit <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> aktivity implicitně volání dokončení transakce po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="95ed7-104">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="95ed7-105">Všechny aktivity, které jsou součástí <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope> aktivity účasti v transakci.</span><span class="sxs-lookup"><span data-stu-id="95ed7-105">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="95ed7-106">WF můžete tok transakcí do pracovních postupů prostřednictvím <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="95ed7-106">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="95ed7-107">Podobně jako <xref:System.Activities.Statements.TransactionScope> aktivity, všechny obsažené v <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> účastní v transakci.</span><span class="sxs-lookup"><span data-stu-id="95ed7-107">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="95ed7-108">WF zajišťuje této aktivity závislé na <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> pracuje s oběma <xref:System.Activities.Statements.TransactionScope> a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="95ed7-108">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="95ed7-109">Pokud poskytované systémem aktivity se nezabývají všechny požadavky, můžete vlastní aktivity vytvořené pomocí <xref:System.Activities.RuntimeTransactionHandle> povolit pokročilé toku a scénáře řízení transakce.</span><span class="sxs-lookup"><span data-stu-id="95ed7-109">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
<span data-ttu-id="95ed7-110">V následujícím příkladu je vytvořen skládající se z pracovního postupu <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje podřízené aktivity, včetně <xref:System.Activities.Statements.TransactionScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="95ed7-110">In the following example, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="95ed7-111"><xref:System.Activities.Statements.TransactionScope.Body%2A> Aktivity <xref:System.Activities.Statements.TransactionScope> provést v rámci transakce inicializovány <xref:System.Activities.Statements.TransactionScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="95ed7-111">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =   
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
```  
  
<span data-ttu-id="95ed7-112">Další informace najdete v tématu o použití <xref:System.ServiceModel.Activities.TransactedReceiveScope>, naleznete v tématu [tok transakcí do a ze služby pracovních postupů](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="95ed7-112">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ed7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95ed7-113">See also</span></span>
- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
