---
title: DataReader の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 1ede51ed9119051a647fd27d8d02cd2c93e61bbb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510038"
---
# <a name="creating-a-datareader"></a>DataReader の作成
<xref:System.Data.DataTable> クラスおよび <xref:System.Data.DataSet> クラスには、<xref:System.Data.DataTable.CreateDataReader%2A> の内容または <xref:System.Data.DataTable> オブジェクトの <xref:System.Data.DataSet> コレクションの内容を、読み取り専用で前方参照専用の 1 つ以上の結果セットとして返す <xref:System.Data.DataSet.Tables%2A> メソッドがあります。  
  
## <a name="example"></a>例  
 <xref:System.Data.DataTable> インスタンスを作成するコンソール アプリケーションの例を次に示します。 例は、塗りつぶされた<xref:System.Data.DataTable>を呼び出すプロシージャに、<xref:System.Data.DataTable.CreateDataReader%2A>内に含まれる結果を反復処理するメソッド、<xref:System.Data.DataTableReader>します。  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 この例では、次の出力がコンソール ウィンドウに表示されます。  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
