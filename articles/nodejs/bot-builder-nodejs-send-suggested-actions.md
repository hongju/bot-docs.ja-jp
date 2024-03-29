---
title: メッセージへの推奨されるアクションの追加 | Microsoft Docs
description: Bot Framework SDK for Node.js を使用してメッセージ内で推奨されるアクションを送信する方法について説明します。
author: v-ducvo
ms.author: kamrani
manager: kamrani
ms.topic: article
ms.service: bot-service
ms.subservice: sdk
ms.date: 02/19/2019
monikerRange: azure-bot-service-3.0
ms.openlocfilehash: 04be50ce490f81f27df9190561d8a4174089357c
ms.sourcegitcommit: a295a90eac461f8b96770dd902ba44919acf33fc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67404783"
---
# <a name="add-suggested-actions-to-messages"></a>メッセージへの推奨されるアクションの追加

[!INCLUDE [pre-release-label](../includes/pre-release-label-v3.md)]

> [!div class="op_single_selector"]
> - [.NET](../dotnet/bot-builder-dotnet-add-suggested-actions.md)
> - [Node.JS](../nodejs/bot-builder-nodejs-send-suggested-actions.md)
> - [REST](../rest-api/bot-framework-rest-connector-add-suggested-actions.md)

[!INCLUDE [Introduction to suggested actions](../includes/snippet-suggested-actions-intro.md)]

## <a name="suggested-actions-example"></a>推奨されるアクションの例

推奨されるアクションをメッセージに追加するには、メッセージの `suggestedActions` プロパティを、ユーザーに表示されるボタンを表す[カード アクション][ICardAction]の一覧に設定します。

次のコード例は、3 つの推奨されるアクションをユーザーに提示するメッセージの送信方法を示しています。

[!code-javascript[Send suggested actions](../includes/code/node-send-suggested-actions.js#sendSuggestedActions)]

ユーザーが推奨されるアクションのいずれかをタップすると、対応するアクションの `value` を含むメッセージがユーザーからボットに送信されます。

`value` は、`imBack` メソッドによって、使用しているチャネルのチャット ウィンドウに投稿されることに注意してください。 この結果を望まない場合は、`postBack` メソッドを使用できます。これにより選択内容がご自身のボットにポスト バックされますが、選択内容はチャット ウィンドウに表示されません。 ただし、一部のチャネルでは `postBack` がサポートされていません。この場合、このメソッドは `imBack` と同じように動作します。

## <a name="additional-resources"></a>その他のリソース

- [サンプル][samples]
- [IMessage][IMessage]
- [ICardAction][ICardAction]
- [session.send][SessionSend]

[IMessage]: http://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.imessage

[SessionSend]: https://docs.botframework.com/node/builder/chat-reference/classes/_botbuilder_d_.session.html#send

[ICardAction]: https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.icardaction.html

<!-- The inspector is no longer supported: we're redirecting to the samples for now. -->
[samples]: https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples
