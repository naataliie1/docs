| ポート      | サービス  | 説明                                                                                                    |
| -------- | ----- | ----------------------------------------------------------------------------------------------------- |
| 22       | SSH   | Git over SSHのアクセス。 パブリック／プライベートリポジトリのクローン、フェッチ、プッシュ操作がサポートされています。                                     |
| 25       | SMTP  | 暗号化（STARTTLS）付きのSMTPサポート。                                                                             |
| 80       | HTTP  | Webアプリケーションへのアクセス。 *SSL が有効な場合、すべての要求は HTTPS ポートにリダイレクトされます。*                                         |
| 122      | SSH   | インスタンスのシェルへのアクセス。 *デフォルトのSSHポート（22）は、アプリケーションのgit+sshネットワークトラフィック専用です。*                               |
| 161/UDP  | SNMP  | ネットワークモニタリングプロトコルの処理に必要。                                                                              |
| 443      | HTTPS | Webアプリケーション及びGit over HTTPSのアクセス。                                                                     |
| 1194/UDP | VPN   | High Availability設定でのセキュアなレプリケーションネットワークトンネル。                                                         |
| 8080     | HTTP  | プレーンテキストの Webベースの {{ site.data.variables.enterprise.management_console }}。 *SSL を手動で無効にしない限り必要ありません。* |
| 8443     | HTTPS | セキュアな Webベースの {{ site.data.variables.enterprise.management_console }}。 *基本的なインストールと設定に必要です。*          |
| 9418     | Git   | シンプルなGitプロトコルのポートです。 パブリックリポジトリのクローンとフェッチのみができます。 *暗号化されていないネットワーク通信です。*                              |