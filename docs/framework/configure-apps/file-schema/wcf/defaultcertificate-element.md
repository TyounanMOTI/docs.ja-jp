---
title: '&lt;defaultCertificate&gt; 要素'
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: a4af1c6ec452b24634fa50162fa71f069e2451f5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751013"
---
# <a name="ltdefaultcertificategt-element"></a>&lt;defaultCertificate&gt; 要素
ネゴシエーション プロトコル経由でサービスまたは STS が証明書を提供しないときに使用される X.509 証明書を指定します。  
  
 \<system.ServiceModel >  
\<ビヘイビアー >  
endpointBehaviors セクション  
\<behavior>  
\<clientCredentials>  
\<serviceCertificate >  
\<defaultCertificate >  
  
## <a name="syntax"></a>構文  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|findValue|文字列。 検索対象の値。|  
|x509FindType|列挙値。 検索する証明書フィールドのいずれかです。|  
|storeLocation|列挙値。 検索する 2 つのシステム格納場所のいずれかです。|  
|storeName|列挙値。 検索するシステム ストアのいずれかです。|  
  
## <a name="findvalue-attribute"></a>findValue 属性  
  
|値|説明|  
|-----------|-----------------|  
|String|値は、検索されるフィールド (X509FindType 属性により指定される) によって異なります。 たとえば、サムプリント検索する場合、値は 16 進数の文字列にする必要があります。|  
  
## <a name="x509findtype-attribute"></a>x509FindType 属性  
  
|値|説明|  
|-----------|-----------------|  
|列挙型|値は、FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage、FindBySubjectKeyIdentifier です。|  
  
## <a name="storelocation-attribute"></a>storeLocation 属性  
  
|値|説明|  
|-----------|-----------------|  
|列挙型|CurrentUser または LocalMachine です。|  
  
## <a name="storename-attribute"></a>storeName 属性  
  
|値|説明|  
|-----------|-----------------|  
|列挙型|値は、AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople、および TrustedPublisher です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|クライアントに対してサービスを認証する際に使用される証明書を指定します。|  
  
## <a name="remarks"></a>コメント  
 証明書ベースのメッセージ セキュリティを使用するバインディングでは、この構成要素で指定された証明書を使用して、サービスへのメッセージが暗号化されます。この証明書は、サービスがクライアントへの応答に署名するためにも使用されます。 この要素には、サービスで証明書が指定されていないときに使用する証明書を 1 つ格納できます。  
  
## <a name="example"></a>例  
 次の例の URI がで始まるエンドポイントを使用する証明書を指定するhttp://www.contoso.comと、証明書を証明書ネゴシエーションを実行しないその他のすべてのエンドポイントを使用します。  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [\<authentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
