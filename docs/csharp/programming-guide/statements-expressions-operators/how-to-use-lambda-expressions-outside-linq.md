---
title: '方法: LINQ 以外でラムダ式を使用する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: 6ba6c6f50b4d2f717de4325b5cd21434066b2899
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2018
ms.locfileid: "43389185"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>方法: LINQ 以外でラムダ式を使用する (C# プログラミング ガイド)
ラムダ式の使用は [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリに限定されているわけではありません。 デリゲート値が想定される場面、すなわち匿名メソッドを使用できる場面であれば、どこでもラムダ式を使用できます。 次の例では、Windows フォームのイベント ハンドラーでラムダ式を使用する方法を示します。 なお、入力 (<xref:System.Object> と <xref:System.Windows.Forms.MouseEventArgs>) の型はコンパイラによって推論されるため、ラムダ入力パラメーターで明示的に指定する必要がありません。  
  
## <a name="example"></a>例  
  
```  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [統合言語クエリ (LINQ)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
