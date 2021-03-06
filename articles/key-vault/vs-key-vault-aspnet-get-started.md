---
title: Visual Studio での Key Vault 接続済みサービスの概要 (ASP.NET プロジェクト) | Microsoft Docs
description: このチュートリアルを使用すると、ASP.NET または ASP.NET Core Web アプリケーションに Key Vault のサポートを追加する方法を学習できます。
services: key-vault
author: ghogen
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.workload: azure
ms.topic: conceptual
ms.date: 04/15/2018
ms.author: ghogen
ms.openlocfilehash: cd305801f10c899682aa6d751e48f30b6e8303fa
ms.sourcegitcommit: e221d1a2e0fb245610a6dd886e7e74c362f06467
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="get-started-with-key-vault-connected-service-in-visual-studio-aspnet-projects"></a>Visual Studio での Key Vault 接続済みサービスの概要 (ASP.NET プロジェクト)

> [!div class="op_single_selector"]
> - [作業の開始](vs-key-vault-aspnet-get-started.md)
> - [変更内容](vs-key-vault-aspnet-what-happened.md)

この記事では、Visual Studio の **[Add Connected Services]\(接続済みサービスの追加\)** コマンドを使用して Key Vault を ASP.NET MVC プロジェクトに追加した後のガイダンスを提供します。 プロジェクトにまだサービスを追加していない場合は、「[Add Key Vault to your web application by using Visual Studio Connected Services (Visual Studio 接続済みサービスを使用して Web アプリケーションに Key Vault を追加する)](vs-key-vault-add-connected-service.md)」の手順に従って、いつでも追加することができます。

接続済みサービスを追加したときにプロジェクトに加えられる変更については、[ASP.NET プロジェクトの変更点](vs-key-vault-aspnet-core-what-happened.md)に関するページを参照してください。

## <a name="after-you-connect"></a>接続後

1. Azure 内の Key Vault にシークレットを追加します。 ポータルの適切な場所に移動するには、この **[Manage secrets stored in this Key Vault]\(Key Vault に格納されるシークレットの管理\)** のリンクをクリックします。 ページまたはプロジェクトが閉じている場合は、[Azure Portal](https://portal.azure.com) で **[すべてのサービス]** を選択し、**[セキュリティ]** の下の **[Key Vault]** を選択します。次に、先ほど作成した Key Vault を選択することで、同じ場所に移動できます。

   ![ポータルへの移動](media/vs-key-vault-add-connected-service/manage-secrets-link.jpg)

1. 作成したキー コンテナーの [Key Vault] セクションで、**[シークレット]**、**[Generate/Import]\(生成/インポート\)** の順に選択します。

   ![シークレットを生成/インポートする](media/vs-key-vault-add-connected-service/generate-secrets.jpg)

1. **MySecret** などのシークレットを入力し、テストとして任意の文字列値を指定した後、**[作成]** ボタンを選択します。

   ![シークレットの作成](media/vs-key-vault-add-connected-service/create-a-secret.jpg)
 
1. (省略可能) 別のシークレットを入力しますが、今回は **Secrets--MySecret** という名前を付けることでカテゴリに配置します。 この構文は、**MySecret** というシークレットを含む **Secrets** というカテゴリを指定します。

1. 次のように web.config を変更します。 キーは、AzureKeyVault ConfigurationBuilder によって Key Vault 内のシークレットの値に置き換えられるプレースホルダーです。

   ```xml
     <appSettings configBuilders="AzureKeyVault">
       <add key="webpages:Version" value="3.0.0.0" />
       <add key="webpages:Enabled" value="false" />
       <add key="ClientValidationEnabled" value="true" />
       <add key="UnobtrusiveJavaScriptEnabled" value="true" />
       <add key="MySecret" value="dummy1"/>
       <add key="Secrets--MySecret" value="dummy2"/>
     </appSettings>
   ```

1. HomeController の About コントローラー メソッドに、シークレットを取得して ViewBag に格納する次の行を追加します。
 
   ```csharp
            var secret = ConfigurationManager.AppSettings["MySecret"];
            var secret2 = ConfigurationManager.AppSettings["Secrets--MySecret"];
            ViewBag.Secret = $"Secret: {secret}";
            ViewBag.Secret2 = $"Secret2: {secret2}";
   ```

1. About.cshtml ビューに、シークレットの値を表示する次の行を追加します (テスト目的専用)。

   ```csharp
      <h3>@ViewBag.Secret</h3>
      <h3>@ViewBag.Secret2</h3>
   ```

これで、安全に格納されているシークレットに Web アプリが Key Vault を使用してアクセスできるようになりました。

## <a name="clean-up-resources"></a>リソースのクリーンアップ

不要になったら、リソース グループを削除します。 これにより、Key Vault と関連リソースが削除されます。 ポータルを使用してリソース グループを削除するには:

1. ポータル上部にある検索ボックスにリソース グループの名前を入力します。 このクイック スタートで使用されているリソース グループが検索結果に表示されたら、それを選択します。
2. **[リソース グループの削除]** を選択します。
3. **[リソース グループ名を入力してください:]** ボックスにリソース グループの名前を入力し、**[削除]** を選択します。

# <a name="next-steps"></a>次の手順

Key Vault での開発の詳細については、「[Key Vault 開発者ガイド](key-vault-developers-guide.md)」を参照してください