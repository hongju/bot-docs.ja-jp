---
title: Bot Service の継続的配置を構成する | Microsoft Docs
description: Bot Service のソース管理からの継続的デプロイを設定する方法について説明します。
keywords: 継続的配置, 公開, デプロイ, Azure portal
author: ivorb
ms.author: v-ivorb
manager: kamrani
ms.topic: article
ms.service: bot-service
ms.date: 05/23/2019
monikerRange: azure-bot-service-4.0
ms.openlocfilehash: 8d324138db60c2b34f9bebd3ff53c30a12c3cefa
ms.sourcegitcommit: a295a90eac461f8b96770dd902ba44919acf33fc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67405955"
---
# <a name="set-up-continuous-deployment"></a>Azure App Service での GIT による継続的なデプロイ

[!INCLUDE [applies-to](./includes/applies-to.md)]

この記事では、お使いのボットの継続的デプロイを構成する方法を示します。 継続的デプロイを有効にすると、コード変更をソース リポジトリから Azure に自動的にデプロイできます。 このトピックでは、GitHub に対して継続的デプロイを設定する方法を説明します。 その他のソース管理システムでの継続的デプロイの設定については、このページの下部にある「その他のリソース」セクションを参照してください。

## <a name="prerequisites"></a>前提条件
- Azure サブスクリプションをお持ちでない場合は、開始する前に [無料アカウント](http://portal.azure.com) を作成してください。
- 継続的デプロイを有効にする前に、[お使いのボットを Azure にデプロイする](bot-builder-deploy-az-cli.md)**必要があります**。

## <a name="prepare-your-repository"></a>リポジトリを準備する
リポジトリのルートに、プロジェクトの適切なファイルがあることを確認してください。 これにより Azure App Service の Kudu ビルド サーバーから自動ビルドを取得できます。 

|ランタイム | ルート ディレクトリのファイル |
|:-------|:---------------------|
| ASP.NET Core | .sln または .csproj |
| Node.js | server.js、app.js、またはスタート スクリプトを含む package.json |


## <a name="continuous-deployment-using-github"></a>GitHub を使用した継続的デプロイ
GitHub を使用する継続的デプロイを有効にするには、Azure portal でご自身のボットの **App Service** ページに移動します。

**[デプロイ センター]**  >  **[GitHub]**  >  **[承認]** をクリックします。

![継続的デプロイ](~/media/azure-bot-build/azure-deployment.png)

表示されたブラウザー ウィンドウで、 **[Authorize AzureAppService]\(AzureAppService の承認\)** をクリックします。 

![Azure Github のアクセス許可](~/media/azure-bot-build/azure-deployment-github.png)

**AzureAppService** の承認後、Azure portal の**デプロイ センター**に戻ります。

1. **[続行]** をクリックします。 

1. **[App Service のビルド サービス]** を選択します。

1. **[続行]** をクリックします。

1. **[組織]** 、 **[リポジトリ]** 、および **[分岐]** を選択します。

1. **[続行]** をクリックし、 **[完了]** をクリックして設定を完了します。

この時点で、GitHub での継続的デプロイは設定されています。 ソース コード リポジトリにコミットするたびに、変更が Azure Bot Service に自動的にデプロイされます。

## <a name="disable-continuous-deployment"></a>継続的なデプロイの無効化

ボットが継続的デプロイ用に構成されている間は、オンライン コード エディターを使ってボットを変更することはきません。 オンライン コード エディターを使いたい場合は、継続的デプロイを一時的に無効にできます。

継続的デプロイを無効にするには、次の手順のようにします。
1. [Azure portal](https://portal.azure.com) 上で、ボットの **[All App service settings]\(すべての App Service の設定\)** ブレードに移動し、 **[デプロイ センター]** をクリックします。 
1. **[Disconnect]\(切断\)** をクリックして、継続的デプロイを無効化にします。 継続的デプロイを再度有効にするには、上記の該当するセクションの手順を繰り返します。

## <a name="additional-resources"></a>その他のリソース
- BitBucket および Azure DevOps Services からの継続的デプロイを有効にするには、「[Azure App Service への継続的デプロイ](https://docs.microsoft.com/azure/app-service/deploy-continuous-deployment)」を参照してください。


