---
title: 'チュートリアル: Azure Active Directory と Dome9 Arc の統合 | Microsoft Docs'
description: Azure Active Directory と Dome9 Arc の間でシングル サインオンを構成する方法について説明します。
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: 4c12875f-de71-40cb-b9ac-216a805334e5
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 01/18/2018
ms.author: jeedes
ms.openlocfilehash: de164f6a439fd68b4746dc96c43ff5cb0740ffe8
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2018
---
# <a name="tutorial-azure-active-directory-integration-with-dome9-arc"></a>チュートリアル: Azure Active Directory と Dome9 Arc の統合

このチュートリアルでは、Dome9 Arc と Azure Active Directory (Azure AD) を統合する方法について説明します。

Dome9 Arc と Azure AD の統合には、次の利点があります。

- Dome9 Arc にアクセスできる Azure AD ユーザーを制御できます。
- ユーザーが自分の Azure AD アカウントで自動的に Dome9 Arc にサインオン (シングル サインオン) できるようにします。
- 1 つの中央サイト (Azure Portal) でアカウントを管理できます。

SaaS アプリと Azure AD の統合の詳細については、「[Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](manage-apps/what-is-single-sign-on.md)」をご覧ください。

## <a name="prerequisites"></a>前提条件

Dome9 Arc と Azure AD の統合を構成するには、次のものが必要です。

- Azure AD サブスクリプション
- Dome9 Arc でのシングル サインオンが有効なサブスクリプション

> [!NOTE]
> このチュートリアルの手順をテストする場合、運用環境を使用しないことをお勧めします。

このチュートリアルの手順をテストするには、次の推奨事項に従ってください。

- 必要な場合を除き、運用環境は使用しないでください。
- Azure AD の評価環境がない場合は、[1 か月の評価版を入手できます](https://azure.microsoft.com/pricing/free-trial/)。

## <a name="scenario-description"></a>シナリオの説明
このチュートリアルでは、テスト環境で Azure AD のシングル サインオンをテストします。 このチュートリアルで説明するシナリオは、主に次の 2 つの要素で構成されています。

1. ギャラリーからの Dome9 Arc の追加
2. Azure AD シングル サインオンの構成とテスト

## <a name="adding-dome9-arc-from-the-gallery"></a>ギャラリーからの Dome9 Arc の追加
Azure AD への Dome9 Arc の統合を構成するには、ギャラリーから管理対象 SaaS アプリの一覧に Dome9 Arc を追加する必要があります。

**ギャラリーから Dome9 Arc を追加するには、次の手順を実行します。**

1. **[Azure Portal](https://portal.azure.com)** の左側のナビゲーション ウィンドウで、**[Azure Active Directory]** アイコンをクリックします。 

    ![Azure Active Directory のボタン][1]

2. **[エンタープライズ アプリケーション]** に移動します。 次に、**[すべてのアプリケーション]** に移動します。

    ![[エンタープライズ アプリケーション] ブレード][2]
    
3. 新しいアプリケーションを追加するには、ダイアログの上部にある **[新しいアプリケーション]** をクリックします。

    ![[新しいアプリケーション] ボタン][3]

4. 検索ボックスに「**Dome9 Arc**」と入力し、結果パネルから **[Dome9 Arc]** を選択してから、**[追加]** ボタンをクリックしてアプリケーションを追加します。

    ![結果一覧の Dome9 Arc](./media/active-directory-saas-dome9arc-tutorial/tutorial_dome9arc_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Azure AD シングル サインオンの構成とテスト

このセクションでは、"Britta Simon" という名前のテスト ユーザーに基づいて、Dome9 Arc で Azure AD シングル サインオンを構成してテストします。

シングル サインオンを機能させるには、Azure AD ユーザーに対応する Dome9 Arc ユーザーが Azure AD で認識されている必要があります。 言い換えると、Azure AD ユーザーと Dome9 Arc の関連ユーザーの間で、リンク関係が確立されている必要があります。

Dome9 Arc で、Azure AD の **[ユーザー名]** の値を **[Username]** の値として割り当ててリンク関係を確立します。

Dome9 Arc で Azure AD のシングル サインオンを構成してテストするには、次の構成要素を完了する必要があります。

1. **[Azure AD シングル サインオンの構成](#configure-azure-ad-single-sign-on)** - ユーザーがこの機能を使用できるようにします。
2. **[Azure AD のテスト ユーザーの作成](#create-an-azure-ad-test-user)** - Britta Simon で Azure AD のシングル サインオンをテストします。
3. **[Dome9 Arc テスト ユーザーの作成](#create-a-dome9-arc-test-user)** - Dome9 Arc で Britta Simon に対応するユーザーを作成し、Azure AD の Britta Simon にリンクさせます。
4. **[Azure AD テスト ユーザーの割り当て](#assign-the-azure-ad-test-user)** - Britta Simon が Azure AD シングル サインオンを使用できるようにします。
5. **[シングル サインオンのテスト](#test-single-sign-on)** - 構成が機能するかどうかを確認します。

### <a name="configure-azure-ad-single-sign-on"></a>Azure AD シングル サインオンの構成

このセクションでは、Azure Portal で Azure AD のシングル サインオンを有効にし、Dome9 Arc アプリケーションでシングル サインオンを構成します。

**Dome9 Arc で Azure AD シングル サインオンを構成するには、次の手順を実行します。**

1. Azure Portal の **Dome9 Arc** アプリケーション統合ページで、**[シングル サインオン]** をクリックします。

    ![シングル サインオン構成のリンク][4]

2. **[シングル サインオン]** ダイアログで、**[モード]** として **[SAML ベースのサインオン]** を選択し、シングル サインオンを有効にします。
 
    ![[シングル サインオン] ダイアログ ボックス](./media/active-directory-saas-dome9arc-tutorial/tutorial_dome9arc_samlbase.png)

3. **[Dome9 Arc Domain and URLs] (Dome9 Arc のドメインと URL)** セクションで、**IDP** 開始モードでアプリケーションを構成する場合は、次の手順を実行します。

    ![[Dome9 Arc Domain and URLs] (Dome9 Arc のドメインと URL) のシングル サインオン情報](./media/active-directory-saas-dome9arc-tutorial/tutorial_dome9arc_url.png)

    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[識別子]** ボックスに次の URL を入力します。`https://secure.dome9.com/`

    b. **[応答 URL]** ボックスに、`https://secure.dome9.com/sso/saml/yourcompanyname` のパターンを使用して URL を入力します。

    > [!NOTE]
    > Dome9 管理ポータルで会社名の値を選択します。これについては、このチュートリアルの後の方で説明します。

4. アプリケーションを **SP** 開始モードで構成する場合は、**[詳細な URL 設定の表示]** チェックボックスをオンにして次の手順を実行します。

    ![[Dome9 Arc Domain and URLs] (Dome9 Arc のドメインと URL) のシングル サインオン情報](./media/active-directory-saas-dome9arc-tutorial/tutorial_dome9arc_url1.png)

    **[サインオン URL]** ボックスに、`https://secure.dome9.com/sso/saml/<yourcompanyname>` のパターンを使用して URL を入力します。
     
    > [!NOTE] 
    > これらは実際の値ではありません。 実際の応答 URLとサインオン URL でこれらの値を更新します。 これらの値を取得するには、[Dome9 Arc クライアント サポート チーム](https://dome9.com/about/contact-us/)に問い合わせてください。 

5. Dome9 Arc Software アプリケーションは、特定の形式で構成された SAML アサーションを受け入れます。 このアプリケーションには、次の要求を構成します。 この属性の値は、アプリケーション統合ページの **[User Attributer]** セクションで管理できます。 次のスクリーンショットはその例です。

    ![シングル サインオンの構成の属性](./media/active-directory-saas-dome9arc-tutorial/tutorial_dome9arc_attribute.png)

6. **[シングル サインオン]** ダイアログの **[ユーザー属性]** セクションで、上の図に示すように SAML トークン属性を構成し、次の手順を実行します。
    
    | 属性名  | 属性値 | 
    | --------------- | --------------- | 
    | memberof | user.assignedroles | 
    
    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[属性の追加]** をクリックして **[属性の追加]** ダイアログを開きます。

    ![シングル サインオンの構成の属性の追加](./media/active-directory-saas-dome9arc-tutorial/tutorial_dome9_04.png)

    ![シングル サインオンの構成の属性の編集](./media/active-directory-saas-dome9arc-tutorial/tutorial_attribute_05.png)

    b. **[名前]** ボックスに、その行に対して表示される属性名を入力します。

    c. **[値]** 一覧から、その行に対して表示される値を入力します。
    
    d. **[OK]** をクリックします。

7. **[SAML 署名証明書]** セクションで、**[証明書 (Base64)]** をクリックし、コンピューターに証明書ファイルを保存します。

    ![証明書のダウンロードのリンク](./media/active-directory-saas-dome9arc-tutorial/tutorial_dome9arc_certificate.png) 

8. **[保存]** ボタンをクリックします。

    ![[シングル サインオンの構成] の [保存] ボタン](./media/active-directory-saas-dome9arc-tutorial/tutorial_general_400.png)
    
9. **[Dome9 Arc Configuration] (Dome9 Arc 構成)** セクションで、**[Configure Dome9 Arc] (Dome9 Arc の構成)** をクリックして **[サインオンの構成]** ウィンドウを開きます。 **[クイック リファレンス]** セクションから、**SAML エンティティ ID と SAML シングル サインオン サービス URL** をコピーします。

    ![[Dome9 Arc Configuration] (Dome9 Arc 構成)](./media/active-directory-saas-dome9arc-tutorial/tutorial_dome9arc_configure.png) 

10. 別の Web ブラウザー ウィンドウで、Dome9 Arc 企業サイトに管理者としてログインします。

11. 右上隅にある **[プロファイル設定]** をクリックしてから、**[アカウント設定]** をクリックします。 

    ![[Dome9 Arc Configuration] (Dome9 Arc 構成)](./media/active-directory-saas-dome9arc-tutorial/configure1.png)

12. **[SSO]** に移動し、**[有効にする]** をクリックします。

    ![[Dome9 Arc Configuration] (Dome9 Arc 構成)](./media/active-directory-saas-dome9arc-tutorial/configure2.png)

13. [SSO 構成] セクションで、次の手順を実行します。

    ![[Dome9 Arc Configuration] (Dome9 Arc 構成)](./media/active-directory-saas-dome9arc-tutorial/configure3.png)

    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[アカウント ID]** テキスト ボックスに会社名を入力します。 この値は、Azure Portal の URL のセクションで説明されている応答 URL で使用されます。

    b. **[発行者]** テキスト ボックスに、Azure Portal からコピーした **SAML エンティティ ID** の値を貼り付けます。

    c. **[Idp endpoint url] (IDP エンドポイント URL)** テキスト ボックスに、Azure Portal からコピーした **SAML シングル サインオン サービス URL** の値を貼り付けます。

    d. ダウンロードされた Base64 でエンコードされた証明書をメモ帳で開き、その内容をクリップボードにコピーしてから、それを **[X.509 証明書]** テキスト ボックスに貼り付けます。

    e. **[Save]** をクリックします。

> [!TIP]
> アプリのセットアップ中、[Azure Portal](https://portal.azure.com) 内で上記の手順の簡易版を確認できるようになりました。  **[Active Directory] の [エンタープライズ アプリケーション]** セクションからこのアプリを追加した後、**[シングル サインオン]** タブをクリックし、一番下の **[構成]** セクションから組み込みドキュメントにアクセスするだけです。 組み込みドキュメント機能の詳細については、[Azure AD の組み込みドキュメント]( https://go.microsoft.com/fwlink/?linkid=845985)に関するページを参照してください。

### <a name="create-an-azure-ad-test-user"></a>Azure AD のテスト ユーザーの作成

このセクションの目的は、Azure Portal で Britta Simon というテスト ユーザーを作成することです。

   ![Azure AD のテスト ユーザーの作成][100]

**Azure AD でテスト ユーザーを作成するには、次の手順に従います。**

1. Azure Portal の左側のウィンドウで、**Azure Active Directory** のボタンをクリックします。

    ![Azure Active Directory のボタン](./media/active-directory-saas-dome9arc-tutorial/create_aaduser_01.png)

2. ユーザーの一覧を表示するには、**[ユーザーとグループ]** に移動し、**[すべてのユーザー]** をクリックします。

    ![[ユーザーとグループ] と [すべてのユーザー] リンク](./media/active-directory-saas-dome9arc-tutorial/create_aaduser_02.png)

3. **[ユーザー]** ダイアログ ボックスを開くには、**[すべてのユーザー]** ダイアログ ボックスの上部にある **[追加]** をクリックしてきます。

    ![[追加] ボタン](./media/active-directory-saas-dome9arc-tutorial/create_aaduser_03.png)

4. **[ユーザー]** ダイアログ ボックスで、次の手順に従います。

    ![[ユーザー] ダイアログ ボックス](./media/active-directory-saas-dome9arc-tutorial/create_aaduser_04.png)

    a. **[名前]** ボックスに「**BrittaSimon**」と入力します。

    b. **[ユーザー名]** ボックスに、ユーザーである Britta Simon の電子メール アドレスを入力します。

    c. **[パスワードを表示]** チェック ボックスをオンにし、**[パスワード]** ボックスに表示された値を書き留めます。

    d. **Create** をクリックしてください。
 
### <a name="create-a-dome9-arc-test-user"></a>Dome9 Arc テスト ユーザーを作成する

Azure AD ユーザーが Dome9 Arc にログインできるようにするには、そのユーザーをアプリケーションにプロビジョニングする必要があります。 Dome9 Arc はジャストインタイムのプロビジョニングをサポートしていますが、それが正しく機能するには、ユーザーが特定の**ロール**を選択し、同じものをそのユーザーに割り当てる必要があります。

   >[!Note] 
   >**ロール**の作成やその他の詳細については、[Dome9 Arc クライアント サポート チーム](https://dome9.com/about/contact-us/)に問い合わせてください。

**ユーザー アカウントを手動でプロビジョニングするには、次の手順を実行します。**

1. Dome9 Arc 企業サイトに管理者としてログインします。

2. **[Users & Roles] (ユーザーとロール)** をクリックしてから、**[ユーザー]** をクリックします。

    ![従業員の追加](./media/active-directory-saas-dome9arc-tutorial/user1.png)

3. **[ユーザーの追加]** をクリックします。

    ![従業員の追加](./media/active-directory-saas-dome9arc-tutorial/user2.png)

4. **[Create User]** セクションで、次の手順に従います。
    
    ![従業員の追加](./media/active-directory-saas-dome9arc-tutorial/user3.png)

    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[電子メール]** テキスト ボックスに、ユーザーの電子メール (Brittasimon@contoso.com など) を入力します。

    b. **[First Name]\(名\)** ボックスに、ユーザーの名を入力します (この例では Britta)。

    c. **[Last Name]\(姓\)** ボックスに、ユーザーの姓を入力します (この例では Simon)。

    d. **[SSO User] (SSO ユーザー)** を **[オン]** にします。

    e. **[作成]** をクリックします。

### <a name="assign-the-azure-ad-test-user"></a>Azure AD テスト ユーザーの割り当て

このセクションでは、Britta Simon に Dome9 Arc へのアクセスを許可することで、このユーザーが Azure シングル サインオンを使用できるようにします。

![ユーザー ロールを割り当てる][200] 

**Dome9 Arc に Britta Simon を割り当てるには、次の手順を実行します。**

1. Azure Portal でアプリケーション ビューを開き、ディレクトリ ビューに移動します。次に、**[エンタープライズ アプリケーション]** に移動し、**[すべてのアプリケーション]** をクリックします。

    ![ユーザーの割り当て][201] 

2. アプリケーションの一覧で、**[Dome9 Arc]** を選択します。

    ![アプリケーションの一覧の [Dome9 Arc] リンク](./media/active-directory-saas-dome9arc-tutorial/tutorial_dome9arc_app.png)  

3. 左側のメニューで **[ユーザーとグループ]** をクリックします。

    ![[ユーザーとグループ] リンク][202]

4. **[追加]** ボタンをクリックします。 次に、**[割り当ての追加]** ダイアログで **[ユーザーとグループ]** を選択します。

    ![[割り当ての追加] ウィンドウ][203]

5. **[ユーザーとグループ]** ダイアログで、ユーザーの一覧から **[Britta Simon]** を選択します。

6. **[ユーザーとグループ]** ダイアログで **[選択]** をクリックします。

7. **[割り当ての追加]** ダイアログで **[割り当て]** ボタンをクリックします。
    
### <a name="test-single-sign-on"></a>シングル サインオンのテスト

このセクションでは、アクセス パネルを使用して Azure AD のシングル サインオン構成をテストします。

アクセス パネルで [Dome9 Arc] タイルをクリックすると、Dome9 Arc アプリケーションに自動的にサインオンします。
アクセス パネルの詳細については、[アクセス パネルの概要](active-directory-saas-access-panel-introduction.md)に関する記事を参照してください。 

## <a name="additional-resources"></a>その他のリソース

* [SaaS アプリと Azure Active Directory を統合する方法に関するチュートリアルの一覧](active-directory-saas-tutorial-list.md)
* [Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/active-directory-saas-dome9arc-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-dome9arc-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-dome9arc-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-dome9arc-tutorial/tutorial_general_04.png

[100]: ./media/active-directory-saas-dome9arc-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-dome9arc-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-dome9arc-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-dome9arc-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-dome9arc-tutorial/tutorial_general_203.png

