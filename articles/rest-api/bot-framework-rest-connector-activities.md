---
title: アクティビティの概要 | Microsoft Docs
description: Bot Connector サービス内で使用できるさまざまなアクティビティの種類について説明します。
author: RobStand
ms.author: kamrani
manager: kamrani
ms.topic: article
ms.prod: bot-framework
ms.date: 12/13/2017
ms.openlocfilehash: cf8da2240df7edbb6ea8c858829e71089b7e72cb
ms.sourcegitcommit: f576981342fb3361216675815714e24281e20ddf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39304153"
---
# <a name="activities-overview"></a>アクティビティの概要

Bot Connector サービスは、[Activity][Activity] オブジェクトを渡すことによって、ボットとチャンネル (ユーザー) 間で情報を交換します。 アクティビティの最も一般的な種類は **message** ですが、さまざまな種類の情報をボットまたはチャネルに伝達するために使用できる他のアクティビティの種類もあります。 

## <a name="activity-types-in-the-bot-connector-service"></a>Bot Connector サービスのアクティビティの種類

次のアクティビティの種類は、Bot Connector サービスでサポートされています。

| アクティビティの種類 | 説明 |
|------|------|------|
| message | ボットとユーザー間の通信を表します。 |
| conversationUpdate | ボットが会話に追加されたこと、他のメンバーが会話に追加された、または会話から削除されたこと、会話のメタデータが変更されたことを示します。 |
| contactRelationUpdate | ユーザーの連絡先リストに対してボットが追加または削除されたことを示します。 |
| typing | 会話の相手側のユーザーまたはボットが応答をコンパイルしていることを示します。 | 
| ping | ボットのエンドポイントがアクセス可能かどうかを判断しようとしていることを表します。 | 
| deleteUserData | ボットに保存されている可能性のあるユーザー データを削除するようにユーザーが要求したことをボットに示します。 |
| endOfConversation | 会話の終了を示します。 |

## <a name="message"></a>message

ボットは、**message** アクティビティを送信してユーザーに情報を伝達し、ユーザーから **message** アクティビティを受信します。 メッセージはプレーンテキストの場合もあれば、[メディアの添付ファイル](bot-framework-rest-connector-add-media-attachments.md)、[ボタンやカード](bot-framework-rest-connector-add-rich-cards.md)、または[チャネル固有のデータ](bot-framework-rest-connector-channeldata.md)など、よりリッチなコンテンツを含む場合もあります。 一般的に使用されるメッセージのプロパティについては、「[メッセージの作成](bot-framework-rest-connector-create-messages.md)」をご参照ください。 メッセージを送受信する方法については、「[メッセージの送受信](bot-framework-rest-connector-send-and-receive-messages.md)」をご参照ください。 

## <a name="conversationupdate"></a>conversationUpdate

ボットは、ボットが会話に追加されたり、他のメンバーが会話に追加または会話から削除されたり、会話メタデータが変更されたりするたびに、**conversationUpdate** アクティビティを受信します。 

メンバーが会話に追加された場合、アクティビティの `addedMembers` プロパティは新しいメンバーを識別します。 メンバーが会話から削除された場合、アクティビティの `removedMembers` プロパティは削除されたメンバーを識別します。 

> [!TIP]
> ユーザーが会話に参加したことを示す **conversationUpdate** アクティビティをボットが受信した場合、そのユーザーにウェルカム メッセージを送信して応答することを選択できます。 

## <a name="contactrelationupdate"></a>contactRelationUpdate

ボットがユーザーの連絡先リストに対して追加または削除されるたびに、ボットは **contactRelationUpdate** アクティビティを受信します。 アクティビティの `action` プロパティ (追加 | 削除) の値は、ボットがユーザーの連絡先リストに対して追加または削除されているかを示します。

## <a name="typing"></a>typing

ボットは **typing** アクティビティを受信して、ユーザーが応答を入力中であることを示します。 ボットは、**typing** アクティビティを送信して、要求を満たすため、または応答をコンパイルするためにボットが動作中であることをユーザーに示すことがあります。 

## <a name="ping"></a>ping

ボットは **ping** アクティビティを受信して、エンドポイントにアクセス可能かどうかを判断します。 ボットは、HTTP 状態コード 200 (OK)、403 (許可されていません) または 401 (権限がありません) で応答する必要があります。

## <a name="deleteuserdata"></a>deleteUserData

ボットは、ボットが以前に保持していたユーザーのデータを削除するようにユーザーが要求すると、**deleteUserData** アクティビティを受信します。 ボットがこの種類のアクティビティを受信した場合、ボットはその要求を実行したユーザー用に以前保存した個人を特定できる情報 (PII) を削除する必要があります。

## <a name="endofconversation"></a>endOfConversation 

ボットは **endOfConversation** アクティビティを受信して、ユーザーが会話を終了したことを示します。 ボットは **endOfConversation** アクティビティを送信して、ユーザーが会話を終了したことを示すことがあります。 

## <a name="additional-resources"></a>その他のリソース

- [メッセージの作成](bot-framework-rest-connector-create-messages.md)
- [メッセージを送受信する](bot-framework-rest-connector-send-and-receive-messages.md)

[Activity]: bot-framework-rest-connector-api-reference.md#activity-object