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

## docker-outside-of-docker
- 主に Windows Subsystem for Linux で docker を動かしている場合に `docker ps` を実行しやすくする。
    1. コンテナに `ssh`
    1. `docker ps` で兄弟関係のコンテナをすべて見れる
- Portforward で ホスト側からしか繋がらない Proxy への転送にも使えるはず
    1. Portforward設定を追加
    1. コンテナに `ssh`

