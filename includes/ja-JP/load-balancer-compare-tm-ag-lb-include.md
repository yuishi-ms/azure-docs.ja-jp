## <a name="load-balancer-differences"></a>Load Balancer の相違点

Microsoft Azure を使用してネットワーク トラフィックを分散するには、さまざまなオプションがあります。 これらのオプションはそれぞれ動作が異なり、さまざまな機能セットが含まれ、さまざまなシナリオをサポートします。 オプションは単独または組み合わせて使用することができます。

* **Azure Load Balancer** は、トランスポート層で動作します (OSI ネットワーク参照モデルの第 4 層)。 これは、同じ Azure データ センターで実行するアプリケーションのインスタンス間で、トラフィックのネットワーク レベルの分散を提供します。
* **Application Gateway** は、アプリケーション層で動作します (OSI ネットワーク参照モデルの第 7 層)。 これは、クライアント接続を終了して、バックエンドのエンドポイントへの要求を転送し、リバース プロキシ サービスとして機能します。
* **Traffic Manager** は、DNS レベルで動作します。  これは、DNS 応答を使用して、エンドユーザーのトラフィックをグローバルに分散されたエンドポイントに送信します。 その後、クライアントは、それらのエンドポイントに直接接続します。

次の表では、各サービスで提供される機能についてまとめています。

| サービス | Azure Load Balancer | Application Gateway | Traffic Manager |
| --- | --- | --- | --- |
| テクノロジ |トランスポート レベル (第 4 層) |アプリケーション レベル (第 7 層) |DNS レベル |
| サポート対象アプリケーション プロトコル |任意 |HTTP、HTTPS、および WebSocket |任意 (HTTP エンドポイントはエンドポイントの監視に必要です) |
| エンドポイント |Azure VM と Cloud Services のロール インスタンス |任意の Azure 内部 IP アドレス、パブリック インターネット IP アドレス、Azure VM、または Azure クラウド サービス |Azure VM、Cloud Services、Azure Web Apps および外部エンドポイント |
| VNet のサポート |インターネット接続と内部 (VNet) のアプリケーションの両方に使用できます |インターネット接続と内部 (VNet) のアプリケーションの両方に使用できます |インターネットに接続するアプリケーションのみをサポートします |
| エンドポイントの監視 |プローブ経由でサポート |プローブ経由でサポート |HTTP/HTTPS GET 経由でサポート |

Azure Load Balancer と Application Gateway では、ネットワーク トラフィックをエンドポイントに転送しますが、処理するトラフィックによってさまざまな使用シナリオがあります。 次の表は、2 つのロード バランサーの相違点を理解するために役立ちます。

| type | Azure Load Balancer | Application Gateway |
| --- | --- | --- |
| プロトコル |UDP/TCP |HTTP、HTTPS、および WebSocket |
| IP Reservation |サポートされています |サポートされていません |
| 負荷分散モード |5 組 (発信元 IP、発信元ポート、接続先 IP、接続先ポート、プロトコルの種類) |ラウンド ロビン<br>URL に基づくルーティング |
| 負荷分散モード (発信元 IP/スティッキー セッション) |2 組 (発信元 IP と接続先 IP)、3 組 (発信元 IP、接続先 IP、および接続先ポート)。 仮想マシンの数に基づいて、スケールアップまたはスケールダウンできます |Cookie ベースのアフィニティ<br>URL に基づくルーティング |
| 正常性プローブ |既定値: プローブ間隔 -15 秒。 循環から除外: 2 回連続のエラー。 ユーザー定義のプローブをサポートします |アイドル状態のプローブ間隔 30 秒。 5 回連続するライブ トラフィック障害またはアイドル モードでの単一のプローブ障害の後に除外。 ユーザー定義のプローブをサポートします |
| SSL オフロード |サポートされていません |サポートされています |
| URL ベースのルーティング | サポートされていません | サポートされています|
| SSL ポリシー | サポートされていません | サポートされています|
