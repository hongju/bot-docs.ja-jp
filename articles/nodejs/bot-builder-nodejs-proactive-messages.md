---
title: プロアクティブ メッセージを送信する | Microsoft Docs
description: Bot Builder SDK for Node.js を使用して、現在の会話フローをプロアクティブ メッセージで中断する方法について説明します
author: v-ducvo
ms.author: v-ducvo
manager: kamrani
ms.topic: article
ms.prod: bot-framework
ms.date: 12/13/2017
monikerRange: azure-bot-service-3.0
ms.openlocfilehash: f432a570f5a8393a2aef3e4ec97c5e7e8cbaa43f
ms.sourcegitcommit: f576981342fb3361216675815714e24281e20ddf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39303284"
---
# <a name="send-proactive-messages"></a>プロアクティブ メッセージを送信する
> [!div class="op_single_selector"]
> - [.NET](../dotnet/bot-builder-dotnet-proactive-messages.md)
> - [Node.js](../nodejs/bot-builder-nodejs-proactive-messages.md)

[!INCLUDE [Introduction to proactive messages - part 1](../includes/snippet-proactive-messages-intro-1.md)]

## <a name="types-of-proactive-messages"></a>プロアクティブ メッセージの種類

[!INCLUDE [Introduction to proactive messages - part 2](../includes/snippet-proactive-messages-intro-2.md)]

## <a name="send-an-ad-hoc-proactive-message"></a>アドホック プロアクティブ メッセージを送信する

次のサンプル コードは、Bot Builder SDK for Node.js を使用して、アドホック プロアクティブ メッセージを送信する方法を示しています。

アドホック メッセージをユーザーに送信できるようにするには、ボットは、現在の会話からユーザーに関する情報を収集して保存しておく必要があります。 メッセージの **address** プロパティには、ボットが後でユーザーにアドホック メッセージを送信するために必要なすべての情報が含まれます。 

```javascript
bot.dialog('adhocDialog', function(session, args) {
    var savedAddress = session.message.address;

    // (Save this information somewhere that it can be accessed later, such as in a database, or session.userData)
    session.userData.savedAddress = savedAddress;

    var message = 'Hello user, good to meet you! I now know your address and can send you notifications in the future.';
    session.send(message);
})
```

> [!NOTE]
> ユーザー データは、ボットが後でアクセスできる限り、任意の方法で格納できます。

ユーザーに関する情報を収集した後、ボットは、アドホック プロアクティブ メッセージをユーザーにいつでも送信できます。 これを行うには、格納済みのユーザー データを取得し、メッセージを作成して送信します。

```javascript
var inMemoryStorage = new builder.MemoryBotStorage();

var bot = new builder.UniversalBot(connector)
                .set('storage', inMemoryStorage); // Register in-memory storage 

function sendProactiveMessage(address) {
    var msg = new builder.Message().address(address);
    msg.text('Hello, this is a notification');
    msg.textLocale('en-US');
    bot.send(msg);
}
```

> [!TIP]
> アドホック プロアクティブ メッセージは、HTTP 要求、タイマー、キューなどの非同期トリガーや開発者が選択した他の場所から開始できます。

## <a name="send-a-dialog-based-proactive-message"></a>ダイアログ ベースのプロアクティブ メッセージを送信する

次のサンプル コードは、Bot Builder SDK for Node.js を使用して、ダイアログ ベースのプロアクティブ メッセージを送信する方法を示しています。 完全な作業例は、[Microsoft/BotBuilder-Samples/Node/core-proactiveMessages/startNewDialog](https://github.com/Microsoft/BotBuilder-Samples/tree/master/Node/core-proactiveMessages/startNewDialog) フォルダーで見つけることができます。

ダイアログ ベースのアドホック メッセージをユーザーに送信できるようにするには、ボットは、現在の会話からの情報の収集 (および保存) を行っておく必要があります。 `session.message.address` オブジェクトには、ボットがダイアログ ベースのプロアクティブ メッセージをユーザーに送信するために必要なすべての情報が含まれます。 

```javascript
// proactiveDialog dialog
bot.dialog('proactiveDialog', function (session, args) {

    savedAddress = session.message.address;

    var message = 'Hey there, I\'m going to interrupt our conversation and start a survey in five seconds...';
    session.send(message);

    message = `You can also make me send a message by accessing: http://localhost:${server.address().port}/api/CustomWebApi`;
    session.send(message);

    setTimeout(() => {
        startProactiveDialog(savedAddress);
    }, 5000);
});
```

メッセージを送信するときが来たら、ボットは、新しいダイアログを作成して、ダイアログ スタックの先頭に追加します。 新しいダイアログが会話を制御し、プロアクティブ メッセージを配信した後、スタック内の前のダイアログに制御を戻します。 

```javascript
// initiate a dialog proactively 
function startProactiveDialog(address) {
    bot.beginDialog(address, "*:survey");
}
```

> [!NOTE]
> 上記のコード サンプルでは、カスタム ファイル **botadapter.js**が必要です。これは [GitHub からダウンロード](https://github.com/Microsoft/BotBuilder-Samples/blob/master/Node/core-proactiveMessages/startNewDialog/botadapter.js)できます。

調査ダイアログは、会話が終わるまでそれを制御します。 その後、ダイアログは (`session.endDialog()` の呼び出しによって) 閉じ、それによって前のダイアログに制御が戻ります。 


```javascript
// handle the proactive initiated dialog
bot.dialog('survey', function (session, args, next) {
  if (session.message.text === "done") {
    session.send("Great, back to the original conversation");
    session.endDialog();
  } else {
    session.send('Hello, I\'m the survey dialog. I\'m interrupting your conversation to ask you a question. Type "done" to resume');
  }
});
```

## <a name="sample-code"></a>サンプル コード

Bot Builder SDK for Node.js を使用してプロアクティブ メッセージを送信する方法を示す完全なサンプルについては、GitHub で<a href="https://github.com/Microsoft/BotBuilder-Samples/tree/master/Node/core-proactiveMessages" target="_blank">プロアクティブ メッセージの例</a>を参照してください。 プロアクティブ メッセージの例の中では、<a href="https://github.com/Microsoft/BotBuilder-Samples/tree/master/Node/core-proactiveMessages/simpleSendMessage" target="_blank">simpleSendMessage</a> がアドホック プロアクティブ メッセージの送信方法を示し、<a href="https://github.com/Microsoft/BotBuilder-Samples/tree/master/Node/core-proactiveMessages/startNewDialog" target="_blank">startNewDialog</a> がダイアログ ベースのプロアクティブ メッセージの送信方法を示しています。

## <a name="additional-resources"></a>その他のリソース

- [会話フローの設計](../bot-service-design-conversation-flow.md)