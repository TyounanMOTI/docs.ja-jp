---
title: '&lt;wsDualHttpBinding&gt; の &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
author: BrucePerlerMS
ms.openlocfilehash: 761eb9d111630d64d0fe4450c7a8950a8181366d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2018
ms.locfileid: "48776540"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a>&lt;wsDualHttpBinding&gt; の &lt;security&gt;
セキュリティ機能を定義、 [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)します。  
  
 \<system.ServiceModel >  
\<bindings>  
\<wsDualHttpBinding >  
\<binding>  
\<セキュリティ >  
  
## <a name="syntax"></a>構文  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|モード|-省略可能。 適用するセキュリティの種類を指定します。 既定値は `Message` です。 この属性は <xref:System.ServiceModel.WSDualHttpSecurityMode> 型です。|  
  
## <a name="mode-attribute"></a>Mode 属性  
  
|値|説明|  
|-----------|-----------------|  
|なし|セキュリティを無効にします。|  
|メッセージ|セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|メッセージ レベル セキュリティの設定を定義します。 この要素は <xref:System.ServiceModel.MessageSecurityOverHttp> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|すべてのバインド機能を定義、 [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)します。|  
  
## <a name="remarks"></a>Remarks  
 二重バインディングでは、クライアントの IP アドレスをサービスに公開します。 クライアントは、セキュリティを使用して信頼するサービスに対して接続のみを可能にする必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [サービスとクライアントを構成するためのバインディングの使用](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<binding>](../../../../../docs/framework/misc/binding.md)
