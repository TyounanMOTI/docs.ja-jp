---
title: SQL Server の CLR 統合セキュリティ
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 953982045574cc62b1da46c5d763693b9d9d89ff
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516194"
---
# <a name="clr-integration-security-in-sql-server"></a>SQL Server の CLR 統合セキュリティ
Microsoft SQL Server で新たに導入された機能の 1 つに、.NET Framework の共通言語ランタイム (CLR) コンポーネントの統合があります。 CLR の統合により、Microsoft Visual Basic .NET や Microsoft Visual C# を含む任意の .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数、ユーザー定義集計、およびストリーミング テーブル値関数を作成できるようになりました。  
  
 CLR は、コード アクセス セキュリティ (CAS) と呼ばれるマネージ コード用のセキュリティ モデルをサポートしています。 このモデルでは、コードのメタデータに指定された証拠に基づいてアセンブリに権限が付与されます。 SQL Server のユーザーベースのセキュリティ モデルは、SQL Server により CLR のコード アクセスベースのセキュリティ モデルと統合されます。  
  
## <a name="external-resources"></a>外部リソース  
 SQL Server と CLR の統合の詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|[コード アクセス セキュリティ](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)|.NET Framework の CAS について説明します。|  
|[CLR 統合のセキュリティ](https://go.microsoft.com/fwlink/?LinkId=59998)|SQL Server の内部で実行されるマネージド コードのセキュリティ モデルについて説明します。|  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET アプリケーションのセキュリティ保護](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server におけるアプリケーション セキュリティのシナリオ](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server の共通言語ランタイム統合](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
