---
title: "Advisor の高可用性に関する推奨事項 | Microsoft Docs"
description: "Azure Advisor を使用して、Azure のデプロイの高可用性を向上させます。"
services: advisor
documentationcenter: NA
author: KumudD
manager: carmonm
editor: 
ms.assetid: 
ms.service: advisor
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: NA
ms.date: 11/16/2016
ms.author: kumud
ms.openlocfilehash: e1cd7948e1969cd4ddb926e428c09b559190a805
ms.sourcegitcommit: ce934aca02072bdd2ec8d01dcbdca39134436359
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="advisor-high-availability-recommendations"></a>Advisor の高可用性に関する推奨事項

Azure Advisor を使用して、ビジネスに不可欠なアプリケーションの継続稼働を保証し、さらに向上させることができます。 Advisor による高可用性に関する推奨事項は、Advisor ダッシュボードの**[高可用性]** タブで取得できます。

## <a name="ensure-virtual-machine-fault-tolerance"></a>仮想マシンのフォールト トレランスを確保する

アプリケーションに冗長性をもたらすには、可用性セット内に 2 つ以上の仮想マシンをグループ化することをお勧めします。 Advisor は、可用性セットの一部ではない仮想マシンを識別し、それらを可用性セットに移動することを推奨します。 このような構成により、計画済みのメンテナンス イベント中でも計画外のメンテナンス イベント中でも、少なくとも 1 台の仮想マシンが利用可能となり、Azure 仮想マシンの SLA が満たされます。 仮想マシンの可用性セットを作成するか、既存の可用性セットに仮想マシンを追加するかを選択できます。

> [!NOTE]
> 可用性セットを作成する場合は、少なくとも 1 台以上の仮想マシンを可用性セットに追加する必要があります。 2 台以上の仮想マシンを 1 つの可用性セットにグループ化して、障害の発生時に少なくとも 1 台のマシンを使用できるようにしておくことをお勧めします。

## <a name="ensure-availability-set-fault-tolerance"></a>可用性セットのフォールト トレランスを確保する 

アプリケーションに冗長性をもたらすには、可用性セット内に 2 つ以上の仮想マシンをグループ化することをお勧めします。 Advisor は、1 台の仮想マシンのみを含む可用性セットを識別し、そのセットにさらに仮想マシンを追加することを推奨します。 このような構成により、計画済みのメンテナンス イベント中でも計画外のメンテナンス イベント中でも、少なくとも 1 台の仮想マシンが利用可能となり、Azure 仮想マシンの SLA が満たされます。 仮想マシンを作成するか、既存の仮想マシンを可用性セットに追加するかを選択できます。  

## <a name="ensure-application-gateway-fault-tolerance"></a>アプリケーション ゲートウェイのフォールト トレランスを確保する
アプリケーション ゲートウェイを備えるミッション クリティカルなアプリケーションのビジネス継続性を確保するために、Advisor は、フォールト トレランス用に構成されていないアプリケーション ゲートウェイ インスタンスを識別し、実施できる修復アクションを提案します。 Advisor は、中規模または大規模な単一インスタンス アプリケーション ゲートウェイを識別し、少なくとも 1 つ以上のインスタンスを追加することを推奨します。 また、1 つまたは複数の小規模アプリケーション ゲートウェイを識別し、中規模または大規模な SKU に移行することを推奨します。 これらの修復アクションでは、アプリケーション ゲートウェイ インスタンスがこれらのリソースの現在の SLA 要件を満たすように構成されていることを確認します。

## <a name="improve-the-performance-and-reliability-of-virtual-machine-disks"></a>仮想マシンのディスクのパフォーマンスと信頼性の向上

Advisor は、Standard ディスクを使用している仮想マシンを識別し、Premium ディスクにアップグレードすることを推奨します。
 
Azure Premium Storage は、高負荷の I/O ワークロードを実行する仮想マシン向けに高パフォーマンスで待ち時間の少ないディスク サポートを提供します。 Premium Storage アカウントを使用する仮想マシンのディスクでは、ソリッド ステート ドライブ (SSD) にデータを格納します。 アプリケーションで最適なパフォーマンスを実現するには、高い IOPS を必要とする仮想マシン ディスクは Premium Storage に移行することをお勧めします。 

ディスクが高い IOPS を必要としない場合は、Standard Storage で管理することでコストを制限できます。 Standard Storage は、仮想マシンのディスク データを、SSD ではなくハード ディスク ドライブ (HDD) に格納します。 仮想マシンのディスクを Premium ディスクに移行することを選択できます。 Premium ディスクは、ほとんどの仮想マシンの SKU でサポートされます。 ただし、場合によっては、Premium ディスクを使用するには、仮想マシンの SKU もアップグレードする必要があります。

## <a name="protect-your-virtual-machine-data-from-accidental-deletion"></a>誤って削除されないように、仮想マシンのデータを保護する
仮想マシンのバックアップを設定することにより、ビジネス クリティカルなデータの可用性が確保され、偶発的な削除または破損からデータを保護します。  Advisor は、バックアップが有効になっていない仮想マシンを識別子、バックアップを有効にすることを推奨します。 

## <a name="how-to-access-high-availability-recommendations-in-advisor"></a>Advisor の高可用性に関する推奨事項にアクセスする方法

1. [Azure Portal](https://portal.azure.com) にサインインし、[Advisor](https://aka.ms/azureadvisordashboard) を開きます。

2.  Advisor ダッシュボードの **[高可用性]** タブをクリックします。

## <a name="next-steps"></a>次のステップ

Advisor の推奨事項について詳しくは、以下を参照してください。
* [Azure Advisor の概要](advisor-overview.md)
* [Advisor の使用を開始する](advisor-get-started.md)
* [Advisor のコストに関する推奨事項](advisor-performance-recommendations.md)
* [Advisor のパフォーマンスに関する推奨事項](advisor-performance-recommendations.md)
* [Advisor のセキュリティに関する推奨事項](advisor-security-recommendations.md)

