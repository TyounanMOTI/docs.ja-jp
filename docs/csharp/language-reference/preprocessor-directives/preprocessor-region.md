---
title: '#region (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 3edc4fe757ab1f5cbf42e67ab74cd8032a82d853
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518279"
---
# <a name="region-c-reference"></a>#region (C# リファレンス)
`#region` を使用すると、コード ブロックを指定できます。このブロックは、Visual Studio コード エディターの[アウトライン](/visualstudio/ide/outlining)機能を使用して展開や折りたたみを行うことができます。 コード ファイルが長い場合は、現在操作している部分に集中できるように 1 つ以上の領域を折りたたむ (非表示にする) ことができると便利です。 次の例では、領域を定義する方法を示します。  
  
```csharp
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a>コメント  
 `#region` ブロックは、[#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) ディレクティブで終了させる必要があります。  
  
 `#region` ブロックは、[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ブロックと重複することはできません。 ただし、`#region` ブロックを `#if` ブロック内に入れ子にしたり、`#if` ブロックを `#region` ブロック内に入れ子にしたりすることはできます。  
  
## <a name="see-also"></a>参照

- [C# リファレンス](../../../csharp/language-reference/index.md)  
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
- [C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)
