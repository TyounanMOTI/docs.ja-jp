---
title: -bugreport (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 6e4674acd2a5edbbffd2babf130d2078019ab9b7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517004"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (C# コンパイラ オプション)
後で分析を実行できるように、デバッグ情報をファイルに出力するよう指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>引数  
 `file`  
 バグ レポートを作成するファイルの名前。  
  
## <a name="remarks"></a>コメント  
 **-bugreport** オプションを指定すると、次の情報が `file` に出力されます。  
  
-   コンパイルのすべてのソース コード ファイルのコピー。  
  
-   コンパイルで使用されたコンパイラ オプションの一覧。  
  
-   コンパイラ、ランタイム、およびオペレーティング システムのバージョン情報。  
  
-   16 進数として保存された参照アセンブリとモジュール (.NET Framework (SDK を含む) に付属のアセンブリを除く)。  
  
-   コンパイラの出力 (指定されている場合)。  
  
-   問題点の説明。プロンプトが表示されます。  
  
-   問題点の修正方法の説明。プロンプトが表示されます。  
  
 このオプションに **-errorreport:prompt** または **-errorreport:send** を指定すると、ファイルに保存される情報が Microsoft Corporation に送信されます。  
  
 すべてのソース コード ファイルのコピーが `file` に出力されるため、問題があると思われるコードは、できるだけ小さなプログラムで再生成することをお勧めします。  
  
 このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。  
  
 生成されたファイルの内容によってソース コードが公開され、意図しない情報開示につながる場合があることに注意してください。  
  
## <a name="see-also"></a>参照  

- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
- [-errorreport (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)  
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
