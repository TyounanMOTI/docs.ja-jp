---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 1611183dc02e46ea6d5fbb53c26500be3ed93d0d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483951"
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
PresentationHost.exe が、ホスト アプリケーションに必要な未加工入力デバイス (ヒューマン インターフェイス デバイス) を検出できるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
  
 [out]ポインター、 [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md)未加工入力デバイスを列挙するためです。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 HRESULT:  
  
 S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) S_OK が返された場合のみ PresentationHost.exe によってに使用されます。  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>Remarks  
 未加工入力デバイスは、キーボード、マウス、およびリモート コントロールのような比較的新しいデバイスを含む入力デバイスのセットです。  
  
 未加工の入力デバイスの一覧を取得すると、PresentationHost.exe は WM_INPUT 通知メッセージを受信するデバイスを登録します。  
  
## <a name="see-also"></a>関連項目  
 [http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
