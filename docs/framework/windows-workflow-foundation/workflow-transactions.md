---
title: ワークフロー トランザクション
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: e2a0c301abac562904e976fe09e5a68697b191e5
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779960"
---
# <a name="workflow-transactions"></a>ワークフロー トランザクション

[!INCLUDE[wf1](../../../includes/wf1-md.md)] は、<xref:System.Transactions> アクティビティを使用してトランザクション済み作業単位のスコープを設定することで、<xref:System.Activities.Statements.TransactionScope> トランザクションへの参加をサポートします。 <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> は明示的に完了する必要がありますが、<xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> アクティビティは正常完了時にトランザクション上で暗黙的に完了を呼び出します。 <xref:System.Activities.Statements.TransactionScope.Body%2A> アクティビティの <xref:System.Activities.Statements.TransactionScope> に含まれるすべてのアクティビティは、トランザクションに参加します。 WF は、<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを使用してワークフローにトランザクションをフローできます。 <xref:System.Activities.Statements.TransactionScope> アクティビティと同様に、<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> に含まれるすべてのアクティビティはトランザクションに参加します。 WF は、<xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> に依存するアクティビティが、<xref:System.Activities.Statements.TransactionScope> と <xref:System.ServiceModel.Activities.TransactedReceiveScope> の両方で確実に動作するようにします。 システム標準アクティビティがすべての要件を満たさない場合、高度なフロー シナリオやトランザクション制御シナリオを可能にするには、<xref:System.Activities.RuntimeTransactionHandle> を使用してカスタム アクティビティを構築します。  
  
構成でワークフローを作成、次の例では、<xref:System.Activities.Statements.Sequence>アクティビティを含む子アクティビティを含む、<xref:System.Activities.Statements.TransactionScope>アクティビティ。 <xref:System.Activities.Statements.TransactionScope.Body%2A> の <xref:System.Activities.Statements.TransactionScope> アクティビティは、<xref:System.Activities.Statements.TransactionScope> アクティビティにより初期化されるトランザクションの下で実行されます。  
  
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
  
詳細については、使用方法を参照してください<xref:System.ServiceModel.Activities.TransactedReceiveScope>を参照してください[ワークフロー サービスとの間にトランザクションをフロー](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Activities.Statements.TransactionScope>  
 <xref:System.Transactions.TransactionScope>  
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
