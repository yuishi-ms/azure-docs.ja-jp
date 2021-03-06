---
title: Azure Stack Development Kit (ASDK) の再デプロイ | Microsoft Docs
description: このチュートリアルでは、ASDK を再インストールする方法について説明します。
services: azure-stack
documentationcenter: ''
author: jeffgilb
manager: femila
editor: ''
ms.assetid: ''
ms.service: azure-stack
ms.workload: na
pms.tgt_pltfrm: na
ms.devlang: na
ms.topic: tutorial
ms.custom: mvc
ms.date: 03/16/2018
ms.author: jeffgilb
ms.reviewer: misainat
ms.openlocfilehash: fcf1abfe574dd3067f00df7c5ff2632b9cc2ec4f
ms.sourcegitcommit: e2adef58c03b0a780173df2d988907b5cb809c82
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="tutorial-redeploy-the-asdk"></a>チュートリアル: ASDK の再デプロイ
このチュートリアルでは、非運用環境で Azure Stack Development Kit (ASDK) を再デプロイする方法について説明します。 ASDK のアップグレードはサポートされていないため、新しいバージョンに移行するには、ASDK を完全に再デプロイする必要があります。 また、ゼロからやり直したいときにも、いつでも ASDK を再デプロイすることができます。

> [!IMPORTANT]
> 新しいバージョンへの ASDK のアップグレードはサポートされていません。 Azure Stack のより新しいバージョンを評価するたびに、開発キットのホスト コンピューターに ASDK を再デプロイする必要があります。

このチュートリアルで学習する内容は次のとおりです。

> [!div class="checklist"]
> * Azure の登録の削除 
> * ASDK の再デプロイ

## <a name="remove-azure-registration"></a>Azure の登録の削除 
以前に ASDK インストールを Azure に登録したことがある場合は、ASDK を再デプロイする前に、登録リソースを削除する必要があります。 ASDK を再デプロイするときに、マーケットプレースのシンジケーションを有効にするために、ASDK を再登録します。 以前に ASDK を Azure サブスクリプションに登録していない場合は、このセクションをスキップできます。

登録リソースを削除するには、**Remove-AzsRegistration** コマンドレットを使用して Azure Stack の登録を解除します。 次に、**Remove-AzureRMRsourceGroup** コマンドレットを使用して、Azure サブスクリプションから Azure Stack リソース グループを削除します。

1. 特権エンドポイントにアクセスできるコンピューターで、管理者として PowerShell コンソールを開きます。 ASDK の場合は、開発キットのホスト コンピューターです。

2. 次の PowerShell コマンドを実行して、ASDK のインストールを登録解除し、Azure サブスクリプションから **azurestack** リソース グループを削除します。

  ```Powershell    
  #Import the registration module that was downloaded with the GitHub tools
  Import-Module C:\AzureStack-Tools-master\Registration\RegisterWithAzure.psm1

  # Provide Azure subscription admin credentials
  Add-AzureRmAccount

  # Provide ASDK admin credentials
  $CloudAdminCred = Get-Credential -UserName AZURESTACK\CloudAdmin -Message "Enter the cloud domain credentials to access the privileged endpoint"

  # Unregister Azure Stack
  Remove-AzsRegistration `
      -CloudAdminCredential $YourCloudAdminCredential `
      -PrivilegedEndpoint AzS-ERCS01

  # Remove the Azure Stack resource group
  Remove-AzureRmResourceGroup -Name azurestack -Force
  ```

3. スクリプトの実行時に、Azure サブスクリプションとローカル ASDK インストールの両方にサインインするように求めるメッセージが表示されます。
4. コマンドが完了すると、次の例のようなメッセージが表示されます。

    ` De-Activating Azure Stack (this may take up to 10 minutes to complete).` ` Your environment is now unable to syndicate items and is no longer reporting usage data.` ` Remove registration resource from Azure...` ` "Deleting the resource..." on target "/subscriptions/<subscription information>"` ` ********** End Log: Remove-AzsRegistration ********* `



これで、Azure Stack の登録が Azure サブスクリプションから正常に解除されました。 さらに、ASDK を Azure に登録したときに作成された azurestack リソース グループも削除する必要があります。

## <a name="redeploy-the-asdk"></a>ASDK の再デプロイ
Azure Stack を再デプロイするには、次に説明するように、最初から開始する必要があります。 ASDK のインストールに Azure Stack インストーラー (asdk-installer.ps1) スクリプトを使用したかどうかによって、手順が異なります。

### <a name="redeploy-the-asdk-using-the-installer-script"></a>インストーラー スクリプトを使用して ASDK を再デプロイする
1. ASDK コンピューターで、管理者特権で PowerShell コンソールを開き、非システム ドライブにある **AzureStack_Installer** ディレクトリの asdk-installer.ps1 スクリプトに移動します。 スクリプトを実行し、**[再起動]** をクリックします。

   ![asdk-installer.ps1 スクリプトを実行する](media/asdk-redeploy/1.png)

2. ベース オペレーティング システム (**Azure Stack** でなく) を選択し、**[次へ]** をクリックします。

   ![ホスト オペレーティング システムで再起動する](media/asdk-redeploy/2.png)

3. 開発キットのホストがベース オペレーティング システムで再起動したら、ローカル管理者としてログインします。 以前のデプロイの一部として使用されていた **C:\CloudBuilder.vhdx** ファイルを探して削除します。 

4. 最初に [ASDK をデプロイ](asdk-deploy.md)したときと同じ手順を繰り返します。

### <a name="redeploy-the-asdk-without-using-the-installer"></a>インストーラーを使用せずに ASDK を再デプロイする
ASDK をインストールするために asdk-installer.ps1 スクリプトを使用しなかった場合は、ASDK を再デプロイする前に、開発キットのホスト コンピューターを手動で再構成する必要があります。

1. ASDK コンピューターで **msconfig.exe** を実行して、システム構成ユーティリティを起動します。 **[ブート]** タブでホスト コンピューターのオペレーティング システム (Azure Stack ではない) を選択し、**[既定値に設定する]** をクリックし、**[OK]** をクリックします。 確認を求めるメッセージが表示されたら、**[再起動]** をクリックします。

      ![ブート構成を設定する](media/asdk-redeploy/4.png)

2. 開発キットのホストがベース オペレーティング システムで再起動したら、開発キット ホスト コンピューターのローカル管理者としてログインします。 以前のデプロイの一部として使用されていた **C:\CloudBuilder.vhdx** ファイルを探して削除します。 

3. 最初に [PowerShell を使用して ASDK をデプロイ](asdk-deploy-powershell.md)したときと同じ手順を繰り返します。


## <a name="next-steps"></a>次の手順
このチュートリアルで学習した内容は次のとおりです。

> [!div class="checklist"]
> * Azure の登録の削除 
> * ASDK の再デプロイ

次のチュートリアルに進み、Azure Stack マーケットプレース項目を追加する方法を学習してください。

> [!div class="nextstepaction"]
> [Azure Stack マーケットプレース項目を追加する](asdk-marketplace-item.md)




