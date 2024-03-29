---
ms.openlocfilehash: 0b991c438c0006d1fb4bafa90982f73f4a18be77
ms.sourcegitcommit: 980612a922b8290b2faadaca193496c4117e415a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2019
ms.locfileid: "64563449"
---
Bot Builder Framework を使用すると、ボットは、ユーザー、会話、または特定の会話のコンテキスト内で特定ユーザーに関連付けられている状態データを、格納および取得できます。 状態データは、以前の会話がどこで中断されたかを判断したり、戻ってきたユーザーにそのユーザーの名前を使ってあいさつしたりするなど、さまざまな目的で使用できます。 ユーザーの設定を保存すると、次回チャットするときにその情報を使用して会話をカスタマイズできます。 たとえば、ユーザーが関心を持っているトピックに関するニュース記事についてユーザーに通知したり、予約が利用可能になった場合にユーザーに通知したりできます。 

テストやプロトタイプ作成が目的の場合は、Bot Builder Framework のインメモリ データ ストレージを使用できます。 運用ボットの場合は、独自のストレージ アダプターを実装するか、Azure 拡張機能のいずれかを使用できます。 Azure 拡張機能を使用すると、Table Storage、CosmosDB、または SQL のいずれかにボットの状態データを格納できます。 この記事では、インメモリ ストレージ アダプターを使用してボットの状態データを格納する方法を説明します。 

> [!IMPORTANT]
> Bot Framework State Service API を運用環境で使用することは推奨されていません。将来のリリースで非推奨となる可能性があります。 テストが目的の場合はインメモリ ストレージ アダプターを使用するようにボット コードを更新し、運用ボットの場合は **Azure 拡張機能**のいずれかを使用することをお勧めします。
