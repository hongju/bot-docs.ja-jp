---
title: ボット設計の原則 | Microsoft Docs
description: 適切な会話ボットとは何か、また、ユーザーが満足し、ご自身のニーズにも合ったボットを計画および設計する方法について説明します。
keywords: ベスト プラクティス, ボットの設計
author: matvelloso
ms.author: mateusv
manager: kamrani
ms.topic: article
ms.service: bot-service
ms.subservice: sdk
ms.date: 12/13/2017
ms.openlocfilehash: 3ac767e525c1082005f4521af9e9714dd8c39cff
ms.sourcegitcommit: b78fe3d8dd604c4f7233740658a229e85b8535dd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2018
ms.locfileid: "49998519"
---
# <a name="principles-of-bot-design"></a>ボット設計の原則

Bot Framework を使用すると、開発者が、さまざまなビジネス上の問題を解決する説得力のあるボット エクスペリエンスを作成できます。 このセクションで説明する概念を学習することで、ベスト プラクティスに沿ったボットを、比較的新しいこの分野でこれまで学んだ教訓を生かして設計する準備が整います。 

## <a name="designing-a-bot"></a>ボットの設計

ボットを構築する場合は、ユーザーがそのボットを使ってくれることを想定するでしょう。 また、ユーザーが、アプリ、Web サイト、特定のニーズに対処するための手段として、電話などの他のエクスペリエンスよりも、ボットでのエクスペリエンスを好んで欲しいと期待するのも当然です。 つまり、ご自身のボットは、ユーザーの時間をめぐってアプリや Web サイトなどと競い合っているのです。 では、ボットでユーザーを引き付け、そのまま魅了し続けるという最終的な目標を達成する可能性を最大限に高めるには、どうすればよいのでしょうか。 これは単にボットを設計するときに、適切な要因を優先させればいいだけです。

## <a name="factors-that-do-not-guarantee-a-bots-success"></a>ボットの成功要因になるとは限らないもの

ボットを設計するとき、以下がボットの成功要因にはなるとは限らない点に注意してください。 

- **ボットが "賢い" こと**: ご自身のボットをいくら賢くしても、それによってユーザーが満足し、ボットをプラットフォームに導入するとは限らないでしょう。 実際、高度な機械学習や自然言語の機能をほとんど備えていないボットは多数存在します。 問題を解決するうえでこれらの機能が必要で、ボットがその問題を対処するように設計されている場合は、これらの機能がボットに含まれていることもあるでしょう。それでも、ボットのインテリジェンスと、ユーザーによるボット導入の間に相関関係はないと思ってください。

- **ボットがサポートする自然言語の量**: お使いのボットが会話能力に優れていることもあります。 ボキャブラリが豊富で、ジョークを言うこともできます。 しかし、ユーザーが解決しなければならない問題がボットで対処されなければ、これらの機能は、ボットを成功させるうえでほとんど役に立たないでしょう。 実際、ボットの中には会話機能がまったく搭載されてないものがあります。 そして、多くの場合、それでもまったく問題がありません。

- **音声**: ボットで音声に対応できるようにしても、優れたユーザー エクスペリエンスにつながるとは限りません。 音声を無理に使わなければならない状況を、ユーザーがストレスに感じることも少なくありません。 ご自身のボットを設計するときは、音声が、該当する問題に適したチャネルであるかどうかを必ず検討してください。 使用環境が騒がしくなる可能性はありませんか。 共有する必要がある情報が、音声でユーザーに伝わりますか。 

## <a name="factors-that-do-influence-a-bots-success"></a>ボットの成功に影響を及ぼす要因

成功したアプリまたは Web サイトのほとんどに共通する点が少なくとも 1 つあります。それは優れたユーザー エクスペリエンスです。 その点ではボットもまったく同じです。 したがって、ボットを設計するときは、優れたユーザー エクスペリエンスを確保することが最優先事項になります。 考慮事項として他に重要なものを次に示します。

- ユーザーの問題は、ボットによって最小限の手順で簡単に解決されますか。

- ユーザーの問題は、ボットによって、他のどのエクスペリエンスよりも適切/簡単/迅速に解決されますか。

- ボットは、ユーザーが使用するデバイスやプラットフォームで動作しますか。

- ボットは探索可能ですか。 ボットを使用するときの操作をユーザーが自然に把握できますか。

これらの質問はいずれも、ボットの賢さ、自然言語能力、機械学習を使用しているかどうか、ボットの作成時に使用されたプログラミング言語などの要因とは直接は関係ありません。 ユーザーが対処する必要がある問題がボットで解決され、ボットのユーザー エクスペリエンスが優れていれば、これらの要因をユーザーが気にするとはないでしょう。 ユーザー エクスペリエンスが優れていれば、ユーザーが、無駄に入力したり、話したり、操作を繰り返したり、ボットで自動的に認識するべきことを説明したりする必要はありません。

> [!TIP]
> 作成しているアプリケーションの種類 (ボット、Web サイト、またはアプリ) に関係なく、ユーザー エクスペリエンスを最優先させてください。

ボットを設計するプロセスは、アプリや Web サイトを設計するプロセスと似ているため、UI を構築したり UX をアプリや Web サイトに提供したりする中で数十年にわたって学んできた教訓は、ボットの設計にも当てはまります。 

ご自身のボットに対する適切な設計アプローチがわからない場合は、一歩引いて、自分自身に問いかけてみましょう。アプリまたは Web サイトだったら、その問題をどのように解決しますか。 多くの場合、その答えはボットの設計にも適用できます。 

## <a name="next-steps"></a>次の手順

ボット設計の基本原則についてはおわかりいただけたと思います。次は、ユーザー エクスペリエンスと、このセクションの続きの部分となる一般的なパターンを設計する方法について詳しく説明します。