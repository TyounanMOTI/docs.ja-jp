---
title: '&lt;serviceActivations&gt; の &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 1a25ad517e26e037c588bb14844e38147e251d96
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745826"
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a>&lt;serviceActivations&gt; の &lt;add&gt;
Windows Communication Foundation (WCF) サービスの型にマップする仮想サービス アクティベーション設定を定義できる構成要素。 これにより、.svc ファイルを使用せずに、WAS/IIS でホストされているサービスをアクティブ化できます。  
  
 \<system.ServiceModel >  
\<ServiceHostingEnvironment >  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|factory|サービス アクティベーション要素を生成するファクトリの CLR 型名を指定する文字列。|  
|service|サービスを実装する ServiceType (完全修飾 Typename または省略形の Typename (App_Code フォルダーに配置されている場合))。|  
|relativeAddress|現在の IIS アプリケーション内の相対アドレス (たとえば "Service.svc")。 WCF 4.0 ではこの相対アドレスが 1 個の既知のファイル拡張子 (.svc、.xamlx など) を含む必要があります。relativeUrl 用の物理ファイルは必要ありません。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ServiceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|アクティベーション設定を記述する構成セクション。|  
  
## <a name="remarks"></a>コメント  
 web.config ファイルでアクティベーション設定を構成する方法を次の例に示します。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 この構成を使用して、.svc ファイルを使用せずに、GreetingService をアクティブ化できます。  
  
 `<serviceHostingEnvironment>` はアプリケーション レベルの構成であることに注意してください。 構成を格納した `web.config` は、仮想アプリケーションのルートの下に配置する必要があります。 また、`serviceHostingEnvironment` は machinetoApplication の継承可能なセクションです。 コンピューターのルートに単一のサービスを登録すると、アプリケーションの各サービスはこのサービスを継承します。  
  
 構成ベースのアクティベーションは、http および非 http プロトコル経由のアクティベーションをサポートします。 relatativeAddress では、.svc、.xoml、.xamlx などの拡張子が必要です。 既知の buildProviders に対して独自の拡張子をマップできます。これにより、任意の拡張子を使用してサービスをアクティブ化できるようになります。 競合が発生した場合には、`<serviceActivations>` セクションにより、.svc の登録がオーバーライドされます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
