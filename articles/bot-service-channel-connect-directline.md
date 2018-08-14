---
title: ボットを Direct Line に接続する | Microsoft Docs
description: Direct Line へのボットの接続を構成する方法について説明します。
keywords: Direct Line, ボット チャネル, カスタム クライアント, チャネルへの接続, 構成
author: RobStand
ms.author: kamrani
manager: kamrani
ms.topic: article
ms.prod: bot-framework
ms.date: 03/08/2018
ms.openlocfilehash: 2ec11c4cc0e12b6a130b2f703f30660c4bc9f072
ms.sourcegitcommit: f95702d27abbd242c902eeb218d55a72df56ce56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39304665"
---
# <a name="connect-a-bot-to-direct-line"></a>ボットを Direct Line に接続する

Direct Line チャネルを使用することによって、独自のクライアント アプリケーションとボットの通信を有効にできます。 

## <a name="add-the-direct-line-channel"></a>Direct Line チャネルを追加する

Direct Line チャネルを追加するには、[Azure portal](https://portal.azure.com/) でボットを開き、**[チャネル]** ブレードをクリックして、**[Direct Line]\(Direct Line\)** をクリックします。

![Direct Line チャネルを追加する](~/media/bot-service-channel-connect-directline/directline-addchannel.png)

## <a name="add-new-site"></a>新しいサイトを追加する

次に、ボットに接続するクライアント アプリケーションを表す新しいサイトを追加します。 **[Add new site]\(新しいサイトの追加\)** をクリックし、サイトの名前を入力して、**[完了]** をクリックします。

![Direct Line サイトを追加する](~/media/bot-service-channel-connect-directline/directline-addsite.png)

## <a name="manage-secret-keys"></a>秘密鍵を管理する

サイトが作成されると、Bot Framework によって秘密鍵が生成されます。クライアント アプリケーションは、この秘密鍵を使って、ボットと通信するために発行する Direct Line API 要求の[認証](~/rest-api/bot-framework-rest-direct-line-3-0-authentication.md)を行うことができます。 鍵をプレーン テキストで表示するには、対応する鍵の **[表示]** をクリックします。

![Direct Line の鍵を表示する](~/media/bot-service-channel-connect-directline/directline-showkey.png)

表示された鍵をコピーし、安全に保管します。 その後、この鍵を使って、クライアントがボットと通信するために発行する Direct Line API 要求を[認証](~/rest-api/bot-framework-rest-direct-line-3-0-authentication.md)します。
または、Direct Line API を使って[鍵をトークンと交換](~/rest-api/bot-framework-rest-direct-line-3-0-authentication.md#generate-token)します。クライアントはこのトークンを使って、1 つの会話のスコープ内で後続の要求を認証できます。

![Direct Line の鍵をコピーする](~/media/bot-service-channel-connect-directline/directline-copykey.png)

## <a name="configure-settings"></a>設定を構成する

最後に、サイトの設定を構成します。

- クライアント アプリケーションがボットとの通信に使用する Direct Line プロトコルのバージョンを選択します。

> [!TIP]
> クライアント アプリケーションとボットの間の新しい接続を作成する場合は、Direct Line API 3.0 を使います。

終わったら、**[完了]** をクリックしてサイトの構成を保存します。 ボットに接続するクライアント アプリケーションごとに、このプロセスを [[Add new site]\(新しいサイトの追加\)](#add-new-site) から繰り返すことができます。