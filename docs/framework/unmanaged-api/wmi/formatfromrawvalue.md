---
title: FormatFromRawValue 関数 (アンマネージ API リファレンス)
description: FormatFromRawValue 関数では、生のパフォーマンス データを指定された形式に変換します。
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95ef445d41672c5c2895bd7115afb6a73a57e8f9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086138"
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue 関数
1 つの生のパフォーマンス データ値が指定した形式に変換されます。この形式変換が時間ベースである場合は、2 つの生のパフォーマンス データ値が変換されます。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```  

## <a name="parameters"></a>パラメーター

`dwCounterType`  
[in]カウンターの型。 カウンターの種類の一覧は、次を参照してください。 [WMI パフォーマンス カウンターの種類](/windows/desktop/WmiSdk/wmi-performance-counter-types)します。 `dwCounterType` 以外の任意のカウンター タイプ`PERF_LARGE_RAW_FRACTION`と`PERF_LARGE_RAW_BASE`します。 

`dwFormat`  
[in]生のパフォーマンス データを変換先の形式。 次の値のいずれかを指定できます。

|定数  |値  |説明 |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | 倍精度浮動小数点値として計算される値を返します。 | 
| `PDH_FMT_LARGE` | 0x00000400 | 計算される値を 64 ビット整数として返します。 |
| `PDH_FMT_LONG` | 0x00000100 | 計算される値を 32 ビット整数として返します。 |

次のスケーリング フラグのいずれかの論理和前の値のいずれかのことができます。

|定数  |値  |説明 |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | カウンターのスケール ファクターは適用されません。 |
| `PDH_FMT_1000` | 0x00002000 | 1000 で最終的な値を乗算します。 | 

`pTimeBase`  
[in]形式の変換に必要な場合、時間ベースへのポインター。 時間ベースの情報は、形式変換の必要はありません、このパラメーターの値は無視されます。

`pRawValue1` [in]ポインターを[ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx)生のパフォーマンス値を表す構造体です。

`pRawValue2` [in]ポインターを[ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) 2 番目の生のパフォーマンス値を表す構造体です。 2 番目の生のパフォーマンス値が必要でない場合、このパラメーターがあります`null`します。

`pFmtValue` [out]ポインターを[ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx)を書式設定されたパフォーマンスの値を受け取る構造体。

## <a name="return-value"></a>戻り値

この関数では、次の値が返されます。

|定数  |値  |説明  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | 関数呼び出しは成功します。 |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | 必須の引数が不足しているか、正しくありません。 | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | ハンドルが有効な PDH オブジェクトです。 |
  
## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx)関数。

## <a name="requirements"></a>要件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ライブラリ:** どちら  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
