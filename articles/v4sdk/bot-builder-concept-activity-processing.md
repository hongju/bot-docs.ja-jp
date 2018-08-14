---
title: アクティビティの処理 | Microsoft Docs
description: ボット SDK でのアクティビティ処理について説明します。
keywords: ボット アダプター, カスタム ミドルウェア, ショート サーキット, フォールバック, イベント ハンドラー
author: jonathanfingold
ms.author: jonathanfingold
manager: kamrani
ms.topic: article
ms.prod: bot-framework
ms.date: 03/22/2018
monikerRange: azure-bot-service-4.0
ms.openlocfilehash: 8e08ac4721ee78bbd5d13dac09d9e505d3a1b134
ms.sourcegitcommit: f95702d27abbd242c902eeb218d55a72df56ce56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39304660"
---
# <a name="activity-processing"></a>アクティビティの処理

[!INCLUDE [pre-release-label](~/includes/pre-release-label.md)]

ボットとユーザーの間では、アクティビティを介して情報の交換が行われます。 ご利用のボット アプリケーションによって受信された各アクティビティはボット アダプターに渡されます。次に、このボット アダプターから、アクティビティ情報がご利用のボルト ロジックに渡され、最終的に応答がユーザーに送信されます。

[!INCLUDE [Define a turn](~/includes/snippet-definition-turn.md)]

> [!IMPORTANT]
> アクティビティ (特にボット ターン中に[作成する](#generating-responses)アクティビティ) は、非同期で処理されます。 非同期処理はボットの構築に必要な部分です。ボット全体の動作方法についてブラッシュ アップを行う必要がある場合は、[.NET の場合の非同期](https://docs.microsoft.com/en-us/dotnet/csharp/async)または [JavaScript の場合の非同期](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)に関するページを確認してください。

## <a name="the-bot-adapter"></a>ボット アダプター

ボットはその**アダプター**からの指示を受けます。アダプターは、ご利用のボットに対する管理者と考えることができます。 アダプターの役割としては、認証や、送受信の通信のルーティングなどが挙げられます。 アダプターはその環境によって異なります (ローカルの場合と Azure 上の場合とでは、アダプターの内部的な動作は異なります) が、各インスタンスにおいて、同じ目標が実現されます。 ほとんどの状況で、アダプターを直接操作することはありません (テンプレートからボットを作成する場合など) が、アダプターが存在する場所、アダプターによって何が行われるのかを把握しておくことをお勧めします。

ボット アダプターでは、認証プロセスのカプセル化、および Bot Connector Service との間でのアクティビティの送受信が行われます。 ご利用のボットでアクティビティが受信されると、アダプターによって次のことが行われます。そのアクティビティに関するすべての情報がラップされ、そのターン用の[コンテキスト オブジェクト](#turn-context)が作成され、それがご利用のボットのアプリケーション ロジックに渡され、ご利用のボットによって生成された応答がユーザーのチャネルに返送されます。

## <a name="authentication"></a>Authentication

アプリケーションによって受け取られた各受信アクティビティは、アクティビティからの情報および REST 要求からの `Authentication` ヘッダーを使用して、アダプターによって認証されます。

ユーザーへの送信アクティビティを認証する場合、アダプターではコネクタ オブジェクトおよびご利用のアプリケーションの資格情報が使用されます。

Bot Connector Service 認証では、JWT (JSON Web Token)`Bearer` トークンに加えて、ボット サービスの作成時またはご利用になるボットの登録時に Azure によって自動的に作成される **Microsoft アプリ ID** および **Microsoft アプリ パスワード**が使用されます。 ご利用のアプリケーションでは、トラフィックの認証をアダプターに許可するために、そのような資格情報が初期化時に必要になります。

> [!NOTE]
> ボットをローカルで実行またはテストする場合 (たとえば、Bot Framework Emulator を使用して)、それを行うために、ボットとの間でやり取りされるトラフィックを認証するようにアダプターを構成する必要はありません。

## <a name="turn-context"></a>turn context

アダプターでアクティビティが受信されると、**turn context** オブジェクトが作成されます。このオブジェクトでは、受信アクティビティ、送信者、受信者、チャネル、および会話に関する情報、アクティビティを処理するのに必要なその他のデータに関する情報が提供されます。 次に、このコンテキスト オブジェクトはアダプターによってボットに渡されます。 コンテキスト オブジェクトはターンの期間保持され、コンテキスト オブジェクトからは次の項目に関する情報が提供されます。

* 会話 - 会話を識別し、ボットに関する情報および会話に参加しているユーザーに関する情報を取り込みます。
* アクティビティ - 会話での要求および応答はすべて、アクティビティの種類です。 このコンテキストでは、受信アクティビティに関する情報 (ルーティング情報を含む)、チャネル、会話、送信者、および受信者に関する情報が提供されます。
* 状態 - その[状態](~/v4sdk/bot-builder-storage-concept.md)を追跡するために使用されるプロパティ (ユーザーとの会話中である場所、そのユーザーに関する情報、またはその他のビジネスロジック情報など)。
* カスタム情報 - ミドルウェアを実装してボットを拡張するか、またはボット ロジック内でボットを拡張する場合、各ターンで追加の情報を利用可能にすることができます。

またコンテキスト オブジェクトを使用すると、ユーザーに応答を送信できるほか、新しい会話を作成、または既存の会話を継続するためにアダプターへの参照を取得することができます。

> [!NOTE]
> アプリケーションとアダプターでは要求は非同期で処理されます。ただし、ビジネス ロジックを、要求-応答で駆動する必要はありません。

## <a name="middleware"></a>ミドルウェア

アダプターにはミドルウェアを追加することができます。 ミドルウェアとは、ご利用のボットおよびコア ボット ロジックに追加されるプラグインのレイヤーです。 ミドルウェアの詳細については、[ミドルウェア](~/v4sdk/bot-builder-concept-middleware.md)に関する独立した記事を参照してください。

ミドルウェアおよびボット ロジックでは、アクティビティと動作に関する情報を適宜取得するためにコンテキスト オブジェクトが使用されます。 ミドルウェアおよびボットでは、情報の更新およびコンテキスト オブジェクトへの情報の追加を行うこともできます (ターン、会話、またはその他のスコープにおける状態を追跡する場合など)。 SDK では、状態の永続性をボットに追加するのに使用できる何らかの_状態ミドルウェア_が提供されています。

## <a name="generating-responses"></a>応答の生成

コンテキスト オブジェクトには、アクティビティへの応答をコードで行えるようにするためのアクティビティ応答メソッドが備わっています。

* _send activity_ メソッドおよび _send activities_ メソッドを使用すると、1 つまたは複数のアクティビティを会話に送信することができます。
* _update activity_ メソッドがチャネルによってサポートされている場合は、このメソッドによって会話内のアクティビティを更新することができます。
* _delete activity_ メソッドがチャネルによってサポートされている場合は、このメソッドによって会話からアクティビティを削除することができます。

各応答メソッドは、非同期プロセスで実行されます。 それが呼び出されると、関連するイベント ハンドラー リストがアクティビティ応答メソッドによって複製されてから、ハンドラーの呼び出しが開始されます。すなわち、その複製には、この時点までに追加されたすべてのハンドラーが含まれますが、プロセスの開始後に追加されたものは含まれません。

このことはまた、タスク間で複雑さが異なる場合は特に、応答の順序が保証されないことも意味しています。 ご利用のボットで受信アクティビティに対する応答を複数作成できる場合は、ユーザーが応答を受け取る順番に関係なく、それらの応答が意味を成すことを確認します。

> [!IMPORTANT]
> プライマリ ボット ターンが完了すると、それを処理していたスレッドによってコンテキスト オブジェクトの破棄処理が行われます。 応答 (そのハンドラーも含まれる) にかなりの時間がかかり、コンテキスト オブジェクトに基づいた処理が試みられた場合、`Context was disposed` エラーが返されることがあります。 **いずれのアクティビティ呼び出しに対しても必ず `await` を実行**します。これにより、プライマリ スレッドでは生成されたアクティビティで待機してから、その処理が終了され、ターン コンテキストの破棄が行われます。

## <a name="response-event-handlers"></a>応答イベント ハンドラー

ボットおよびミドルウェア ロジックに加えて、応答ハンドラー (イベント ハンドラーやアクティビティ イベント ハンドラーと呼ばれることもある) をコンテキスト オブジェクトに追加することもできます。 これらのハンドラーは、実際の応答が実行される前に、現在のコンテキスト オブジェクト上で関連する応答が発生したときに呼び出されます。 これらのハンドラーは、実際のイベントの前または後で、現在の応答の残りの部分でその種類のすべてのアクティビティのために何かを行う必要があることがわかっているときに便利です。

> [!WARNING]
> アクティビティ応答メソッドを、そのそれぞれの応答イベント ハンドラー内から呼び出さないように注意してください。たとえば、send activity メソッドを _on send activity_ ハンドラー内から呼び出さないようにしてください。 それを行うと、無限ループが生成される可能性があります。

それぞれの新しいアクティビティには、新しいスレッドが与えられ、それぞれ対応するスレッドで実行されます。 アクティビティを処理するスレッドが作成されると、そのアクティビティ用のハンドラー リストが、その新しいスレッドにコピーされます。 そのポイントより後に追加されたハンドラーは、その特定のアクティビティ イベントに対して実行されません。

アダプターでは、[ミドルウェア パイプライン](~/v4sdk/bot-builder-concept-middleware.md#the-bot-middleware-pipeline)を管理する場合とよく似た方法で、コンテキスト オブジェクトに登録されたハンドラーが管理されます。

具体的には、ハンドラーはそれらが追加された順に呼び出され、_next_ デリゲートを呼び出すと、次に登録されているイベント ハンドラーに制御が渡されます。 次のデリゲートがハンドラーによって呼び出されない場合、アダプターによる後続のイベント ハンドラーの呼び出しは行われません。イベントは[ショート サーキット](~/v4sdk/bot-builder-concept-middleware.md#short-circuiting)状態となり、アダプターからチャネルに応答は送信されません。

## <a name="next-steps"></a>次の手順

これでボットのいくつかの主な概念について説明しましたので、次にボットから事前対応型のメッセージを送信する方法を詳細まで掘り下げてみましょう。

> [!div class="nextstepaction"]
> [ミドルウェア](~/v4sdk/bot-builder-concept-middleware.md)