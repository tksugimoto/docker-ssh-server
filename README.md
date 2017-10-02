# ssh server on docker
## 事前準備
1. Docker, Docker Composeをインストール
1. ssh公開鍵を作成
    ```
    ssh-keygen
    ```
1. 作成された公開鍵(`*.pub`)を`./sshd/ssh-pub-keys/` ディレクトリに移動
    * ファイル名は自由（`.pub`拡張子の公開鍵すべてが使えるようになる）
1. ssh serverの待ち受けIP:PORTを環境変数設定 (`.env`ファイル)
    * `cp .env.sample .env`
    * `.env` ファイル内 `SSHD_BIND_IP_PORT` 環境変数を編集

## コンテナ作成
```
docker-compose up
```
* ※ 公開鍵の共有は初回(build時)のみ
