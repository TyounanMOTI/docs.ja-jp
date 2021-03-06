---
title: '方法 : コントラクト インターフェイスを使用してサービスを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 796870b80ed72db2353e79db3e4e3fc164c22875
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489795"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>方法 : コントラクト インターフェイスを使用してサービスを作成する
インターフェイスを使用して、、Windows Communication Foundation (WCF) コントラクトを作成することをお勧めします。 このコントラクトでは、サービスが提供する操作にアクセスするために必要なメッセージのコレクションと構造を指定します。 このインターフェイスでは、インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用し、公開するメソッドに <xref:System.ServiceModel.OperationContractAttribute> クラスを適用して、入力と出力の種類を定義します。  
  
 サービス コントラクトの詳細については、次を参照してください。[サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)です。  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>インターフェイスを使用した WCF コントラクトの作成  
  
1.  Visual Basic、C# の場合、またはその他の共通言語ランタイム言語を使用して新しいインターフェイスを作成します。  
  
2.  インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。  
  
3.  インターフェイスのメソッドを定義します。  
  
4.  適用、<xref:System.ServiceModel.OperationContractAttribute>クラス、パブリックの WCF コントラクトの一部として公開する必要がある各メソッドにします。  
  
## <a name="example"></a>例  
 次のコード例は、サービス コントラクトを定義するインターフェイスを示しています。  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <xref:System.ServiceModel.OperationContractAttribute> クラスが適用されたメソッドは、既定で要求/応答メッセージ パターンを使用します。 このメッセージ パターンの詳細については、次を参照してください。[する方法: 要求/応答コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)です。 属性のプロパティを設定することにより、他のメッセージ パターンを作成および使用できるようになります。 例については、次を参照してください。[する方法: 一方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)と[する方法: 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
