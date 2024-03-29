---
title: ボットをアプリに埋め込む | Microsoft Docs
description: 他のアプリに埋め込まれるボットを設計する方法について説明します。
author: matvelloso
ms.author: mateusv
manager: kamrani
ms.topic: article
ms.service: bot-service
ms.subservice: sdk
ms.date: 08/15/2018
ms.openlocfilehash: 5a0ded9af5f624398df764f16e6dd2db0105255c
ms.sourcegitcommit: a295a90eac461f8b96770dd902ba44919acf33fc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67405874"
---
# <a name="embed-a-bot-in-an-app"></a>ボットをアプリに埋め込む

多くの場合、ボットはアプリの外部に存在しますが、アプリに統合することもできます。 たとえば、複雑なアプリ構造内で検索が困難な情報をユーザーが見つけやすくするために、[ナレッジ ボット](~/bot-service-design-pattern-knowledge-base.md)をアプリに埋め込むことができます。 受信ユーザー要求に対する最初のレスポンダーとして機能するように、ヘルプ デスク アプリにボットを埋め込むこともできます。 簡単な問題はボットが自力で解決し、複雑な問題は人のエージェントに[ハンドオフ](~/bot-service-design-pattern-handoff-human.md)されます。 

## <a name="integrating-bot-with-app"></a>アプリへのボットの統合

アプリとボットを統合する方法はアプリの種類によって異なります。 

### <a name="native-mobile-app"></a>ネイティブ モバイル アプリ

ネイティブ コードで作成されたアプリは、REST または WebSocket 経由で[Direct Line API][directLineAPI] を使用して Bot Framework と通信できます。

### <a name="web-based-mobile-app"></a>Web ベースのモバイル アプリ

Web 言語と、<a href="https://cordova.apache.org/" target="_blank">Cordova</a> などのフレームワークを使用してビルドされたモバイル アプリが Bot Framework と通信するときは、[Web サイトに埋め込まれたボット](~/bot-service-design-pattern-embed-web-site.md)が使用するのと同じコンポーネント、つまりネイティブ アプリのシェル内にカプセル化されているものを使用します。

### <a name="iot-app"></a>IoT アプリ

IoT アプリと Bot Framework の通信には、[Direct Line API][directLineAPI] が使用されます。 シナリオによっては、<a href="https://www.microsoft.com/cognitive-services/" target="_blank">Microsoft Cognitive Services</a> を使って、画像認識や音声などの機能を有効にできます。

### <a name="other-types-of-apps-and-games"></a>その他の種類のアプリとゲーム

その他の種類のアプリやゲームと Bot Framework の通信には、[Direct Line API][directLineAPI] が使用されます。 

## <a name="creating-a-cross-platform-mobile-app-that-runs-a-bot"></a>ボットが実行されるクロスプラットフォーム モバイル アプリの作成

この例では、クロスプラットフォーム モバイル アプリケーションを構築するための一般的ツールである <a href="https://www.xamarin.com/" target="_blank">Xamarin</a> を使用して、ボットが実行されるモバイル アプリを作成します。 

最初に、シンプルな Web ビュー コンポーネントを作成し、それを使って <a href="https://github.com/Microsoft/BotFramework-WebChat" target="_blank">Web チャット コントロール</a>をホストします。 次に、Azure portal を使用して、Web チャット チャネルを追加します。 

次に、登録されている Web チャット URL を、Xamarin アプリ内の Web ビュー コントロールのソースとして指定します。

```cs
public class WebPage : ContentPage
{
    public WebPage()
    {
        var browser = new WebView();
        browser.Source = "https://webchat.botframework.com/embed/<YOUR SECRET KEY HERE>";
        this.Content = browser;
    }
}
```

このプロセスを使用して、Web チャット コントロールを使って、埋め込まれた Web ビューがレンダリングされるクロスプラットフォーム モバイル アプリケーションを作成できます。

![バック チャネル](~/media/bot-service-design-pattern-embed-app/xamarin-apps.png)

<!-- TODO: No sample bot available
## Sample code

For a complete sample that shows how to create a cross-platform mobile app that runs a bot (as described in this article), see the <a href="https://github.com/Microsoft/BotBuilder-Samples/tree/master/CSharp/capability-BotInApps" target="_blank">Bot in Apps sample</a> in GitHub.
-->

## <a name="additional-resources"></a>その他のリソース

- [Direct Line API][directLineAPI]
- <a href="https://www.microsoft.com/cognitive-services/" target="_blank">Microsoft Cognitive Services</a>

[directLineAPI]: https://docs.botframework.com/restapi/directline3/#navtitle
