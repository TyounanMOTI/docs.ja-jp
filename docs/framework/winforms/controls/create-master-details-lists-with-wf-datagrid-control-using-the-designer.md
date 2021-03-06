---
title: '方法 : デザイナーで Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: aec02e38fbe80302108397543144b1cc9c3ea346
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266788"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>方法 : デザイナーで Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 場合、<xref:System.Data.DataSet>は一連の関連テーブルの 2 つ使用できます<xref:System.Windows.Forms.DataGrid>マスター/詳細形式でデータを表示するコントロール。 1 つ<xref:System.Windows.Forms.DataGrid>マスター グリッドに指定し、2 つ目は詳細グリッドに指定します。 マスター リストのエントリを選択すると、すべての関連する子エントリ、詳細の一覧に表示されます。 たとえば場合、 <xref:System.Data.DataSet> Customers テーブルと関連する Orders テーブルを含むマスター グリッドに Customers テーブルと Orders テーブル詳細グリッドに指定します。 マスター グリッドから顧客を選択すると、すべての Orders テーブルでは、その顧客に関連付けられている注文の詳細グリッドで表示されます。  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクト (**ファイル** > **新規** > **プロジェクト** >  **Visual c#** または**Visual Basic** > **クラシック デスクトップ** > **Windows フォームアプリケーション**)。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a>デザイナーでマスター/詳細リストを作成するには  
  
1.  2 つ追加<xref:System.Windows.Forms.DataGrid>フォームのコントロール。 詳細については、次を参照してください。[方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)します。 Visual Studio 2005 で、<xref:System.Windows.Forms.DataGrid>制御されていない、**ツールボックス**既定。 詳細については、次を参照してください。[方法: ツールボックス アイテムの追加](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0)します。  
  
    > [!NOTE]
    >  次の手順は Visual Studio 2005 では、使用に適用されない、**データ ソース**デザイン時のデータ バインディングのウィンドウ。 詳細については、次を参照してください。 [Visual Studio でのデータ コントロールをバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)と[方法: Windows フォーム アプリケーションで関連データを表示](https://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)します。  
  
2.  2 つ以上のテーブルをドラッグして**サーバー エクスプ ローラー**をフォームにします。  
  
3.  **データ**メニューの **データセットの生成**します。  
  
4.  XML デザイナーを使用してテーブル間のリレーションシップを設定します。 詳細については、次を参照してください。"する方法: 一対多を作成する XML スキーマおよびデータセットでリレーションシップ"msdn です。  
  
5.  選択して、リレーションシップを保存**すべて保存**から、**ファイル**メニュー。  
  
6.  構成、<xref:System.Windows.Forms.DataGrid>マスター グリッドを次のように指定するコントロール。  
  
    1.  選択、<xref:System.Data.DataSet>でドロップダウン リストから、<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティ。  
  
    2.  マスター テーブル (たとえば、"Customers") でドロップダウン リストから選択、<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティ。  
  
7.  構成、<xref:System.Windows.Forms.DataGrid>詳細グリッドを次のように指定するコントロール。  
  
    1.  選択、<xref:System.Data.DataSet>でドロップダウン リストから、<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティ。  
  
    2.  ドロップダウン リストからマスター/詳細テーブル間のリレーションシップ (たとえば、"Customers.CustOrd") を選択して、<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティ。 リレーションシップを表示するには、プラス記号をクリックして、ノードを展開します (**+**) ドロップダウン リストのマスター テーブルの横にサインオンします。  
  
## <a name="see-also"></a>関連項目  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [DataGrid コントロールの概要](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [方法: データ ソースに Windows フォーム DataGrid コントロールをバインドする](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Visual Studio でのデータへのコントロールのバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
