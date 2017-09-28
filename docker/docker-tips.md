## Dockerとは

- Dockerはコンテナ型仮想化と呼ばれる技術の実装の1つ
- 手元の開発環境では動いていたが、本番環境にデプロイしたら動きませんでしたや、環境変数が違う、実行環境のバージョンやライブラリのバージョンが違うときに、プロダクションの環境にログインしてこれらを操作する、と言ったことはやりたくない
- 今よく使われているサーバ仮想化はハードウェアの機能を全てソフトウェアで実装するという高度な仕組みが必要で、実装はいまだ複雑なものになっている
- 一方コンテナ型仮想化はOSの上に、”コンテナ”と呼ばれる仮想的なユーザ空間を提供します。ユーザ空間とはユーザがアプリケーションを実行するための、一揃いのリソースが提供される空間。通常は一つのOSの上に一つのユーザ空間だが、コンテナ型仮想化では、一つのOSの上で仮想的なユーザ空間を複数提供できる

![docker01.jpg](resources/0952C63000C3DDB57AC0933CF8EE733D.jpg)

- Dockerでは`Dockerファイル`と呼ばれる、コンテナの内容をコードとして記述できる仕組みを備えている
- これにより、コンテナ無いのOSやライブラリ、環境変数といった内容をパッケージングしたり、保存したり、移動させたりといった事が可能。中身をそのままバイナリファイル化したのがDockerイメージ。
- DockerHubには様々なアプリケーションのオフィシャルイメージが登録されている

## Dockerのメリット
- ビルドもデプロイも高速
- ゲストOSが無く、カーネルを共有しているのでオーバーヘッドが少ない
- プラットフォームやハードウェアからの隔離環境
- ラップトップで動いているものをそのままサーバに持っていける

### オーバーヘッド
余計にかかってしまうコストのこと

## Dockerのデメリット
- サーバ仮想化では仮想サーバ毎にOSが選択できるのに対して、コンテナ型仮想化はその構造上、全てのコンテナで同一のOS（カーネル）を利用することが前提である

## Docker Cleanup Commands
[元記事](https://www.calazan.com/docker-cleanup-commands/)

### Delete all stopped containers (including data-only containers)
```sh
docker rm $(docker ps -a -q)
```

### Delete all 'untagged/dangling' (<none>) images
```sh
docker rmi $(docker images -q -f dangling=true)
```

## docker container login

```sh
docker exec -it {container_id} /bin/bash
```