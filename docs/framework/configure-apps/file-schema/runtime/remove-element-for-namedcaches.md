---
title: '&lt;削除&gt;要素&lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f885416629ae58949cc688f4e6fbd41e77e872aa
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2018
ms.locfileid: "48781675"
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a>&lt;削除&gt;要素&lt;namedCaches&gt;
名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches >  
\<remove>  
  
## <a name="syntax"></a>構文  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>型  
 `None`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 `None`  
  
### <a name="child-elements"></a>子要素  
 `None`  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|名前付きの構成設定のコレクションを含む<xref:System.Runtime.Caching.MemoryCache>インスタンス。|  
  
## <a name="remarks"></a>Remarks  
 `remove`要素は、削除、`namedCache`メモリ キャッシュの名前付きキャッシュのコレクションからエントリ。  
  
## <a name="see-also"></a>関連項目  
 [\<namedCaches > 要素 (キャッシュ設定)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
