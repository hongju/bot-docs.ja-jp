---
title: メッセージへの推奨されるアクションの追加 | Microsoft Docs
description: Bot Connector サービスを使用して、推奨されるアクションをメッセージに追加する方法について説明します。
author: RobStand
ms.author: kamrani
manager: kamrani
ms.topic: article
ms.service: bot-service
ms.subservice: sdk
ms.date: 12/13/2017
ms.openlocfilehash: 346c522a1e1cd3d5904b74ad6e6092a1457a001c
ms.sourcegitcommit: f84b56beecd41debe6baf056e98332f20b646bda
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2019
ms.locfileid: "65032589"
---
# <a name="add-suggested-actions-to-messages"></a>メッセージへの推奨されるアクションの追加
> [!div class="op_single_selector"]
> - [.NET](../dotnet/bot-builder-dotnet-add-suggested-actions.md)
> - [Node.js](../nodejs/bot-builder-nodejs-send-suggested-actions.md)
> - [REST](../rest-api/bot-framework-rest-connector-add-suggested-actions.md)

[!INCLUDE [Introduction to suggested actions](../includes/snippet-suggested-actions-intro.md)]

## <a name="send-suggested-actions"></a>推奨されるアクションの送信

推奨されるアクションをメッセージに追加するには、[Activity][Activity] の `suggestedActions` プロパティを設定して、ユーザーに表示されるボタンを表す [CardAction][CardAction] オブジェクトのリストを指定します。 

次の要求では、3 つの推奨されるアクションをユーザーに提示するメッセージが送信されます。 この要求の例で、`https://smba.trafficmanager.net/apis` はベース URI を示しています。ご利用のボットによって発行される要求に対するベース URI は、これとは異なる場合があります。 ベース URI の設定の詳細については、[API リファレンス](bot-framework-rest-connector-api-reference.md#base-uri)に関する記事をご覧ください。

```http
POST https://smba.trafficmanager.net/apis/v3/conversations/abcd1234/activities/5d5cdc723
Authorization: Bearer ACCESS_TOKEN
Content-Type: application/json
```

```json
{
    "type": "message",
    "from": {
        "id": "12345678",
        "name": "sender's name"
    },
    "conversation": {
        "id": "abcd1234",
        "name": "conversation's name"
   },
   "recipient": {
        "id": "1234abcd",
        "name": "recipient's name"
    },
    "text": "I have colors in mind, but need your help to choose the best one.",
    "inputHint": "expectingInput",
    "suggestedActions": {
        "actions": [
            {
                "type": "imBack",
                "title": "Blue",
                "value": "Blue"
            },
            {
                "type": "imBack",
                "title": "Red",
                "value": "Red"
            },
            {
                "type": "imBack",
                "title": "Green",
                "value": "Green"
            }
        ]
    },
    "replyToId": "5d5cdc723"
}
```

ユーザーが推奨されるアクションのいずれかをタップすると、対応するアクションの `value` を含むメッセージがユーザーからボットに送信されます。

## <a name="additional-resources"></a>その他のリソース

- [メッセージの作成](bot-framework-rest-connector-create-messages.md)
- [メッセージを送受信する](bot-framework-rest-connector-send-and-receive-messages.md)

[channelInspector]: ../bot-service-channel-inspector.md

[Activity]: bot-framework-rest-connector-api-reference.md#activity-object

[CardAction]: bot-framework-rest-connector-api-reference.md#cardaction-object

[SuggestedAction]: bot-framework-rest-connector-api-reference.md#suggestedactions-object
