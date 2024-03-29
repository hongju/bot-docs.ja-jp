---
title: Bot Service についてよく寄せられる質問 | Microsoft Docs
description: Bot Framework の要素と、新しい機能が利用可能になる時期についてよく寄せられる質問を示します。
author: DeniseMak
ms.author: v-demak
manager: kamrani
ms.topic: article
ms.service: bot-service
ms.date: 02/21/2019
ms.openlocfilehash: 57efc2f1d137988792d9484d7f1f857bd193ecfa
ms.sourcegitcommit: a295a90eac461f8b96770dd902ba44919acf33fc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67405784"
---
# <a name="bot-framework-frequently-asked-questions"></a>Bot Framework についてよく寄せられる質問

この記事では、Bot Framework についてよく寄せられる質問とその回答を示します。

## <a name="background-and-availability"></a>背景と提供状況
### <a name="why-did-microsoft-develop-the-bot-framework"></a>Microsoft が Bot Framework を開発したのはなぜですか?

会話ユーザー インターフェイス (CUI) が登場しましたが、現時点では、新しい会話型エクスペリエンスを構築したり、ユーザーが楽しめる会話型インターフェイスで既存のアプリケーションやサービスを利用できるようにするために必要な専門知識やツールを持っている開発者はほとんどいません。 Microsoft は、開発者が優れたボットを作成し、Microsoft のプレミア チャンネル上など、ユーザーが会話する場所にボットを接続することを容易にするために、Bot Framework を開発しました。

### <a name="what-is-the-v4-sdk"></a>v4 SDK とは何ですか?
Bot Framework v4 SDK は、以前の Bot Framework SDK から得たフィードバックと知識を基に構築されています。 ボットの構成要素の豊富なコンポーネント化を可能にしながら、適切なレベルの抽象化が導入されます。 簡単なボットから始め、モジュール式の拡張可能なフレームワークを使用してボットを高度化していくことができます。 GitHub で SDK の [FAQ](https://github.com/Microsoft/botbuilder-dotnet/wiki/FAQ) をご覧ください。

## <a name="bot-framework-sdk-version-3-lifetime-support"></a>Bot Framework SDK バージョン 3 のライフタイム サポート 
SDK V3 ボットは Azure Bot Service によって引き続き実行およびサポートされます。  他のフレームワークと同様に、Bot Framework SDK V4 のリリース以降も、セキュリティ、優先度の高いバグ修正、およびコネクタ/プロトコル レイヤーの更新を含む SDK V3 のサポートを継続します。  v3 のサポートは 2019 年まで継続されます。

### <a name="what-is-microsoft-plan-for-supporting-existing-v3-bots-what-happens-to-my-v3-bots-will-my-v3-bots-stop-working"></a>既存の V3 ボットをサポートするために Microsoft はどのような計画を立てていますか? 自作の V3 ボットはどうなりますか? 自作の V3 ボットは動作しなくなりますか?
SDK V3 ボットは Azure Bot Service によって引き続き実行およびサポートされます。  他のフレームワークと同様に、Bot Framework SDK V4 のリリース以降も、セキュリティ、優先度の高いバグ修正、およびコネクタ/プロトコル レイヤーの更新を含む SDK V3 のサポートを継続します。  v3 のサポートは 2019 年まで継続されます。
- Azure Bot Service と Bot Framework V3 はどちらも GA (一般公開) 製品であり、完全にサポートされています。 基となる Bot Framework プロトコルとコネクタ ライブラリは変更されておらず、V3 SDK と V4 SDK の間で共有されています。  
- Bot Framework (BotBuilder) V3 SDK で作成されたボットは、引き続き 2019 年までサポートされます。 
- お客様は、Azure portal または Azure CLI ツールを使用して V3 ボットを引き続き作成できます。

### <a name="what-happens-to-my-bot-written-to-rest--bot-framework-protocol-31"></a>REST & Bot Framework Protocol 3.1 に書き込まれたボットはどうなりますか?
- Azure Bot Service と Bot Framework V3 はどちらも GA (一般公開) 製品であり、完全にサポートされています。
- Bot Framework プロトコルは変更されておらず、V3 SDK と V4 SDK の間で共有されています。  

### <a name="will-there-be-more-updates-additional-development-for-the-v3-sdk-or-just-bugfixes"></a>V3 SDK 用に更新プログラムのリリース、追加の開発は行われますか? それともバグ修正のみですか?  
- V3 の更新には、軽微な機能強化 (主にコネクタ レイヤー) と、セキュリティと優先度の高いバグの修正を含める予定です。  
- V3 の更新プログラムは、年に 2 回と、バグ修正や必要なプロトコルの変更に基づいて必要に応じてリリースされる予定です。 
- 現在の計画では、C# および JavaScript SDK 用の NuGet および NPM に対してマイナーおよびパッチ バージョンの V3 を公開します。

### <a name="why-v4-is-not-backwards-compatible-with-v3"></a>V4 が V3 と下位互換性がないのはなぜですか?
- プロトコル レベルでは、会話型アプリ (ボットとも呼ばれます) と別のチャネル間の通信には、V3 と V4 の間で同じ Bot Framework Activity プロトコルが使用されます。 同じ基となる Azure Bot Service (AZURE BOT SERVICE) インフラストラクチャが V3 と V4 の両方のボットをサポートしています。
- Bot Framework SDK V4 にはモジュール式で拡張可能な SDK アーキテクチャを使用した会話中心の開発環境が提供されるため、開発者は堅牢で洗練されたチャット アプリケーションを作成することができます。 V4 の拡張可能な設計は、お客様からのフィードバックに基づいています。つまり、SDK V3 のダイアログ モデルとプリミティブは統一的ではなく、拡張性に制約があります。  

### <a name="what-is-the-general-migration-strategy-i-have-a-v3-bot-how-can-i-migrate-it-to-v4-can-i-migrate-my-v3-bot-to-v4"></a>全般的な移行戦略について教えてください。 V3 ボットを持っていますが、どうすれば V4 に移行できますか? V3 ボットは V4 に移行できますか?

- V3 ボットから V4 への移行については、「[Differences between the v3 and v4 .NET SDK (.NET SDK v3 と v4 の違い)](v4sdk/migration/migration-about.md)」を参照してください。
- 現時点では、SDK V3 で作成されたボットの SDK V4 への移行に関するヘルプは、ドキュメントとサンプルの形式で提供する予定です。 現時点では、V3 ビルド ボットを V4 ボット内で機能できるようにする SDK V3 互換レイヤーを SDK V4 で提供する予定はありません。
- 運用中の Bot Framework SDK V3 ボットが既にある場合でも心配は無用です。当面の間はそのまま機能します。
- Bot Framework SDK V4 は、非常に成功した V3 SDK の進化版です。 V4 は、V3 ボットが新しい V4 SDK 上で動作しなくなる重大な変更を含むメジャー バージョン リリースです。

### <a name="should-i-build-new-a-bot-using-v3-or-v4"></a>V3 または V4 を使用して新しいボットをビルドする必要はありますか?
- 新しい会話型エクスペリエンスのために、Bot Framework SDK V4 を使用して新しいボットを始めることをお勧めします。
- Bot Framework SDK V3 に既に慣れ親しんでいる場合は、新しいバージョンと、新しい [Bot Framework SDK V4](http://aka.ms/botframeowrkoverview) で提供される機能の学習には時間がかかります。
- 運用中の Bot Framework SDK V3 ボットが既にある場合でも心配は無用です。当面の間はそのまま機能します。
- Azure portal と Azure コマンド ラインを使用すると、Bot Framework SDK V4 ボットと以前の V3 ボットを作成できます。 

### <a name="how-can-i-migrate-azure-bot-service-from-one-region-to-another"></a>Azure Bot Service をあるリージョンから別のリージョンに移行するにはどうすればよいですか?

Azure Bot Service は、リージョンの移動をサポートしていません。 特定のリージョンに関連付けられていないグローバル サービスです。

## <a name="channels"></a>チャンネル
### <a name="when-will-you-add-more-conversation-experiences-to-the-bot-framework"></a>Bot Framework にさらに多くの会話エクスペリエンスが追加されるのはいつですか?

Microsoft では、チャンネルの追加など、Bot Framework を継続的に改善していく予定ですが、現時点でスケジュールを提供することはできません。  
フレームワークに特定のチャンネルを追加することをご希望の場合は[お問い合わせください][Support]。

### <a name="i-have-a-communication-channel-id-like-to-be-configurable-with-bot-framework-can-i-work-with-microsoft-to-do-that"></a>Bot Framework で構成可能にしたいコミュニケーション チャンネルがあります。 Microsoft と協力してこれを行うことはできますか?

開発者が Bot Framework に新しいチャンネルを追加する一般的なメカニズムは提供していませんが、[Direct Line API][DirectLineAPI]. If you are a developer of a communication channel and would like to work with us to enable your channel in the Bot Framework [we’d love to hear from you][Support] を使用してボットをアプリに接続できます。

### <a name="if-i-want-to-create-a-bot-for-microsoft-teams-what-tools-and-services-should-i-use"></a>Microsoft Teams 用のボットを作成する場合、どのようなツールやサービスを使用すればよいですか?

Bot Framework は、Teams や他の多くのチャンネル向けに、高品質でパフォーマンスと応答性に優れたスケーラブルなボットを作成、接続、展開できるように設計されています。 SDK を使用して、(会話エクスペリエンス全体で現在のボットの対話において多くを占める) テキスト/SMS、画像、ボタン、カード対応のボットや、豊富なオーディオ/動画エクスペリエンスなどの Teams 固有のボットの対話を作成できます。

優れたボットが既にあり、Teams の対象ユーザーを獲得したい場合は、Bot Framework for REST API を使用して Teams (またはサポートされている任意のチャンネル) に簡単に接続できます (インターネットにアクセス可能な REST エンドポイントがある場合)。

### <a name="how-do-i-create-a-bot-that-uses-the-us-government-data-center"></a>米国政府データ センターを使用するボットはどのように作成しますか?

米国政府データ センターを使用するボットを作成するために必要となる主要な手順は 2 つあります。
1. appsettings.json (または App Service 設定) に "チャンネル プロバイダー" 設定を追加します。 これは、具体的にはこの名前/値の定数に設定する必要があります:ChannelService ="https://botframework.azure.us"。 以下に appsetting.json の使用例を示します。

```json
{
  "MicrosoftAppId": "", 
  "MicrosoftAppPassword": "",
  "ChannelService": "https://botframework.azure.us"
}
```
2. .NET core を使用している場合、startup.cs ファイルに ConfigurationChannelProvider を追加する必要があります。 この方法は、使用している SDK のバージョンによって異なります。

- バージョン 4.3 以降、ConfigureServices メソッドで、ConfigurationChannelProvider インスタンスを作成する必要があります。 BotFrameworkHttpAdapter クラスを使用している場合、これをシングルトンとしてサービス コレクションに次のように挿入します:

```csharp  
services.AddSingleton<IChannelProvider, ConfigurationChannelProvider>();
```
- 4\.3 より前のバージョンの場合、ConfigureServices メソッドで、AddBot メソッドを検索します。 オプションを設定するときは、必ず次を追加します:

```csharp
options.ChannelProvider = new ConfigurationChannelProvider();
```
政府機関のサービスに関する詳細については、[こちら](https://docs.microsoft.com/en-us/azure/azure-government/documentation-government-services-aiandcognitiveservices#azure-bot-service)を参照してください。

## <a name="security-and-privacy"></a>セキュリティとプライバシー
### <a name="do-the-bots-registered-with-the-bot-framework-collect-personal-information-if-yes-how-can-i-be-sure-the-data-is-safe-and-secure-what-about-privacy"></a>Bot Framework に登録されているボットは個人情報を収集するのでしょうか。 収集する場合、データの安全とセキュリティを確保するにはどうすればよいですか? プライバシーはどうですか?

各ボットは独自のサービスであり、これらのサービスの開発者には、開発者倫理規定に従ってサービス利用規約とプライバシーに関する声明を提供することが義務付けられています。  この情報には、ボット ディレクトリのボットのカードからアクセスできます。

I/O サービスを提供するために、Bot Framework では、お客様が使用したチャット サービスからボットに、メッセージとメッセージのコンテンツ (お客様の ID を含む) を送信します。

### <a name="can-i-host-my-bot-on-my-own-servers"></a>自分のサーバー上でボットをホストできますか?
はい。 お使いのボットはインターネット上のあらゆる場所でホストできます。 これには、ご自身のサーバー、Azure、またはその他の任意のデータセンターが含まれます。 唯一の要件は、パブリックにアクセスできる HTTPS エンドポイントがボットによって公開されている必要があることです。

### <a name="how-do-you-ban-or-remove-bots-from-the-service"></a>Microsoft はどのようにしてボットを禁止したり、サービスからボットを削除したりするのですか?

ユーザーは、ディレクトリ内のボットの連絡先カードを使用して、不正な動作をするボットを報告できます。 開発者がサービスに参加するには、Microsoft サービス利用規約に従う必要があります。

### <a name="which-specific-urls-do-i-need-to-whitelist-in-my-corporate-firewall-to-access-bot-framework-services"></a>Bot Framework サービスにアクセスするために、会社のファイアウォールでホワイトリストに登録する必要がある URL を教えてください。
お客様のボットからインターネットへの送信トラフィックをブロックしているファイアウォールがある場合は、そのファイアウォールで次の URL をホワイトリストに登録する必要があります。
- login.botframework.com (Bot 認証)
- login.microsoftonline.com (Bot 認証)
- westus.api.cognitive.microsoft.com (Luis.ai の NLP 統合用)
- state.botframework.com (プロトタイプ作成用のボット状態ストレージ)
- cortanabfchanneleastus.azurewebsites.net (Cortana チャンネル)
- cortanabfchannelwestus.azurewebsites.net (Cortana チャンネル)
- *.botframework.com (チャンネル)

### <a name="can-i-block-all-traffic-to-my-bot-except-traffic-from-the-bot-connector-service"></a>Bot Connector サービスからのトラフィックを除く、自分のボットへのすべてのトラフィックをブロックできますか?
いいえ。 このような IP アドレスまたは DNS ホワイトリスト登録は実用的ではありません。 Bot Framework Connector サービスは、世界規模の Azure データセンターでホストされ、Azure IP の一覧が常に変わっています。 特定の IP アドレスのホワイトリスト登録が有効なのは 1 日で、翌日に Azure IP アドレスが変わると無効になります。
 
### <a name="what-keeps-my-bot-secure-from-clients-impersonating-the-bot-framework-connector-service"></a>自分のボットは、Bot Framework Connector サービスを偽装するクライアントからどのように保護されますか?
1. お使いのボットへのすべての要求に付いているセキュリティ トークンでは ServiceUrl がエンコードされています。つまり、攻撃者がトークンにアクセスしても、会話を新しい ServiceUrl にリダイレクトすることはできません。 これは、SDK のすべての実装によって適用され、Microsoft の認証[参考](https://docs.microsoft.com/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-3.0#bot-to-connector)資料に記載されています。

2. 受信トークンが欠落しているか、形式に誤りがある場合、Bot Framework SDK の応答ではトークンが生成されません。 これにより、ボットが正しく構成されていない場合に発生する損害が制限されます。
3. ボット内で、トークンで提供される ServiceUrl を手動で確認できます。 これにより、サービス トポロジの変更が発生した場合にボットが脆弱になります。したがって、これは可能ですが、お勧めしません。


これらはボットからインターネットへの送信接続であることに注意してください。 ボットへの通信に Bot Framework Connector サービスによって使用される IP アドレスまたは DNS 名の一覧はありません。 受信 IP アドレスのホワイトリスト登録はサポートされていません。

## <a name="rate-limiting"></a>レート制限
### <a name="what-is-rate-limiting"></a>レート制限とは何ですか?
Bot Framework サービスは、どのボットも他のボットのパフォーマンスに悪影響を及ぼすことがないように、不正な呼び出しパターン (サービス拒否攻撃など) からサービス自体と顧客を保護する必要があります。 このような保護を実現するために、すべてのエンドポイントにレート制限 ("調整" とも呼ばれます) が追加されました。 レート制限を適用することで、ボットが特定の呼び出しを行うことができる頻度を制限できます。 たとえば、レート制限を有効にすると、ボットは多数のアクティビティを投稿する場合に、それらを一定期間にわたって分割して投稿する必要があります。 レート制限の目的は、ボットの総容量の上限を設けることではないことに注意してください。 人間の会話パターンに従っていない会話インフラストラクチャの不正使用を防ぐことを目的としています。

### <a name="how-will-i-know-if-im-impacted"></a>影響を受けているかどうかはどうすればわかりますか?
要求が大量であっても、お客様がレート制限を受けることはまずありません。 ほとんどのレート制限は、(ボットまたはクライアントからの) アクティビティの一括送信、極端なロード テスト、またはバグによってのみ発生します。 要求が調整されると、要求の再試行が成功するまでの待機時間 (秒単位) を示す Retry-After ヘッダーと共に、HTTP 429 (Too Many Requests) 応答が返されます。 この情報を収集するには、Azure Application Insights を使用してボットの分析を有効にします。 また、メッセージをログに記録するコードをボットに追加することもできます。 

### <a name="how-does-rate-limiting-occur"></a>レート制限はどのように発生しますか?
次の場合に発生する可能性があります。
-   ボットがメッセージを送信する頻度が高すぎる場合
-   ボットのクライアントがメッセージを送信する頻度が高すぎる場合
-   Direct Line クライアントが新しい Web ソケットを要求する頻度が高すぎる場合

### <a name="what-are-the-rate-limits"></a>レート制限値を教えてください。
サービスとユーザーを保護しながら、できるだけ緩やかなものにするために、レート制限値は継続的に調整されています。 しきい値が変更されることがあるため、現時点では数値を公開していません。 レート制限の影響を受けている場合は、[bf-reports@microsoft.com](mailto://bf-reports@microsoft.com) までお気軽にご連絡ください。

## <a name="related-services"></a>関連サービス
### <a name="how-does-the-bot-framework-relate-to-cognitive-services"></a>Bot Framework は Cognitive Services にどのように関連していますか?

Bot Framework と [Cognitive Services](http://www.microsoft.com/cognitive) は、[Microsoft Build 2016](http://build.microsoft.com) で導入された新しい機能であり、一般提供時に Cortana Intelligence Suite にも統合されます。 これらのサービスはいずれも、長年にわたる研究と一般的な Microsoft 製品での使用に基づいて構築されています。 これらの機能を "Cortana Intelligence" と組み合わせることで、あらゆる組織が、データの力、クラウド、インテリジェンスを活用して、新たなチャンスを切り開き、ビジネスを加速させ、顧客にサービスを提供する業界をリードする独自のインテリジェント システムを構築できます。

### <a name="what-is-cortana-intelligence"></a>Cortana Intelligence とは何ですか?

Cortana Intelligence は、データをインテリジェントなアクションに変える、フル マネージドのビッグ データ、高度な分析、およびインテリジェンスのスイートです。  
これは、Microsoft 全体にわたる長年の研究と技術革新に基づいたテクノロジー (高度な分析、機械学習、ビッグ データ ストレージ、クラウドでの処理など) をまとめた包括的なスイートです。

* すべてのデータを収集、管理、保存することができます。データは、スケーラブルかつ安全な方法で、長期的にシームレスにコスト効率よく増加させることができます。
* クラウドによって強化された、アクションにつながる分析を簡単に行うことができます。これらの分析により、最も厳しい問題に対処するための予測、指示、意思決定の自動化が可能になります。
* Cognitive Services とエージェントを使用して、状況に応じた自然な方法で周囲の世界を見る、聴く、解釈する、理解することを可能にするインテリジェント システムを実現します。

Microsoft は、Cortana Intelligence によって、企業のお客様が新たなチャンスを切り開き、ビジネスを加速させ、業界のリーダーになれるよう支援したいと考えています。

### <a name="what-is-the-direct-line-channel"></a>Direct Line チャンネルとは何ですか?

Direct Line は、サービス、モバイル アプリ、または Web ページにボットを追加できる REST API です。

Direct Line API のクライアントは、任意の言語で記述できます。 [Direct Line プロトコル][DirectLineAPI]にコード化し、Direct Line 構成ページでシークレットを生成して、コードが存在する場所からボットに話しかけるだけです。

Direct Line は以下に適しています。

* iOS、Android、Windows Phone などの OS 上のモバイル アプリ
* Windows、OSX などの OS 上のデスクトップ アプリケーション
* [埋め込み可能な Web チャット チャンネル][WebChat]が提供するものよりも多くのカスタマイズが必要な Web ページ
* サービス間アプリケーション


## <a name="app-registration"></a>アプリケーションの登録

### <a name="i-need-to-manually-create-my-app-registration-how-do-i-create-my-own-app-registration"></a>自分のアプリケーションの登録を手動で作成する必要があります。 独自のアプリケーションの登録はどのように作成するのですか?

独自のアプリケーションの登録の作成は、次のような状況で必要になります。

- Bot Framework ポータル (https://dev.botframework.com/bots/new) など) で、ボットを作成しました。 
- 自分の組織でアプリケーションの登録をすることができず、構築しているボット用のアプリ ID を作成するために別のパーティーが必要になります。
- それ以外の場合、独自のアプリ ID (とパスワード) を手動で作成する必要があります。

独自のアプリ ID を作成するには、次の手順に従ってください。

1. [Azure アカウント](https://portal.azure.com)にサインインします。 Azure アカウントを持っていない場合は、[無料のアカウントにサインアップ ](https://azure.microsoft.com/free/) できます。
2. [[アプリの登録] ブレード ](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) にアクセスし、上部にある操作バーの **[新しい登録]** をクリックします。

    ![新しい登録](media/app-registration/new-registration.png)

3. *[名前]* フィールドにアプリケーション登録の表示名を入力し、サポートされているアカウントの種類を選択します。 この名前は、ボット ID と一致させる必要はありません。

    > [!IMPORTANT]
    > *[サポートされているアカウントの種類]* で、 *[任意の組織のディレクトリ内のアカウントと、個人用の Microsoft アカウント (Skype、Xbox、Outlook.com など)]* ラジオ ボタンを選択します。 その他のオプションのいずれかを選択すると、**ボットの作成は失敗**します。

    ![登録の詳細](media/app-registration/registration-details.png)

4. **[登録]** をクリックします。

    しばらくすると、新しく作成されたアプリケーションの登録によって、ブレードが開きます。 [概要] ブレードの *[アプリケーション クライアント ID]* をコピーし、[アプリ ID] フィールドに貼り付けます。

    ![アプリケーション ID](media/app-registration/app-id.png)

Bot Framework ポータルを介してボットを作成している場合、アプリケーションの登録の設定は完了しています。シークレットは自動的に生成されます。 

Azure portal でボットを作成している場合、アプリケーションの登録用のシークレットを生成する必要があります。 

1. アプリケーション登録のブレードの左側のナビゲーション列にある **[Certificates & secrets]\(証明書およびシークレット\)** をクリックします。
2. そのブレードで、 **[New client secret]\(新しいクライアント シークレット\)** ボタンをクリックします。 ポップアップ表示されるダイアログ ボックスで、シークレットのオプションの説明を入力し、[有効期限] ラジオ ボタン グループから **[無期限]** を選択します。 

    ![新しいシークレット](media/app-registration/new-secret.png)

3. *[クライアント シークレット]* の下の表からシークレットの値をコピーして、アプリケーションの *[パスワード]* フィールドに貼り付け、そのブレードの下部にある **[OK]** をクリックします。 ボットの作成を続行します。 

    > [!NOTE]
    > シークレットは、このブレード上にいる間のみ表示されます。そのページから移動すると、取得することができなくなります。 必ず、これを安全な場所にコピーしてください。

    ![新しいアプリケーション ID](media/app-registration/create-app-id.png)


[DirectLineAPI]: https://docs.microsoft.com/azure/bot-service/rest-api/bot-framework-rest-direct-line-3-0-concepts
[Support]: bot-service-resources-links-help.md
[WebChat]: bot-service-channel-connect-webchat.md

