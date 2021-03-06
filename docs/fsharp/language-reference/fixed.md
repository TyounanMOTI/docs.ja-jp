---
title: Fixed キーワード (f#)
description: F# を使用して、コレクションを回避するには、スタックにローカルがキーワードを 'fixed' することができます 'pin' 方法について説明します。
ms.date: 04/24/2017
ms.openlocfilehash: 1bf1b2ad67d2dd7f854e569cfca7c06e8aec7f4c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2018
ms.locfileid: "45624510"
---
# <a name="the-fixed-keyword"></a>固定キーワード

F# 4.1 が導入されています、`fixed`キーワードで、収集またはガベージ コレクション中に移動されないようにするには、スタックにローカルを「ピン留め」することができます。  低レベルのプログラミング シナリオに使用されます。

## <a name="syntax"></a>構文

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Remarks

これは、ポインターを抽出し、収集されたり、ガベージ コレクション中に移動できない名前にバインドすることを許可する式の構文を拡張します。  

使用して式からのポインターが固定されて、`fixed`キーワードは、識別子を使用してにバインドされて、`use`キーワード。  これのセマンティクスを使用したリソース管理に似ています、`use`キーワード。  ポインターは、スコープ内にあるし、修正が不要になったスコープ外に出ることが、中に固定されています。  `fixed` コンテキストの外部で使用することはできません、`use`バインドします。  名前に、ポインターをバインドする必要があります`use`します。

使用`fixed`関数またはメソッドの式内で発生する必要があります。  これは、スクリプト レベルまたはモジュール レベルのスコープで使用できません。

ポインターのすべてのコードのようにこれは安全でない機能で、使用時に警告が生成されます。

## <a name="example"></a>例

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>関連項目

- [NativePtr モジュール](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
