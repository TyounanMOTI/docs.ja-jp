---
title: '&lt;wsHttpContextBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1e40b5c9-0df2-4d66-afc5-a99d0e4ae7a4
ms.openlocfilehash: 0757d02845fa4eaf32c432dcc7b9f8fc18333e54
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2018
ms.locfileid: "48781058"
---
# <a name="ltwshttpcontextbindinggt"></a>&lt;wsHttpContextBinding&gt;
保護レベルの署名を要求する <xref:System.ServiceModel.WSHttpBinding> のコンテキストを提供します。  
  
\<system.serviceModel>  
\<bindings>  
\<wsHttpContextBinding>  
  
## <a name="syntax"></a>構文  
  
```xml
<wsHttpContextBinding>  
  <binding allowCookies="Boolean" 
           bypassProxyOnLocal="Boolean"  
           closeTimeout="TimeSpan" 
           contextProtectionLevel="EncryptAndSign/None/Sign" 
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard" 
           maxBufferPoolSize="integer" 
           maxReceivedMessageSize="Integer" 
           messageEncoding="Text/Mtom" 
           name="string" 
           openTimeout="TimeSpan" 
           proxyAddress="URI" 
           receiveTimeout="TimeSpan" 
           sendTimeout="TimeSpan" 
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
           transactionFlow="Boolean"  
           useDefaultWebProxy="Boolean">  
    <reliableSession ordered="Boolean"  
                     inactivityTimeout="TimeSpan"  
                     enabled="Boolean" />  
    <security mode="Message/None/Transport/TransportWithCredential">  
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                 realm="string"   
                 defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                 defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                 defaultRealm="string" />  
      <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
               establishSecurityContext="Boolean"   
               negotiateServiceCredential="Boolean" />  
    </security>  
    <readerQuotas maxArrayLength="Integer" 
                  maxBytesPerRead="Integer" 
                  maxDepth="Integer" 
                  maxNameTableCharCount="Integer" 
                  maxStringContentLength="Integer" />
  </binding>  
</wsHttpContextBinding>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|allowCookies|クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定するブール値です。 既定値は、`false` です。<br /><br /> `allowCookies` が `true` に設定されると、contextChannel は httpCookies をコンテキストの交換モードとして使用します。 この属性が `false` に設定されると、コンテキストは、SOAP ヘッダーとして交換されます。<br /><br /> 既定値は `false` です。<br /><br /> クッキーを使用する ASMX Web サービスと対話する場合にこのプロパティを使用できます。 この方法で、サーバーから返されるクッキーを、それ以降のサービスに対するすべてのクライアント要求に自動的にコピーできます。|  
|bypassProxyOnLocal|ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。 既定値は、`false` です。|  
|closeTimeout|クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|contextProtectionLevel|コンテキスト情報の反映に使用される SOAP ヘッダーの必要な保護レベルを指定する、有効な <xref:System.Net.Security.ProtectionLevel> 値。  既定値は `Sign` です。|  
|hostnameComparisonMode|URI の解析に使用する HTTP ホスト名比較モードを指定します。 この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。 既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。|  
|maxBufferPoolSize|このバインディングに使用するバッファー プール サイズの上限を指定する整数。 既定は 524,288 バイト (512 * 1024) です。 Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。 使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。 バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。 これで、バッファーの作成と破棄のオーバーヘッドを回避できます。|  
|maxReceivedMessageSize|このバインディングで構成されるチャネルで受信可能な最大メッセージ サイズ (ヘッダーを含む) をバイト単位で指定する正の整数。 この制限を超えるメッセージの送信者が、SOAP エラーを受信します。 メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。 既定値は 65536 です。|  
|messageEncoding|メッセージのエンコードに使用されるエンコーダーを定義します。 以下の値が有効です。<br /><br /> テキスト: は、テキスト メッセージ エンコーダーを使用します。<br />Mtom: Message Transmission 組織 Mechanism 1.0 (MTOM) エンコーダーを使用します。<br />-既定値はテキストです。<br /><br /> この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。|  
|name|バインディングの構成名を格納する文字列です。 この値は、バインディングの ID として使用されるため、一意にする必要があります。 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と無名のバインディングおよび動作の詳細については、「[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)」と「[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。|  
|openTimeout|実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|proxyAddress|HTTP プロキシのアドレスを指定する URI。 `useSystemWebProxy` が `true` の場合、この設定を `null` にする必要があります。 既定値は、`null` です。|  
|receiveTimeout|受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|sendTimeout|送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|textEncoding|バインドでメッセージの発行に使用される文字セット エンコーディングを指定します。 以下の値が有効です。<br /><br /> -UnicodeFffeTextEncoding: Unicode BigEndian エンコーディングします。<br />-Utf16TextEncoding: 16 ビット エンコーディング。<br />-Utf8TextEncoding: 8 ビット エンコーディング。<br /><br /> 既定値は Utf8TextEncoding です。<br /><br /> この属性は <xref:System.Text.Encoding> 型です。|  
|transactionFlow|バインディングが WS-Transactions のフローをサポートするかどうかを指定するブール値です。 既定値は、`false` です。|  
|useDefaultWebProxy|システムの自動設定 HTTP プロキシを使用するかどうかを指定するブール値。 既定値は `true` です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|バインディングのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> 型です。|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。 この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。|  
|[reliableSession](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|チャネルのエンドポイント間に信頼できるセッションを確立するかどうかを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<bindings>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.WSHttpContextBinding>  
 <xref:System.ServiceModel.Configuration.WSHttpContextBindingElement>  
 <xref:System.ServiceModel.Channels.ContextBindingElement>  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [サービスとクライアントを構成するためのバインディングの使用](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<binding>](../../../../../docs/framework/misc/binding.md)  
 [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
