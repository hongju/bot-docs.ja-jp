---
title: Node.js を使用して Cortana スキルを構築する | Microsoft Docs
description: Bot Framework SDK for Node.js で Cortana スキルを構築するための主要概念について説明します。
keywords: Bot Framework, Cortana スキル, 音声, Node.js, Bot Builder, SDK, 主な概念, 主要概念
author: DeniseMak
manager: kamrani
ms.topic: article
ms.service: bot-service
ms.subservice: sdk
ms.date: 02/10/2019
monikerRange: azure-bot-service-3.0
ms.openlocfilehash: 5de773f6f8f4d46c0c1fe880588f2530c3c68f56
ms.sourcegitcommit: 721bb09f10524b0cb3961d7131966f57501734b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59746066"
---
# <a name="key-concepts-for-building-a-bot-for-cortana-skills-using-nodejs"></a>Node.js を使用して Cortana スキル用のボットを構築するための主要概念
 
[!INCLUDE [pre-release-label](../includes/pre-release-label-v3.md)]

> [!NOTE]
> この記事は暫定的コンテンツであり、更新されます。

この記事では、Bot Framework SDK for Node.js で Cortana スキルを構築するための主な概念を紹介します。 

## <a name="what-is-a-cortana-skill"></a>Cortana スキルとは
Cortana スキルは、Windows 10 に組み込まれているのと同様に、Cortana クライアントを使用して呼び出すことができるボットです。 ユーザーは、ボットに関連付けられている何らかのキーワードまたはフレーズを発話することで、ボットを起動します。 Bot Framework Portal を使用して、ボットの起動に使用するキーワードを構成できます。 

Cortana は、テキストによる会話だけでなく、音声メッセージも送受信できる音声認識対応チャネルと考えることができます。 Cortana スキルとして発行するボットは、音声およびテキストに対応するよう設計する必要があります。 Bot Framework は、ボットが送信する音声メッセージを定義するために、音声合成マークアップ言語 (SSML) を指定するためのメソッドを提供します。

## <a name="acknowledge-user-utterances"></a>ユーザーの発話を確認する 

<!-- Establishing conversational understanding -->
<!-- Placeholder: In this section, describe how you have to write your speech to sound natural -->


音声認識に対応したボットを作成する際には、会話における共通の基盤と相互理解を確立するよう試みる必要があります。 ボットは、ユーザーの発話が聞こえて理解できたことを示すことで、ユーザーの発話を "着地" させる必要があります。

システムで発話を着地させることができなければ、ユーザーは混乱します。 たとえば、ボットが "次は何ですか" とたずねた場合、以下の会話は多少の混乱を招きます。

> **Cortana**: プロフィールの詳細を確認しますか?  
> **User**:いいえ。  
> **Cortana**: 次の手順

ボットが "わかりました" と確認の言葉を加えると、ユーザーはより明確に理解できます。

> **Cortana**: プロフィールの詳細を確認しますか?  
> **User**:いいえ。  
> **Cortana**: **わかりました。** 次は何ですか?

着地の度合いは、最も弱いものから最も強いものの順に、以下のようになります。

1. 持続的な関心
2. 次を示唆する発言
3. 確認:最小限の応答やあいづち: "はい"、"ええ"、"わかりました"、"いいですね"
4. デモンストレーション:再構成、補完によって理解を示す。
5. ディスプレイ:全部または一部を繰り返す。

### <a name="acknowledgement-and-next-relevant-contribution"></a>確認と、次を示唆する発言

> **User**:5 月に出張する必要があります。  
> **Cortana**: **わかりました**。 5 月の何日に出張しますか?  
> **User**:えっと、12 日から 15 日までです。  
> **Cortana**: **わかりました**。 どの都市に出張しますか?  

### <a name="grounding-by-demonstration"></a>デモンストレーションによる着地

> **User**:5 月に出張する必要があります。  
> **Cortana**: では、5 月**何日**に出張しますか。  
> **User**:そうですね、12 日から 15 日までです。  
> **Cortana**: **では**、どの都市に出張しますか?  
    
### <a name="closure"></a>クロージャ

アクションを実行しているボットは、正常なパフォーマンスの証拠を提示する必要があります。 また、失敗や理解を示すことも重要です。 

* 非音声クロージャ:エレベーターのボタンを押すと、ライトが点灯する。  
これは次の 2 段階のプロセスです。
    * プレゼンテーション (ボタンを押したとき)
    * 承認 (ボタンのライトが点灯したとき)

## <a name="differences-in-content-presentation"></a>コンテンツのプレゼンテーションの違い
Cortana はさまざまなデバイスでサポートされていますが、画面を備えているのはその一部だけであることに注意してください。 音声対応のボットを設計する際に考慮する必要がある点の 1 つは、音声での対話はボットに表示されるテキスト メッセージと異なることが多いという点です。
<!-- If there are differences in what the bot will say, in the text vs the speak fields of a prompt or in a waterfall, for example, discuss them here.

## Speech

You bot uses the **session.say** method to speak to the user. The speak method has three overloads:
* If you pass only one parameter to **session.say**, it can be a text parameter.
* If you pass two parameters to **session.say**, it can take text and SSML.
* If you pass three parameters, the third parameter takes an options structure that specifies all the options you can pass to build an **IMessage** object.

```javascript
var bot = new builder.UniversalBot(connector, function (session) {
    session.say("Hello... I'm a decision making bot.'.", 
        ssml.speak("Hello. I can help you answer all of life's tough questions."));
    session.replaceDialog('rootMenu');
});

```
## Speech in messages

The **IMessage** object provides a **speak** property for SSML. It can be used to play a .wav file.

The **inputHint** property helps indicate to Cortana whether your bot is expecting input. If you're using a built-in prompt, this value is automatically set to the default of **expectingInput**.

The **inputHint** property can take the following values: 
* **expectingInput**: Indicates that the bot is actively expecting a response from the user. Cortana listens for the user to speak into the microphone.
* **acceptingInput**: Indicates that the bot is passively ready for input but is not waiting on a response. Cortana accepts input from the user if the user holds down the microphone button.
* **ignoringInput**: Cortana is ignoring input. Your bot may send this hint if it is actively processing a request and will ignore input from users until the request is complete.

Prompts must use the `speak:` option.

```javascript
        builder.Prompts.choice(session, "Decision Options", choices, {
            listStyle: builder.ListStyle.button,
            speak: ssml.speak("How would you like me to decide?")
        });
```

Prompts.number has *ordinal support*, meaning that you can say "the last", "the first", "the next-to-last" to choose an item in a list.

## Using synonyms

<!-- Axl Rose example -->
```javascript   
         var choices = [
            { 
                value: 'flipCoinDialog',
                action: { title: "Flip A Coin" },
                synonyms: 'toss coin|flip quarter|toss quarter'
            },
            {
                value: 'rollDiceDialog',
                action: { title: "Roll Dice" },
                synonyms: 'roll die|shoot dice|shoot die'
            },
            {
                value: 'magicBallDialog',
                action: { title: "Magic 8-Ball" },
                synonyms: 'shake ball'
            },
            {
                value: 'quit',
                action: { title: "Quit" },
                synonyms: 'exit|stop|end'
            }
        ];
        builder.Prompts.choice(session, "Decision Options", choices, {
            listStyle: builder.ListStyle.button,
            speak: ssml.speak("How would you like me to decide?")
        });
```

## <a name="configuring-your-bot"></a>ボットの構成

## <a name="prompts"></a>プロンプト

## <a name="additional-resources"></a>その他のリソース

Cortana のドキュメント: [Cortana Skills のドキュメント](/cortana/skills/)

Cortana SSML リファレンス: [音声合成マークアップ言語 (SSML) リファレンス](/cortana/skills/speech-synthesis-markup-language)
