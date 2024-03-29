---
title: カスタム アシスタントの概要 | Microsoft Docs
description: 独自のカスタム アシスタントを作成する方法について説明します
author: darrenj
ms.author: darrenj
manager: kamrani
ms.topic: article
ms.service: bot-service
ms.date: 05/23/2019
monikerRange: azure-bot-service-4.0
ms.openlocfilehash: eba4ad9ba2fae85fbc2488e5fef8d5a7dac593ee
ms.sourcegitcommit: dbbfcf45a8d0ba66bd4fb5620d093abfa3b2f725
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67464760"
---
## <a name="custom-assistant-overview"></a>カスタム アシスタントの概要

## <a name="overview"></a>概要

会話型アシスタントについては、自社のブランドに合わせて調整したり、顧客に合わせてパーソナライズしたり、さまざまな会話キャンバスやデバイスで使用できるようにしたいという要望が、お客様やパートナーから多数寄せられています。 Microsoft では、Bot Framework SDK の開発をオープン ソースのアプローチで進めており、カスタム パーソナル アシスタントもオープン ソースです。そのため、基本機能セットを基に構築されたエンド ユーザー エクスペリエンスについては、お客様が完全に制御できます。 さらに、エンド ユーザーやデバイス/エコシステムの情報に関するインテリジェンスを通じてエクスペリエンスを強化し、真に統合されたインテリジェントなエクスペリエンスを提供することもできます。

Microsoft では、製品の機能をお客様が制御できるようにすることで、お客様が顧客関係や分析データを強化していけるようにする必要があると考えています。 そのため、カスタム アシスタントでは、お客様やパートナーがユーザー エクスペリエンスを完全に制御できるようにしています。 名前、音声、およびパーソナリティは、組織のニーズに合わせて変更することができます。 カスタム アシスタント ソリューションを使用すれば、独自のアシスタントを簡単に作成し、すぐに使い始めることができます。 

カスタム パーソナル アシスタント機能の使用範囲は幅広く、通常は、エンド ユーザーに広範な機能を提供できます。 開発者の生産性を高め、再利用可能な会話エクスペリエンスの高度なエコシステムを構築できるようにするため、Microsoft では、再利用可能な会話スキルの初期サンプルを開発者に提供しています。 これらのスキルを会話アプリケーションに追加すれば、目的地の検索や、カレンダー、タスク、メールの操作など、さまざまなシナリオでの会話エクスペリエンスを強化できます。 スキルは、複数の言語に対応した言語モデルと、ダイアログ、およびコードで構成されており、完全にカスタマイズ可能です。

現在、初期プレビューを進めており、オープンソースのリポジトリを通じて初期のお客様やパートナーと緊密に連携しながら、初期段階のエクスペリエンスを開発し、数か月以内にリリースすることを目指しています。 

![カスタム アシスタントの図](media/enterprise-template/CustomAssistantDiagram.jpg)

## <a name="complete-control-of-the-user-experience"></a>ユーザー エクスペリエンスの完全な制御

エンド ユーザー エクスペリエンスの要素は、すべてお客様が制御できます。 これには、ブランディング、名前、音声、パーソナリティ、応答、およびアバターが含まれます。 カスタム アシスタントとサポート スキルのソース コードもすべて提供されるで、必要に応じて調整することができます。

## <a name="complete-ownership-and-control-of-data"></a>データの完全な所有権と管理

カスタム アシスタントは、お客様の Azure サブスクリプション内にデプロイされます。 したがって、アシスタントによって生成されたデータ (質問の内容やユーザーの動作など) は、ご利用の Azure サブスクリプション内にすべて保存されます。 詳しくは、[Microsoft Cognitive Services](https://www.microsoft.com/trustcenter/cloudservices/cognitiveservices) に関するページと、[Trust Cente の Azure のセクション](https://www.microsoft.com/TrustCenter/CloudServices/Azure)をご覧ください。

## <a name="your-assistant-anywhere"></a>あらゆるチャネルから利用できるアシスタント

カスタム アシスタントは Microsoft Conversational AI プラットフォームを利用しているので、あらゆる Bot Framework [チャネル](https://docs.microsoft.com/azure/bot-service/bot-service-manage-channels?view=azure-bot-service-4.0)を通じて利用することができます (Web チャット、FaceBook Messenger、Skype など)。さらに、[Direct Line](https://docs.microsoft.com/azure/bot-service/rest-api/bot-framework-rest-direct-line-3-0-concepts?view=azure-bot-service-4.0) チャネルを通じて、デスクトップやモバイル アプリ (自動車、スピーカー、アラーム時計などのデバイスを含む) に機能を組み込むこともできます。

## <a name="built-on-enterprise-grade-technology"></a>エンタープライズ グレードのテクノロジに基づいて構築

カスタム アシスタント ソリューションは、Azure Bot Service、Language Understanding Cognitive Service、Unified Speech のほか、Azure の幅広いサポート コンポーネントに基づいて構築されているため、お客様は [Azure のグローバルなインフラストラクチャ](https://azure.microsoft.com/global-infrastructure/)を効果的に活用することができます。

また、LUIS Cognitive Service によって Language Understanding がサポートされているので、[こちらに記載](https://docs.microsoft.com/azure/cognitive-services/luis/luis-supported-languages)されている幅広い言語セットをサポートできます。 [Translator Cognitive Service](https://azure.microsoft.com/services/cognitive-services/translator-text-api/) では、カスタム アシスタントの提供範囲をさらに拡大するための、追加の機械翻訳機能も提供されています。

## <a name="integrated-and-context-aware"></a>統合性とコンテキスト対応

カスタム アシスタントはデバイスやエコシステム内に統合できるので、お客様は真に統合された、インテリジェントなエクスペリエンスを実現することができます。 このコンテキスト対応型のソリューションにより、かつてなくインテリジェントなエクスペリエンスを開発し、他の方法では達成できない高度なパーソナライズ性を提供することが可能となっています。

## <a name="3rd-party-assistant-integration"></a>サードパーティ アシスタントの統合

カスタム アシスタントでは、独自のエクスペリエンスを提供できるだけでなく、エンドユーザーの選択したデジタル アシスタントに処理をハンドオフして、特定のタイプの質問に対応することもできます。

## <a name="flexible-integration"></a>柔軟な統合性

Microsoft のカスタム アシスタント アーキテクチャは柔軟性に優れているので、お客様が既に構築しているデバイス ベースの音声処理機能や自然言語処理機能と統合することができます。もちろん、既存のバックエンド システムや API とも統合できます。

## <a name="adaptive-cards"></a>Adaptive Cards (アダプティブ カード)

カスタム アシスタントで[アダプティブ カード](https://adaptivecards.io/)を使用すると、テキスト ベースの応答と共に、ユーザー エクスペリエンス要素 (カード、画像、ボタンなど) を返すことができます。 デバイスや会話キャンバスに画面がある場合は、これらのアダプティブ カードをさまざまなデバイスやプラットフォームでレンダリングして、チャネルに合ったユーザー エクスペリエンスを提供することができます。 アダプティブ カードの例は[こちら](https://adaptivecards.io/samples/)で確認できます。レンダリングのオプションに関する情報は、[こちら](https://docs.microsoft.com/adaptive-cards/rendering-cards/getting-started)のドキュメントに記載されています。


## <a name="skills"></a>スキル

基本的なアシスタント以外にも、開発者の生産性向上に必要な、幅広い一般機能が用意されています。 生産性機能はその代表的な例です。目的地、メール、カレンダー、タスクなどの一般的なシナリオに対応しようとする場合、通常は、言語モデル (LUIS)、ダイアログ (コード)、統合 (コード)、言語生成 (応答) を作成する必要があります。

また、複数の言語をサポートする必要がある場合はさらに処理が複雑になり、独自のアシスタントを構築するために膨大な作業が必要になります。

カスタム アシスタント ソリューションの新しいスキル機能を使用すれば、構成作業を行うだけで、新機能をカスタム アシスタントにプラグインすることができます。 

ソース コードはカスタム アシスタントと共に GitHub ですべて公開されているので、開発者は各スキルのすべての要素 (言語モデル、ダイアログ、統合コード、言語生成) を自由にカスタマイズできます。

## <a name="example-scenarios"></a>シナリオ例

カスタム アシスタントは、幅広い業種のシナリオに対応して拡張できます。参考用として、シナリオの例を以下に示します。

- 自動車業界: 音声対応のパーソナル アシスタントを自動車に統合して、エンド ユーザーが従来の自動車操作 (ナビゲーションやラジオなど) を音声で行えるようにします。生産性重視のシナリオとしては、予定に間に合わない場合に会議の時間をずらしたり、タスク リストに項目を追加するなどといったことも可能です。さらに、イベントに応じて、実行するべきタスク (エンジンの起動、自宅への移動、クルーズ コントロールの起動など) を自動車から提案するなど、プロアクティブなエクスペリエンスを提供することもできます。 アダプティブ カードはヘッド ユニットにレンダリングし、音声機能はプッシュ トゥ トークやウェイク ワードによる操作で実行できます。

- サービス業: ホテルの客室にあるデバイスに音声対応のパーソナル アシスタントを統合して、接客重視のさまざまなシナリオ (宿泊の延長、レイト チェックアウトの要請、ルーム サービスなど) に対応できます。コンシェルジュ機能を提供したり、近くの飲食店やアトラクションを探すこともできます。 オプションの生産性アカウントにリンクすれば、エクスペリエンスをさらにパーソナライズして、モーニング コールを提案したり、気象警報を通知したり、宿泊パターンを学習させたりすることもできます。 最近では、客室のテレビをパーソナライズするケースも増えています。

- エンタープライズ: 音声とテキストに対応した従業員アシスタント機能を組織のデバイスや既存の会話キャンバス (Teams、Web チャット、Slack など) に統合して、予定表の管理や、空いている会議室の検索、特定のスキルを持った人員の検索、人事関連業務の実行など、さまざまな機能を従業員に提供できます。 

## <a name="getting-started"></a>Getting Started (概要)

現在、初期プレビューを進めており、オープンソースのリポジトリを通じて初期のお客様やパートナーと緊密に連携しながら、初期段階のエクスペリエンスを開発し、数か月以内にリリースすることを目指しています。 ご希望のシナリオを登録し、ソリューションの利用を申し込むには、[こちらのフォーム](https://aka.ms/customassistantpreviewform)に必要事項を入力してください。後ほど、Microsoft からご連絡を差し上げます。

