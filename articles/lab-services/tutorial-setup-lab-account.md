---
title: Azure Lab Services でラボ アカウントを設定する | Microsoft Docs
description: このチュートリアルでは、Azure Lab Services (旧称 DevTest Labs) でラボ アカウントを設定します。
services: devtest-lab, lab-services, virtual-machines
documentationcenter: na
author: spelluru
manager: ''
editor: ''
ms.service: lab-services
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: tutorial
ms.custom: mvc
ms.date: 04/26/2018
ms.author: spelluru
ms.openlocfilehash: 347b7d183839868f3b52adbdfd00b38cee3f3fbc
ms.sourcegitcommit: d98d99567d0383bb8d7cbe2d767ec15ebf2daeb2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="tutorial-set-up-a-lab-account-with-azure-lab-services-formerly-azure-devtest-labs"></a>チュートリアル: Azure Lab Services (旧称 Azure DevTest Labs) でラボ アカウントを設定する
このチュートリアルでは、ラボ管理者として、Azure Lab Services でラボ アカウントを作成します。 その後、このラボ アカウントでクラス用のラボを作成するアクセス許可を教師に与えます。 教師は、[Azure Lab Services Web サイト](https://labs.azure.com)を使って、クラス用のラボを設定できます。   

このチュートリアルでは、次のアクションを実行します。

> [!div class="checklist"]
> * ラボ アカウントを作成する
> * ユーザーをラボの作成者ロールに追加する

Azure サブスクリプションをお持ちでない場合は、開始する前に [無料アカウント](https://azure.microsoft.com/free/) を作成してください。

## <a name="create-a-lab-account"></a>ラボ アカウントを作成する
次の手順では、Azure portal を使って Azure Lab Services でラボ アカウントを作成する方法を示します。 

1. [Azure Portal](https://portal.azure.com) にサインインします。
2. 左側のメイン メニューで、**[リソースの作成]** を選択します。
3. Azure Marketplace で **Lab Services** を検索し、ボックスの一覧から **[Lab Services]** を選択します。 
4. フィルター適用後のサービスの一覧で、**[Lab Services (プレビュー)]** を選択します。 
1. **[Create a lab account]** ウィンドウで、**[作成]** を選びます。
2. **[Lab account]\(ラボ アカウント\)** ウィンドウで、次のようにします。 
    1. **[Lab account name]\(ラボ アカウント名\)** に、名前を入力します。 
    2. ラボ アカウントを作成する **[Azure サブスクリプション]** を選択します。
    3. **[リソース グループ]** で、**[新規作成]** を選択し、リソース グループの名前を入力します。
    4. **[場所]** で、ラボ アカウントが作成される場所/リージョンを選択します。 
    5. **[作成]** を選択します。 

        ![ラボ アカウントの作成ウィンドウ](./media/tutorial-setup-lab-account/lab-account-settings.png)
5. ラボ アカウント ページが表示されない場合は、**[通知]** ボタンを選択し、通知内の **[リソースに移動]** ボタンをクリックします。 

    ![ラボ アカウントの作成ウィンドウ](./media/tutorial-setup-lab-account/notification-go-to-resource.png)    
6. 次の **[Lab account]\(ラボ アカウント\)** ページが表示されます。

    ![[Lab account]\(ラボ アカウント\) ページ](./media/tutorial-setup-lab-account/lab-account-page.png)

## <a name="add-a-user-to-the-lab-creator-role"></a>ユーザーをラボの作成者ロールに追加する
クラスのラボを作成するアクセス許可を教師に与えるには、教師をラボの作成者ロールに追加します。

1. **[ラボ アカウント]** ページで、**[アクセス制御 (IAM)]** を選択し、ツールバーの **[+ 追加]** をクリックします。 

    ![[Lab account]\(ラボ アカウント\) ページ](./media/tutorial-setup-lab-account/access-control.png)
2. **[アクセス許可の追加]** ページで、**[ロール]** から **[ラボの作成者]** を選び、ラボの作成者ロールに追加するユーザーを選んだ後、**[保存]** をクリックします。 

    ![ユーザーをラボの作成者ロールに追加する](./media/tutorial-setup-lab-account/add-user-to-lab-creator-role.png)


## <a name="next-steps"></a>次の手順
このチュートリアルでは、ラボ アカウントを作成しました。 専門職としてクラスルーム ラボを作成する方法を学習するには、次のチュートリアルに進んでください。

> [!div class="nextstepaction"]
> [クラスルーム ラボを設定する](tutorial-setup-classroom-lab.md)

