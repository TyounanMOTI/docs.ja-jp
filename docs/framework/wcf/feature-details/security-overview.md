---
title: セキュリティ Overview1
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
author: BrucePerlerMS
ms.openlocfilehash: 54cb952e2f3bffc9c37f2d75059c931d78f29eee
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198866"
---
# <a name="security-overview"></a>セキュリティの概要
Windows Communication Foundation (WCF) は、SOAP メッセージに基づく分散プログラミングのプラットフォーム、およびクライアントとサービス間のメッセージをセキュリティで保護するはデータの保護に不可欠です。 WCF には、既存のセキュリティ インフラストラクチャと認識されているセキュリティ標準の SOAP メッセージの両方に基づき、セキュリティで保護されたメッセージを交換するための汎用的で相互運用可能なプラットフォームが用意されています。  
  
> [!NOTE]
>  WCF セキュリティの包括的なガイドを参照してください。 [WCF セキュリティ ガイダンス](https://go.microsoft.com/fwlink/?LinkID=158912)します。  
  
 WCF での概念が HTTPS では、Windows などの既存のテクノロジとセキュリティで保護された分散アプリケーションをビルドした場合によく使用するには、セキュリティ、またはユーザー名とユーザーを認証するパスワードが統合されています。 WCF だけでなくは、既存のセキュリティ インフラストラクチャと統合されていますが、セキュリティで保護された SOAP メッセージを使用して Windows 専用のドメインを超えて分散セキュリティも拡張できます。 WCF の既存のプロトコルに加えて、プロトコルとして SOAP を使用する大きな利点を既存のセキュリティ機構の実装を検討してください。 たとえば、ユーザー名とパスワードや X.509 証明書など、クライアントまたはサービスを識別する資格情報には、相互運用可能な XML ベースの SOAP プロファイルがあります。 このプロファイルを使用して、XML デジタル署名や XML 暗号化などの公開仕様を利用するセキュリティで保護されたメッセージ交換を行います。 仕様の一覧は、次を参照してください。[システム標準の相互運用性バインディングでサポートされる Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)します。  
  
 また他にも、Windows プラットフォームのコンポーネント オブジェクト モデル (COM) があり、セキュリティで保護された分散アプリケーションを実現します。 COM は、包括的なセキュリティ機構を有します。このセキュリティ機構により、セキュリティ コンテキストはコンポーネント間をフローできます。また、整合性、機密性、および認証を実現できます。 ただし COM はクロスプラット フォーム、WCF と同様のメッセージ セキュリティで保護を有効になりません。 WCF を使用して、Windows ドメインからインターネット経由で対象にするサービスとクライアントを構築できます。 WCF の相互運用可能なメッセージが動的に構築するために不可欠なビジネス中心のサービスを確信を持てる、情報のセキュリティ。  
  
## <a name="windows-communication-foundation-security-benefits"></a>Windows Communication Foundation セキュリティの利点  
 WCF は、SOAP メッセージに基づく分散プログラミングのプラットフォームです。 WCF を使用して、できる関数を作成するアプリケーションをサービスとサービス クライアントを作成して、無制限の数の他のサービスとクライアントからのメッセージの処理の両方として。 このような分散アプリケーションでは、メッセージをノード間でフローさせ、ファイアウォールを経由してインターネットに送信し、多くの SOAP 中継局を経由させることができます。 しかしこれは、さまざまなメッセージ セキュリティの脅威を招きます。 次の例は、WCF セキュリティのエンティティ間のメッセージを交換するときを緩和するのに役立ついくつかの一般的な脅威を示しています。  
  
-   機密情報を取得するネットワーク トラフィックの監視。 たとえば、オンライン バンキング シナリオを考えます。クライアントは口座間の資金の移動を要求します。 悪意のあるユーザーはメッセージを途中受信し、後で口座番号とパスワードを使用して、侵害した口座から資金を移動します。  
  
-   クライアントに気付かれることなくサービスとして動作する承認されていないエンティティ。 このシナリオでは、悪意のある (承認されていない) ユーザーがオンライン サービスとして動作し、クライアントからメッセージを途中受信して機密情報を取得します。 次にこの承認されていないユーザーは、盗んだデータを使用して侵害した口座から資金を転送します。 この攻撃は、既知のも、*フィッシング攻撃*します。  
  
-   呼び出し元が意図したものと異なる結果を取得するようなメッセージの改ざん。 たとえば、預金先の口座番号を変更して、資金を承認されていない口座に移動できます。  
  
-   迷惑なハッカーは、同じ注文をリプレイします。 たとえば、オンライン書店は数百の注文を受け、注文していない顧客に書籍を送付します。  
  
-   クライアントを認証する能力の欠如。 この場合、サービスは、適切なユーザーがトランザクションを実行していることを保証できません。  
  
 転送セキュリティが提供する保証を簡単に説明すると次のようになります。  
  
-   サービス エンドポイント (応答者) の認証  
  
-   クライアント プリンシパル (イニシエーター) の認証  
  
-   メッセージの整合性  
  
-   メッセージの機密性  
  
-   リプレイの検出  
  
### <a name="integration-with-existing-security-infrastructures"></a>既存のセキュリティ インフラストラクチャとの統合  
 ほとんどの場合、Web サービス展開には、SSL (Secure Sockets Layer) や Kerberos プロトコルなどの既存のセキュリティ ソリューションが実装されています。 Active Directory を使用する Windows ドメインなど、既に展開されているセキュリティ インフラストラクチャを利用する場合もあります。 新しい技術を評価し採用している間に、これらの既存の技術と統合する必要が生じることはよくあります。  
  
 WCF のセキュリティを使用して、既存のトランスポート セキュリティ モデルの統合、SOAP メッセージ セキュリティに基づく新しいトランスポート セキュリティ モデルの既存のインフラストラクチャを利用することができます。  
  
### <a name="integration-with-existing-authentication-models"></a>既存の認証モデルとの統合  
 すべての通信セキュリティ モデルにとって、通信のエンティティを識別し認証する機能は重要です。 この通信のエンティティは、"デジタル ID" または資格情報を使用し、通信先のピアで自身を認証します。 分散型の通信プラットフォームの発展により、さまざまな資格情報認証モデルや関連セキュリティ モデルが実装されてきました。 たとえば、インターネットでは、ユーザー名とパスワードを使用してユーザーを識別することが一般的に行われています。 イントラネットでは、ユーザーとサービスの認証をサポートする Kerberos ドメイン コントローラーの使用が一般的になりつつあります。 たとえば、2 つのビジネス パートナー間での特定のシナリオでは、証明書を使用してお互いにパートナーを認証する場合もあります。  
  
 同じサービスを企業内のユーザーや外部のパートナーまたはインターネット ユーザーに公開する Web サービスの世界では、インフラストラクチャがこのような既存のセキュリティ認証モデルとの統合に備えることが重要です。 WCF セキュリティには、さまざまな要素を含む資格情報の種類 (認証モデル) がサポートされています。  
  
-   匿名の呼び出し元  
  
-   ユーザー名クライアント資格情報  
  
-   証明書クライアント資格情報  
  
-   Windows (Kerberos プロトコルと NT LanMan [NTLM] の両方)  
  
### <a name="standards-and-interoperability"></a>標準と相互運用  
 既存の大規模展開の世界では、均一性はほとんどありません。 分散型のコンピューティングまたは通信のプラットフォームでは、さまざまなベンダーから提供される技術を相互運用する必要があります。 同様に、セキュリティも相互運用可能である必要があります。  
  
 相互運用可能なセキュリティ システムを実現するため、Web サービス業界で活動する企業はさまざまな標準を作成してきました。 特にセキュリティに関して、注目すべき標準がいくつか提案されています。それは、WS-Security の SOAP メッセージ セキュリティ (標準化団体の OASIS で認められ正式には WS-Security として知られる)、WS-Trust、WS-SecureConversation、および WS-SecurityPolicy です。  
  
 WCF では、さまざまな相互運用性のシナリオをサポートします。 <xref:System.ServiceModel.BasicHttpBinding> クラスは、基本セキュリティ プロファイル (BSP) を対象とし、<xref:System.ServiceModel.WSHttpBinding> クラスは、WS-Security 1.1 や WS-SecureConversation などの最新のセキュリティ標準を対象とします。 これらの標準を遵守すること、WCF のセキュリティは相互運用し、オペレーティング システムと Microsoft Windows 以外のプラットフォームでホストされている Web サービスと統合できます。  
  
## <a name="wcf-security-functional-areas"></a>WCF セキュリティの機能領域  
 WCF セキュリティは次の 3 つの機能領域に分かれています。 転送セキュリティ、アクセス制御、および監査します。 この後の各セクションでは、これらの領域について簡単に説明します。また、詳細情報へのリンクを示します。  
  
### <a name="transfer-security"></a>転送セキュリティ  
 転送セキュリティには、整合性、機密性、および認証の 3 つの主要なセキュリティ機能があります。 *整合性*メッセージが改ざんされているかどうかを検出する機能です。 *機密性*目的の受信者以外のすべてのユーザーが読み取り不可能なメッセージを保持する機能は、これは暗号化によって実現します。 *認証*はクレームされた id を確認する機能です。 これらの 3 つの機能を一緒に使用して、メッセージをある地点から別の地点に安全に到着させることができます。  
  
#### <a name="transport-and-message-security-modes"></a>トランスポート セキュリティ モードとメッセージ セキュリティ モード  
 WCF で転送セキュリティを実装する 2 つの主要なメカニズムを使用:*トランスポート*セキュリティ モードと*メッセージ*セキュリティ モード。  
  
-   *トランスポート セキュリティ モード*転送セキュリティを実現するために、HTTPS などのトランスポート レベルのプロトコルを使用します。 トランスポート モードの利点は、広範囲に採用されていること、多くのプラットフォームで利用可能なこと、コンピューター処理上の複雑性が低いことです。 ただし、Point-to-Point からのメッセージだけのセキュリティを保護するという欠点もあります。  
  
-   *メッセージ セキュリティ モード*、転送セキュリティを実装する一方、Ws-security を使用して (およびその他の仕様)。 メッセージ セキュリティは、SOAP メッセージに直接適用され、また SOAP エンベロープ内にアプリケーション データと共に格納されるため、トランスポート プロトコルに依存しない、拡張性が高い、エンド ツー エンド (Point-to-Point と対照) のセキュリティが保証される、という利点があります。ただし、SOAP メッセージの XML の性質を処理する必要があるため、トランスポート セキュリティ モードよりも処理が数倍遅くなる欠点があります。  
  
 これらの違いの詳細については、次を参照してください。 [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)します。  
  
 3 番目のセキュリティ モードは、上記の 2 つのモードを使用し、その両方の利点を引き継ぎます。 このモードは、`TransportWithMessageCredential` と呼ばれます。 このモードでは、クライアントの認証にメッセージ セキュリティを使用し、サーバーの認証にトランスポート セキュリティを使用して、メッセージの機密性と整合性を実現します。 これにより、`TransportWithMessageCredential` セキュリティ モードでは、トランスポート セキュリティ モードと同じ速度で処理が実行され、メッセージ セキュリティ モードと同じ方法でクライアント認証の拡張性が提供されます。 ただし、メッセージ セキュリティ モードと異なり、完全なエンド ツー エンド セキュリティは提供されません。  
  
### <a name="access-control"></a>アクセス制御  
 *アクセス制御*承認とも呼ばれます。 *承認*データを表示するさまざまな特権が異なることができます。 たとえば、企業の人事ファイルには従業員の機密データが含まれているため、管理者だけが従業員データの参照を許可されます。 また、管理者は直接報告書のデータのみを参照できます。 このような場合、アクセス制御は、ロール ("manager") と管理者の特定 ID の両方に基づいて行われます (ある管理者が別の管理者の部下のレコードを参照できないようにします)。  
  
 WCF では、アクセス制御機能が共通言語ランタイム (CLR) との統合によって提供される<xref:System.Security.Permissions.PrincipalPermissionAttribute>と一連の Api と呼ばれる、 *id モデル*します。 詳細については、アクセス制御とクレーム ベースの承認は、次を参照してください。[拡張セキュリティ](../../../../docs/framework/wcf/extending/extending-security.md)します。  
  
### <a name="auditing"></a>監査  
 *監査*は Windows イベント ログにセキュリティ イベントのログ記録します。 認証の失敗 (または成功) などのセキュリティ関連のイベントをログに記録できます。 詳細については、次を参照してください。[監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)します。 プログラミングの詳細については、次を参照してください。[方法: セキュリティ イベントの監査](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [サービスのセキュリティ保護](../../../../docs/framework/wcf/securing-services.md)  
 [一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 [バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [認証](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 [承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [フェデレーションと発行済みトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [セキュリティ ガイドラインとベスト プラクティス](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [構成ファイルを使用してサービスを構成する方法](../../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [エンドポイントの作成の概要](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [セキュリティの拡張](../../../../docs/framework/wcf/extending/extending-security.md)  
 [Windows Server App Fabric のセキュリティ モデル](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
