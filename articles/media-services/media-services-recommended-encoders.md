---
title: "Azure Media Services で推奨されるエンコーダーについて知る | Microsoft Docs"
description: "メディア サービスで推奨されるエンコーダーについて知る"
services: media-services
keywords: "エンコード;エンコーダー;メディア"
author: dbgeorge
manager: jasonsue
ms.author: dwgeo
ms.date: 11/10/2017
ms.topic: article
ms.service: media-services
ms.openlocfilehash: d0c5536d2339470eac058250cc14e1f250b86d90
ms.sourcegitcommit: 9a61faf3463003375a53279e3adce241b5700879
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="recommended-on-premises-encoders"></a>推奨のオンプレミス エンコーダー
Azure Media Services でライブ ストリーミングを行う際には、チャネルでの入力ストリームの受信方法を指定できます。 ライブ エンコード チャネルを使用したオンプレミス エンコーダーを使用する場合、エンコーダーでは、出力として高品質のシングルビットレート ストリームをプッシュする必要があります。 パススルー チャネルを使用したオンプレミス エンコーダーを使用する場合、エンコーダーでは、目的の出力品質をすべて満たした出力として、マルチビット レート ストリームをプッシュする必要があります。 詳細については、「[Live streaming with on-prem encoders (オンプレミス エンコーダーを使用したライブ ストリーミング)](media-services-live-streaming-with-onprem-encoders.md)」を参照してください。

Azure Media Services では、RTMP を使用した、次のいずれかのライブ エンコーダーを出力として使用することを推奨しています。
- Adobe Flash Media Live Encoder 3.2
- Haivision Makito X HEVC
- Telestream Wirecast 8.1
- Teradek Slice 756
- TriCaster 8000
- Tricaster Mini HD-4

Azure Media Services では、マルチビットレートの Smooth Streaming を使用した、次のいずれかのライブ エンコーダーを出力として使用することを推奨しています。
- Ateme TITAN Live
- Cisco Digital Media Encoder 2200
- Elemental Live
- Envivio 4Caster C4 Gen III
- Imagine Communications Selenio MCP3
- Media Excel Hero Live

> [!NOTE]
> ライブ エンコーダーではパススルー チャネルにシングルビットレート ストリームを送信することができますが、クライアントへのアダプティブ ビットレート ストリーミングができなくなるため、この構成は推奨されません。

## <a name="how-to-become-an-on-prem-encoder-partner"></a>オンプレミス エンコーダー パートナーになる方法
Media Services は、Azure Media Services オンプレミス エンコーダー パートナーとして企業のお客様にエンコーダーを推奨することで、製品の販売を促進します。 オンプレミス エンコーダー パートナーになるには、オンプレミス エンコーダーと Media Services との互換性を確認する必要があります。 これを行うには、次の検証を実行します。

パススルー チャネルの検証
1. Azure Media Services アカウントを作成するか、またはアカウントにアクセスします
2. **パススルー** チャネルを作成し、起動します
3. マルチビット レートのライブ ストリームをプッシュするようにエンコーダーを構成します。
4. 公開済みのライブ イベントを作成します
5. ライブ エンコーダーを約 10 分間実行します
6. ライブ イベントを停止します
7. 資産 ID、ライブ アーカイブの公開済みストリーミング URL、およびライブ エンコーダーから使用されている設定とバージョンを記録します
8. 各サンプルの作成後に、チャネルの状態をリセットします
9. エンコーダーでサポートされているすべての構成について、手順 3 ～ 8 を繰り返します (必要に応じて、広告信号/キャプション/異なるエンコード速度を使用します)

ライブ エンコード チャネルの検証
1. Azure Media Services アカウントを作成するか、またはアカウントにアクセスします
2. **ライブ エンコード**チャネルを作成し、起動します
3. シングルビット レートのライブ ストリームをプッシュするようにエンコーダーを構成します。
4. 公開済みのライブ イベントを作成します
5. ライブ エンコーダーを約 10 分間実行します
6. ライブ イベントを停止します
7. 資産 ID、ライブ アーカイブの公開済みストリーミング URL、およびライブ エンコーダーから使用されている設定とバージョンを記録します
8. 各サンプルの作成後に、チャネルの状態をリセットします
9. エンコーダーでサポートされているすべての構成について、手順 3 ～ 8 を繰り返します (必要に応じて、広告信号/キャプション/さまざまなエンコード速度を使用します)

持続時間の検証
1. Azure Media Services アカウントを作成するか、またはアカウントにアクセスします
2. **パススルー** チャネルを作成し、起動します
3. マルチビット レートのライブ ストリームをプッシュするようにエンコーダーを構成します。
4. 公開済みのライブ イベントを作成します
5. ライブ エンコーダーを 1 週間以上実行します
6. ライブ イベントを停止します
7. 資産 ID、ライブ アーカイブの公開済みストリーミング URL、およびライブ エンコーダーから使用されている設定とバージョンを記録します

最後に、amsstreaming@microsoft.com 宛に電子メールを送信して、記録した設定とライブ アーカイブ パラメーターを Media Services に送信します。電子メールを受信すると、Media Services はライブ エンコーダーからのサンプルに対する検証テストを実行します。 このプロセスに関して質問がある場合は、Media Services に問い合わせることができます。