
# docker チートシート

## dockerの流れ
dockerの基本的な流れは次のような感じ
- イメージを取得する(pull）
  - コンテナを作る(create)
  - コンテナを起動する(start)
  - コンテナに接続する(exec)
  - コンテナを終了する(stop)
  - コンテナを削除する(rm)
- イメージを削除する(rmi)


それとは別に、何かを確認したい時はこんな感じ
- 既にもってるイメージの確認(docker images)
- 既にあるコンテナの確認(docker ps)

## dockerの基本的なコマンド
- dockerイメージの取得
  - docker pull イメージ:TAG
```
# CentOS6.8のイメージを取得（ダウンロード）する
docker pull centos:6.8
```

---
- 現在保有しているイメージの確認
  - docker images
  ```
  docker images
  ```
---
- コンテナ作る
  - docker create --name コンテナ名 イメージ:TAG
  ```
  # コンテナを作る。centos:6.8イメージから。my-centosという名前で。
  docker create -it --name mycentos centos:6.8
  ```
    - どうも、普通にdocker create --name mycentos centos:6.8 しただけだと、次にdocker startしても直ぐにexitしてしまうようだ・・・。

---
- イメージ取得して、コンテナ作って、起動して、bashに入る。
  - docker run -it --name コンテナ名 イメージ:TAG コマンド
  ```
  docker run -it centos /bin/bash
  ```

---
応用
---
- 持ってるイメージを全削除＝コンテナ全削除してイメージ全削除
```
docker rm `docker ps -aq`
docker rmi `docker images -aq`
```

---
- アタッチする(docker attach コンテナIDしても固まっちゃってる時)
```
docker exec -it コンテナID /bin/bash
```
  - docker attachは、CTRL+Cやexitで抜けた時、プロセス毎終了してしまう。
  - ので、docker execでアタッチした方が安全と思われる。
  -
  - docker execは、起動中のコンテナに、プロセスを追加するコマンド。
  - 典型的な使い方は、ターミナルへのアクセス。
