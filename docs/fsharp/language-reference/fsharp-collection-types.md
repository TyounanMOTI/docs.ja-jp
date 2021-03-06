---
title: F# コレクション型
description: F# コレクション型と .NET Framework のコレクション型との違いについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: a3cfc3f06582c31a79dce43b583eca39f69ddf1e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864762"
---
# <a name="f-collection-types"></a>F# コレクション型

このトピックを確認するには、f# コレクション型ベストな特定のニーズを特定できます。 など、.NET Framework のコレクション型からこれらのコレクション型とは異なる、`System.Collections.Generic`名前空間には、その f# コレクション型が、オブジェクト指向の観点ではなく、関数型プログラミングの観点から設計されています。 具体的には、配列のコレクションのみでは、変更可能な要素があります。 そのため、コレクションを変更するときに、元のコレクションを変更することではなく、変更されたコレクションのインスタンスを作成します。

コレクション型では、オブジェクトが格納されているデータ構造の種類の点が異なります。 ハッシュ テーブル、リンク リスト、配列などのデータ構造は、さまざまなパフォーマンス特性と使用可能な操作のさまざまなセットがあります。

## <a name="f-collection-types"></a>F# コレクション型

F# コレクション型を次の表に示します。

|型|説明|関連リンク|
|----|-----------|-------------|
|[List](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|同じ型の要素の順序付けられた、変更できないシリーズ。 リンク リストとして実装されます。|[リスト](lists.md)<br /><br />[List モジュール](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[配列](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|すべて、同じ型の一連のデータ要素の固定サイズ、0 から始まる、変更可能なコレクション。|[配列](arrays.md)<br /><br />[Array モジュール](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Array2D モジュール](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Array3D モジュール](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[seq](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|論理的な一連の要素をすべて 1 つの型。 シーケンスは、大規模な順序付けられたデータのコレクションを持っていても、すべての要素を使用すると必ずしも期待しない場合に特に便利です。 シーケンスの個々 の要素としてのみ計算されます必要なため、すべての要素が使用されていない場合にリストよりも優れたシーケンスを実行できます。 シーケンスがによって表される、`seq<'T>`エイリアスである型の`IEnumerable<T>`します。 そのため、実装する .NET Framework 型`System.Collections.Generic.IEnumerable<'T>`シーケンスとして使用できます。|[シーケンス](sequences.md)<br /><br />[Seq モジュール](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[マップ](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|要素の変更できないディクショナリ。 要素にはキーにアクセスします。|[Map モジュール](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[Set](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|比較は f# 構造比較関数の実装を使用する可能性のある、バイナリ ツリーに基づく変更できないセットを`System.IComparable`インターフェイス キーの値にします。|[モジュールの設定](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>関数のテーブル

このセクションでは、f# コレクション型で使用できる関数を比較します。 N が、最初のコレクションのサイズ、M は、存在する場合に 2 つ目のコレクションのサイズは、関数の計算の複雑さが与えられます。 ダッシュ (-) では、この関数は、コレクションで使用できることを示します。 シーケンスは遅延評価されるので、Seq.distinct などの機能をことがあります o (1)、すぐに返すためにまだ列挙されたときに、シーケンスのパフォーマンスに影響します。

|関数|配列|リスト|シーケンス|マップ|設定|説明|
|--------|-----|----|--------|---|---|-----------|
|append|O(M)|O (N)|O (N)|-|-|最初の 2 番目のコレクションの要素の後にコレクションの要素を含む新しいコレクションを返します。|
|追加|-|-|-|O (log N)|O (log N)|要素が追加された新しいコレクションを返します。|
|平均|O (N)|O (N)|O (N)|-|-|コレクション内の要素の平均を返します。|
|averageBy|O (N)|O (N)|O (N)|-|-|各要素に適用される指定された関数の結果の平均を返します。|
|blit|O (N)|-|-|-|-|配列のセクションをコピーします。|
|キャッシュ|-|-|O (N)|-|-|計算し、シーケンスの要素を格納します。|
|cast|-|-|O (N)|-|-|要素を指定した型に変換します。|
|選択|O (N)|O (N)|O (N)|-|-|指定された関数を適用`f`各要素に`x`の一覧。 関数が返す各要素の結果を含むリストを返します`Some(f(x))`します。|
|収集|O (N)|O (N)|O (N)|-|-|コレクションの各要素に指定された関数を適用、すべての結果を連結し、結合リストを返します。|
|compareWith|-|-|O (N)|-|-|要素によって指定された比較関数を使用して、2 つのシーケンスを比較します。|
|concat|O (N)|O (N)|O (N)|-|-|1 つの連結された列挙体として指定された列挙の列挙を組み合わせたものです。|
|次の値を含む|-|-|-|-|O (log N)|指定した要素がセットに含まれている場合に true を返します。|
|containsKey|-|-|-|O (log N)|-|マップのドメイン内の要素があるかどうかをテストします。|
|count|-|-|-|-|O (N)|セット内の要素数を返します。|
|countBy|-|-|O (N)|-|-|シーケンスの各要素にキー生成関数を適用し、一意のキーと元のシーケンス内の要素の数を生成するシーケンスを返します。|
|copy|O (N)|-|O (N)|-|-|コレクションをコピーします。|
|作成|O (N)|-|-|-|-|指定された値ではすべて、最初に全体の要素の配列を作成します。|
|遅延|-|-|O(1)|-|-|シーケンスの指定された遅延指定から作成されたシーケンスを返します。|
|相違点|-|-|-|-|O (M &#42; log N)|最初のセットから削除する 2 番目のセットの要素を含む新しいセットを返します。|
|Distinct|||O (1)&AMP;#42;|||エントリの汎用ハッシュと等値比較に従って、重複するエントリを含まないシーケンスを返します。 要素の順序で複数回が発生した場合は、2 回目以降は破棄されます。|
|distinctBy|||O (1)&AMP;#42;|||特定のキー生成関数によって返されるキーに基づいて汎用ハッシュと等値比較に従って、重複するエントリを含まないシーケンスを返します。 要素の順序で複数回が発生した場合は、2 回目以降は破棄されます。|
|(なし)|O(1)|O(1)|O(1)|O(1)|O(1)|空のコレクションを作成します。|
|exists|O (N)|O (N)|O (N)|O (log N)|O (log N)|シーケンスの任意の要素が、指定された述語を満たすかどうかをテストします。|
|exists2|O(min(N,M))|-|O(min(N,M))|||入力シーケンスの対応する要素のペアが、指定された述語を満たすかどうかをテストします。|
|fill|O (N)|||||配列の要素の範囲を指定した値に設定します。|
|フィルター|O (N)|O (N)|O (N)|O (N)|O (N)|指定された述語を返すコレクションの要素のみを含む新しいコレクションを返します`true`します。|
|find|O (N)|O (N)|O (N)|O (log N)|-|指定された関数を返す最初の要素を返します`true`します。 返します`System.Collections.Generic.KeyNotFoundException`そのような要素が存在しない場合。|
|findIndex|O (N)|O (N)|O (N)|-|-|指定の述語を満たす配列内の最初の要素のインデックスを返します。 発生させる`System.Collections.Generic.KeyNotFoundException`述語を満たす要素がない場合。|
|findKey|-|-|-|O (log N)|-|コレクション内の各マッピングに関数を評価し、関数が返す最初のマッピングのキーを返します`true`します。 この関数を発生させる場合、このような要素が存在しない`System.Collections.Generic.KeyNotFoundException`します。|
|フォールド|O (N)|O (N)|O (N)|O (N)|O (N)|計算にアキュムレータ引数をコレクションの各要素に関数を適用します。 入力関数が f 要素で... i0 場合は、この関数は計算 f (.(f s i0)...)でします。|
|fold2|O (N)|O (N)|-|-|-|関数は、計算にアキュムレータ引数を 2 つのコレクションの対応する要素を適用します。 コレクションは同じサイズである必要があります。 入力関数が f と要素のあるで... i0 j0... 場合 jN、この関数は f (. を計算します(f s i0 j0)...)jN. で|
|foldBack|O (N)|O (N)|-|O (N)|O (N)|計算にアキュムレータ引数をコレクションの各要素に関数を適用します。 この関数が (. f i0 を計算する場合は入力関数が f 要素で... i0、(...(f iN s))。|
|foldBack2|O (N)|O (N)|-|-|-|関数は、計算にアキュムレータ引数を 2 つのコレクションの対応する要素を適用します。 コレクションは同じサイズである必要があります。 JN、この関数が (. f i0 j0 を計算する場合、入力関数が f と要素のあるで... i0 j0...(...(f iN jN s))。|
|forall|O (N)|O (N)|O (N)|O (N)|O (N)|コレクションのすべての要素が、指定された述語を満たすかどうかをテストします。|
|forall2|O (N)|O (N)|O (N)|-|-|コレクションのすべての対応する要素はペアワイズ、指定された述語を満たすかどうかをテストします。|
|取得/n 番目|O(1)|O (N)|O (N)|-|-|指定されたインデックス コレクションから要素を返します。|
|head|-|O(1)|O(1)|-|-|コレクションの最初の要素を返します。|
|Init|O (N)|O (N)|O(1)|-|-|ディメンションと、要素を計算するジェネレーター関数を指定してコレクションを作成します。|
|initInfinite|-|-|O(1)|-|-|シーケンスを生成するには、反復処理される場合は、指定された関数を呼び出すことによって一連の要素を返します。|
|Intersect|-|-|-|-|O (log N&#42;ログ M)|2 つのセットの積集合を計算します。|
|intersectMany|-|-|-|-|O (N1 &AMP;#42; N2...)|セットのシーケンスの積集合を計算します。 シーケンスは空にできません。|
|IsEmpty|O(1)|O(1)|O(1)|O(1)|-|返します`true`コレクションが空の場合。|
|isProperSubset|-|-|-|-|O (M &#42; log N)|返します`true`最初のセットのすべての要素は、2 番目のセットと、2 番目のセットの少なくとも 1 つの要素が最初のセットに含まれていないかどうか。|
|isProperSuperset|-|-|-|-|O (M &#42; log N)|返します`true`2 番目のセットのすべての要素は、最初のセットと、最初のセットの少なくとも 1 つの要素が 2 番目のセットに含まれていないかどうか。|
|isSubset|-|-|-|-|O (M &#42; log N)|返します`true`最初のセットのすべての要素が 2 番目のセットにある場合。|
|isSuperset|-|-|-|-|O (M &#42; log N)|返します`true`2 番目のセットのすべての要素が最初のセットにある場合。|
|Iter|O (N)|O (N)|O (N)|O (N)|O (N)|指定された関数をコレクションの各要素に適用します。|
|iteri|O (N)|O (N)|O (N)|-|-|指定された関数をコレクションの各要素に適用します。 関数に渡される整数では、要素のインデックスを示します。|
|iteri2|O (N)|O (N)|-|-|-|一致する 2 つの配列インデックスから描画された要素のペアに指定された関数を適用します。 関数に渡される整数は、要素のインデックスを示します。 2 つの配列は、同じ長さである必要があります。|
|iter2|O (N)|O (N)|O (N)|-|-|一致する 2 つの配列インデックスから描画された要素のペアに指定された関数を適用します。 2 つの配列は、同じ長さである必要があります。|
|長さ|O(1)|O (N)|O (N)|-|-|コレクション内の要素の数を返します。|
|map|O (N)|O (N)|O(1)|-|-|要素は、配列の各要素に指定された関数を適用した結果のコレクションを作成します。|
|map2|O (N)|O (N)|O(1)|-|-|ペアワイズ 2 つのコレクションの対応する要素に指定された関数を適用した結果要素を含むコレクションを構築します。 2 つの入力配列は、同じ長さである必要があります。|
|map3|-|O (N)|-|-|-|要素が同時に 3 つのコレクションの対応する要素に指定された関数を適用した結果のコレクションを作成します。|
|mapi|O (N)|O (N)|O (N)|-|-|要素は、配列の各要素に指定された関数を適用した結果配列を構築します。 関数に渡される整数インデックスは、変換する要素のインデックスを示します。|
|mapi2|O (N)|O (N)|-|-|-|要素が 2 つのコレクションの要素のインデックスを渡すことも、ペアワイズの対応する要素に指定された関数を適用した結果のコレクションを作成します。 2 つの入力配列は、同じ長さである必要があります。|
|max|O (N)|O (N)|O (N)|-|-|比較を使用して、コレクションの最大の要素を返します、 [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce)演算子。|
|maxBy|O (N)|O (N)|O (N)|-|-|比較を使用して、コレクションの最大の要素を返します[max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce)関数の結果にします。|
|maxElement|-|-|-|-|O (log N)|セットに使用される順序に従って、セットの最大の要素を返します。|
|分|O (N)|O (N)|O (N)|-|-|比較を使用して、コレクションの最小の要素を返します、 [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed)演算子。|
|minBy|O (N)|O (N)|O (N)|-|-|比較を使用して、コレクションの最小の要素を返します、 [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed)演算子、関数の結果にします。|
|minElement|-|-|-|-|O (log N)|セットに使用される順序に従って、セットの最小の要素を返します。|
|ofArray|-|O (N)|O(1)|O (N)|O (N)|指定された配列と同じ要素を含むコレクションを作成します。|
|ofList|O (N)|-|O(1)|O (N)|O (N)|指定されたリストと同じ要素を含むコレクションを作成します。|
|ofSeq|O (N)|O (N)|-|O (N)|O (N)|指定されたシーケンスと同じ要素を含むコレクションを作成します。|
|ペアワイズ|-|-|O (N)|-|-|入力シーケンスとその前身である 2 番目の要素の先行タスクとしてのみが返されますの最初の要素を除く各要素のシーケンスを返します。|
|partition|O (N)|O (N)|-|O (N)|O (N)|2 つのコレクションにコレクションを分割します。 最初のコレクションが、指定された述語を返す要素が含まれています`true`、2 番目のコレクションが、指定された述語を返す要素が含まれている`false`します。|
|permute|O (N)|O (N)|-|-|-|置換を指定された置換に従ってすべての要素の配列を返します。|
|選択|O (N)|O (N)|O (N)|O (log N)|-|最初の結果を返す関数が返すいくつかの連続する要素に指定された関数を適用します。 関数がない、いくつかを返す場合`System.Collections.Generic.KeyNotFoundException`が発生します。|
|readonly|-|-|O (N)|-|-|指定したシーケンス オブジェクトにデリゲートするシーケンス オブジェクトを作成します。 この操作により、型キャストが再検出され、元のシーケンスを変更ことはできません。 たとえば、配列を指定した場合、返されたシーケンスは、配列の要素を返しますが、配列に返されたシーケンス オブジェクトをキャストすることはできません。|
|reduce|O (N)|O (N)|O (N)|-|-|計算にアキュムレータ引数をコレクションの各要素に関数を適用します。 この関数は、最初の 2 つの要素に関数を適用することで開始と 3 番目の要素と共に関数にこの結果を渡します。 関数は、最終的な結果を返します。|
|reduceBack|O (N)|O (N)|-|-|-|計算にアキュムレータ引数をコレクションの各要素に関数を適用します。 この関数が (. f i0 を計算する場合は入力関数が f 要素で... i0、(f in-1 iN))。|
|remove|-|-|-|O (log N)|O (log N)|マップのドメインから要素を削除します。 要素が存在しない場合、例外は発生しません。|
|レプリケートします。|-|O (N)|-|-|-|指定された値に設定するすべての要素で指定された長さの一覧を作成します。|
|rev|O (N)|O (N)|-|-|-|逆の順序で要素を持つ新しいリストを返します。|
|スキャン|O (N)|O (N)|O (N)|-|-|計算にアキュムレータ引数をコレクションの各要素に関数を適用します。 この操作では、2 番目の引数と、一覧の最初の要素に関数が適用されます。 その後、操作は、これに 2 番目の要素と共に関数にこの結果を渡します。 最後に、操作は、中間結果と最終結果の一覧を返します。|
|scanBack|O (N)|O (N)|-|-|-|FoldBack 操作に似ていますが、中間および最終結果の両方が返されます。|
|シングルトン|-|-|O(1)|-|O(1)|1 つだけの項目を生成するシーケンスを返します。|
|set|O(1)|-|-|-|-|配列の要素を指定した値に設定します。|
|スキップ|-|-|O (N)|-|-|基になるシーケンスの n 個の要素をスキップし、シーケンスの残りの要素を生成するシーケンスを返します。|
|SkipWhile|-|-|O (N)|-|-|反復処理されるときに、基になるシーケンスの要素がスキップされ、指定された述語を返しますと while、シーケンスを返します`true`シーケンスの残りの要素を生成します。|
|sort|平均の O (N log N)<br /><br />O(N^2) 最悪の場合|O (N log N)|O (N log N)|-|-|要素の値によって、コレクションを並べ替えます。 使用して要素を比較[比較](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)します。|
|sortBy|平均の O (N log N)<br /><br />O(N^2) 最悪の場合|O (N log N)|O (N log N)|-|-|指定されたプロジェクションを提供するキーを使用して、指定したリストを並べ替えます。 使用してキーの比較は[比較](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)します。|
|sortInPlace|平均の O (N log N)<br /><br />O(N^2) 最悪の場合|-|-|-|-|インプレースの変化し、指定された比較関数を使用して、配列の要素を並べ替えます。 使用して要素を比較する[比較](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)します。|
|sortInPlaceBy|平均の O (N log N)<br /><br />O(N^2) 最悪の場合|-|-|-|-|インプレースの変化をキーに指定されたプロジェクションを使用して、配列の要素を並べ替えます。 使用して要素を比較する[比較](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c)します。|
|sortInPlaceWith|平均の O (N log N)<br /><br />O(N^2) 最悪の場合|-|-|-|-|インプレースの変化の順序と指定された比較関数を使用して、配列の要素を並べ替えます。|
|sortWith|平均の O (N log N)<br /><br />O(N^2) 最悪の場合|O (N log N)|-|-|-|順序と指定された比較関数を使用して、新しいコレクションを返すと、コレクションの要素を並べ替えます。|
|sub|O (N)|-|-|-|-|開始インデックスと長さによって指定されている指定されたサブ範囲を含む配列を構築します。|
|sum|O (N)|O (N)|O (N)|-|-|コレクション内の要素の合計を返します。|
|sumBy|O (N)|O (N)|O (N)|-|-|コレクションの各要素に関数を適用することによって生成される結果の合計を返します。|
|末尾|-|O(1)|-|-|-|その最初の要素を除いたリストを返します。|
|Take|-|-|O (N)|-|-|指定された回数までのシーケンスの要素を返します。|
|TakeWhile|-|-|O(1)|-|-|反復処理されるときに、基になるシーケンスの要素が取得されますが、指定された述語を返しますを while、シーケンスを返します`true`しない複数の要素を返します。|
|ToArray|-|O (N)|O (N)|O (N)|O (N)|指定されたコレクションから配列を作成します。|
|ToList|O (N)|-|O (N)|O (N)|O (N)|指定されたコレクションからリストを作成します。|
|toSeq|O(1)|O(1)|-|O(1)|O(1)|指定されたコレクションからシーケンスを作成します。|
|truncate|-|-|O(1)|-|-|列挙を返します個以下の n 個の要素は、シーケンスを返します。|
|tryFind|O (N)|O (N)|O (N)|O (log N)|-|指定の述語を満たす要素を検索します。|
|tryFindIndex|O (N)|O (N)|O (N)|-|-|指定された述語を満たすし、一致する要素のインデックスを返しますの最初の要素を検索または`None`そのような要素が存在しない場合。|
|tryFindKey|-|-|-|O (log N)|-|指定の述語を満たすまたは取得するコレクション内の最初のマッピングのキーを返します`None`そのような要素が存在しない場合。|
|tryPick|O (N)|O (N)|O (N)|O (log N)|-|関数が返す最初の結果を返す一連の要素に指定された関数を適用`Some`のいくつかの値。 このような要素が存在しないかどうか、操作によって返される`None`します。|
|展開します。|-|-|O (N)|-|-|指定された計算を生成する要素を含むシーケンスを返します。|
|union|-|-|-|-|O (M &#42; log N)|2 つのセットの和集合を計算します。|
|unionMany|-|-|-|-|O (N1 &AMP;#42; N2...)|セットのシーケンスの和集合を計算します。|
|unzip|O (N)|O (N)|O (N)|-|-|2 つのリストには、ペアのリストを分割します。|
|unzip3|O (N)|O (N)|O (N)|-|-|3 要素の一覧を次の 3 つのリストに分割します。|
|ウィンドウ|-|-|O (N)|-|-|入力シーケンスから要素を含むのスライディング ウィンドウを生成するシーケンスを返します。 各ウィンドウは、新しい配列として返されます。|
|zip|O (N)|O (N)|O (N)|-|-|ペアのリストに 2 つのコレクションを結合します。 2 つのリストは、同じ長さである必要があります。|
|zip3|O (N)|O (N)|O (N)|-|-|3 要素のリストに 3 つのコレクションを結合します。 リストは、同じ長さである必要があります。|

## <a name="see-also"></a>関連項目

- [F# の型](fsharp-types.md)
- [F# 言語リファレンス](index.md)
