---
title: "Azure AD アプリにグループを割り当てる | Microsoft Docs"
description: "Azure アプリケーションへのグループの割り当てを実装する方法です。"
services: active-directory
documentationcenter: 
author: kgremban
manager: mtillman
editor: 
ms.assetid: 29b5ba89-a1c7-4f1f-a294-248a40106617
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 05/07/2017
ms.author: kgremban
ms.custom: H1Hack27Feb2017
robots: noindex
ms.openlocfilehash: 471099c58a7fc1dfd520e693873a76f64c0fbf0a
ms.sourcegitcommit: e266df9f97d04acfc4a843770fadfd8edf4fa2b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2017
---
# <a name="assign-azure-active-directory-groups-to-an-application"></a>アプリケーションに Azure Active Directory グループを割り当てる
ユーザーとグループをアプリケーションに割り当てる前に、ユーザー割り当てを要求する必要があります。 ユーザー割り当てを要求する方法については、 [ユーザー割り当ての要求](active-directory-applications-guiding-developers-requiring-user-assignment.md) に関する記事をご覧ください。

この記事では、このアプリケーションに使用する Active Directory に既にグループが作成されていることを前提としています。

## <a name="assigning-groups-to-an-application"></a>アプリケーションへのグループの割り当て
1. 管理者アカウントを使用して、Azure Portal にログインします。
2. メイン メニューの **[すべてのアイテム]** をクリックします。
3. アプリケーションに使用するディレクトリを選択します。
4. **[アプリケーション]** タブをクリックします。
5. このディレクトリに関連付けられているアプリケーションの一覧から、アプリケーションを選択します。
6. **[ユーザーとグループ]** タブをクリックします。
7. **[グループ]** ボックスの一覧を使用して、Active Directory 内のグループの一覧を絞り込みます。
8. グループを選択します。
9. **[割り当て]**をクリックします。
10. 確認を求めるメッセージが表示されたら、 **[はい]** をクリックします。

## <a name="next-steps"></a>次のステップ
[!INCLUDE [active-directory-applications-guiding-developers-for-lob-applications-toc.md](../../includes/active-directory-applications-guiding-developers-for-lob-applications-toc.md)]
