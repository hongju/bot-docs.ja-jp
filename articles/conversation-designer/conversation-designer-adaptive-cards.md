---
title: アダプティブ カードの構成 | Microsoft Docs
description: アダプティブ カードを構成する方法について説明します。
author: vkannan
manager: kamrani
ms.topic: article
ms.service: bot-service
ms.date: 12/13/2017
ROBOTS: NoIndex, NoFollow
ms.openlocfilehash: fee70da7288b3214ff7f384998a69b40f91b3226
ms.sourcegitcommit: dbbfcf45a8d0ba66bd4fb5620d093abfa3b2f725
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67464517"
---
# <a name="configure-adaptive-cards"></a>アダプティブ カードの構成
> [!IMPORTANT]
> Conversation Designer は、一部のお客様はまだご利用いただけません。 Conversation Designer の可用性の詳細については、今年中に提供される予定です。

<a href="http://adaptivecards.io" target="_blank">アダプティブ カード</a>は、高機能な UI カードを定義する新しいスキーマで、Microsoft Bot Framework のチャネルなどのさまざまなエンドポイントで使用できます。 

Conversation Designer は、ボットでアダプティブ カードを作成、プレビュー、および使用するための密接に統合されたオーサリング環境を提供します。 

アダプティブ カードは、さまざまな重要な場所で定義できます。

- タスクのアクションに対する単純な応答。
- ダイアログのフィードバック状態。
- ダイアログのプロンプト状態。 プロンプトには別のカードが存在する場合があることに注意してください。1 つは応答用で、もう 1 つは再プロンプト用です。

アダプティブのカードを定義するには、関連するエディターに移動します。 いずれかの既存のアダプティブ カード テンプレートを参照して選択するか、JSON コード エディターを使って独自に作成します。 

カードを作成する際には、オーサリング ポータルにカードの高度なプレビューが表示されます。

> [!NOTE]
> アダプティブ カードの機能は、そのまま継続して開発できます。 現時点では、すべてのチャネルがすべてのアダプティブ カードの機能をサポートしているわけではありません。 各チャネル機能でサポートされている機能については、「チャネルの状態」セクションを参照してください。

## <a name="input-form"></a>入力フォーム

アダプティブ カードには、入力フォームを含めることができます。 Conversation Designer では、フォームはタスクのエンティティと統合されています。 たとえば、フィールドに **myName** の `id` があり、フォームの `Submit` アクションが実行された場合、**myName** という名前の `taskEntity` が作成され、そのフィールドの値が含まれます。 

次のコード スニペットでは、コードで **myName** エンティティを定義する方法を示しています。

```javascript
{
   "type": "Input.Text",
   "id": "myName",
   "placeholder": "Last, First"
}
```

さらに、フィールドに `@task` の ID がある場合、フィールドの値がタスク名として使用されます。 このフィールドがトリガーされると (例: ボタンのクリック)、名前付きのタスクが実行されます。 

次のスニペットのコードを例にとってみましょう。

```javascript
{
  'type': 'Action.Submit',
  'title': 'Search',
  'speak': '<s>Search</s>',
  'data': {
    '@task': 'Hotel Search'
  }
}
```

このボタンがクリックされたときに、送信アクションがトリガーされ、`context.sticky` が `Hotel Search` に設定されます。 その結果、**ホテル検索**タスクが実行されます。 この機能を使用するには、`@task` が Conversation Designer で定義したタスク名に一致することを確認します。

## <a name="use-entities-and-language-generation-templates"></a>エンティティと言語生成テンプレートの使用
アダプティブ カードは、完全な言語生成の解決をサポートします。

* `entityName` は、カード内のエンティティを使用します。
* `responseTemplateName` は、カード内の単純な応答テンプレートや条件付き応答テンプレートを使用します。

アダプティブ カードの詳細については、こちらの TODO を参照してください:アダプティブ カードのスキーマ ドキュメントへのリンクを挿入 -->

## <a name="sample-adaptive-card-payload"></a>アダプティブ カードのペイロードのサンプル

次の JSON は、アダプティブのカードのペイロードを示しています。

```json
{
    "$schema": "https://microsoft.github.io/AdaptiveCards/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "speak": "<s>Serious Pie is a Pizza restaurant which is rated 9.3 by customers.</s>",
            "type": "ColumnSet",
            "columns": [
                {
                    "type": "Column",
                    "size": "2",
                    "items": [
                        {
                            "type": "TextBlock",
                            "text": "[Greeting], [TimeOfDayTemplate], You can eat in {location}",
                            "weight": "bolder",
                            "size": "extraLarge"
                        },
                        {
                            "type": "TextBlock",
                            "text": "9.3 · $$ · Pizza",
                            "isSubtle": true
                        },
                        {
                            "type": "TextBlock",
                            "text": "[builtin.feedback.display]",
                            "wrap": true
                        }
                    ]
                },
                {
                    "type": "Column",
                    "size": "1",
                    "items": [
                        {
                            "type": "Image",
                            "url": "http://res.cloudinary.com/sagacity/image/upload/c_crop,h_670,w_635,x_0,y_0/c_scale,w_640/v1397425743/Untitled-4_lviznp.jpg",
                            "size":"auto"
                        }
                    ]
                }
            ]
        }
    ],
    "actions": [
        {
            "type": "Action.Http",
            "method": "POST",
            "title": "More Info",
            "url": "http://foo.com"
        },
        {
            "type": "Action.Http",
            "method": "POST",
            "title": "View on Foursquare",
            "url": "http://foo.com"
        }
    ]
}
```

