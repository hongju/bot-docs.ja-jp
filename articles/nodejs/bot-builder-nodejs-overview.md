---
title: Bot Builder SDK for Node.js | Microsoft Docs
description: 強力で使いやすいボット構築フレームワーク、Bot Builder SDK for Node.js について説明します。
author: v-ducvo
ms.author: v-ducvo
manager: kamrani
ms.topic: article
ms.prod: bot-framework
ms.date: 12/13/2017
monikerRange: azure-bot-service-3.0
ms.openlocfilehash: 41c276186f08e9997497e5649a6566954f0c8079
ms.sourcegitcommit: f576981342fb3361216675815714e24281e20ddf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39304569"
---
# <a name="bot-builder-sdk-for-nodejs"></a>Bot Builder SDK for Node.js

> [!div class="op_single_selector"]
> - [.NET](../dotnet/bot-builder-dotnet-overview.md)
> - [Node.js](../nodejs/bot-builder-nodejs-overview.md)
> - [REST](../rest-api/bot-framework-rest-overview.md)

Bot Builder SDK for Node.js は、強力で使いやすいフレームワークで、Node.js 開発者がボットを作成するための手慣れた方法を提供しています。
これを使用して、単純なメッセージから自由形式の会話まで、さまざまな会話型ユーザー インターフェイスを構築できます。

ボットの会話のロジックは、Web サービスとしてホストします。 Bot Builder SDK では、<a href="http://restify.com">Restify</a> という、Web サービスを構築するための一般的なフレームワークを使用して、ボットの Web サーバーを作成します。 SDK は <a href="http://expressjs.com/">Express</a> と互換性があり、その他の Web アプリ フレームワークを適応させて使用することも可能です。 

この SDK を使用すると、SDK の次の機能を利用できます。 

- 会話ロジックをカプセル化するダイアログを構築するための強力なシステム。
- はい/いいえ、文字列、数値、列挙型などの単純な組み込みプロンプトに加え、画像、添付ファイル、およびボタンを含むリッチ カードを含むメッセージをサポートしています。
- <a href="http://luis.ai" target="_blank">LUIS</a>などの強力な AI フレームワークの組み込みサポート。
- 必要に応じて、ヘルプ、ナビゲーション、明確化、確認を提供してユーザーとの会話を進めるようにする組み込みの認識エンジンやイベント ハンドラ。

## <a name="get-started"></a>作業開始

初めてボットを作成する場合は、プロジェクトの設定、SDK のインストール、初めてのボットを実行の手順を詳しく説明した内容を参照して、[Node.js で初めてのボットを作成](bot-builder-nodejs-quickstart.md)してください。 

Bot Builder SDK for Node.js に慣れていない方は、「[主要な概念](bot-builder-nodejs-concepts.md)」を参照して Bot Builder SDK の主要なコンポーネントを理解します。

ボットが最上位ユーザーのシナリオに確実に対応できるようにするには、「[設計原則](../bot-service-design-principles.md)」や「[パターンの検討](../bot-service-design-pattern-task-automation.md)」を確認します。

## <a name="get-samples"></a>サンプルを入手する

[Bot Builder SDK for Node.js サンプル](bot-builder-nodejs-samples.md)では、Bot Builder SDK for Node.js 内の機能を活用する方法を示す、タスクに焦点をおいたボットを説明します。 サンプルを利用することで、豊富な機能を備えた優れたボットのビルドが迅速に開始できるようになります。

## <a name="next-steps"></a>次の手順
> [!div class="nextstepaction"]
> [主要な概念](bot-builder-nodejs-concepts.md)

## <a name="additional-resources"></a>その他のリソース

タスクに焦点をおいた以下のハウツー ガイドでは、Bot Builder SDK for Node.js のさまざまな機能について説明しています。

* [メッセージに応答する](bot-builder-nodejs-use-default-message-handler.md)
* [ユーザー アクションを処理する](bot-builder-nodejs-dialog-actions.md)
* [ユーザーの意図を認識する](bot-builder-nodejs-recognize-intent-messages.md)
* [リッチ カードを送信する](bot-builder-nodejs-send-rich-cards.md)
* [添付ファイルを送信する](bot-builder-nodejs-send-receive-attachments.md)
* [ユーザー データを保存する](bot-builder-nodejs-save-user-data.md)


Bot Builder SDK for Node.js に関する問題が発生した場合や提案がある場合は、[サポート](../bot-service-resources-links-help.md)に関する記事で利用可能なリソースの一覧をご覧ください。 


[DesignGuide]: ../bot-service-design-principles.md 
[DesignPatterns]: ../bot-service-design-pattern-task-automation.md 
[HowTo]: bot-builder-nodejs-use-default-message-handler.md 