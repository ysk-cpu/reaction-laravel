# Reaction

## 概要

化学反応の条件を比較するWebアプリです。特に現在僕が大学の研究室で扱っているテーマである「還元的ヘック反応」について、他の研究者が発表した条件の比較を便利に行う目的で作りました。同じことをエクセルでやっていたのですが、文字、数値しか扱えませんでした。同時に化学構造（画像）も見たかったので、Webの形をとろうと考えました。

## 使い方

```bash
$ make up
```

http://localhost またはhttp://reaction-test1.herokuapp.com にてトップページ('/')が見られます。比較表が表示されていて、その下に新規追加用のフォームがあります。入力して確認画面に移った後、送信するとトップにリダイレクトします。

## Container structure

```bash
├── app
├── web
└── db
```

### app container

- Base image
  - [php](https://hub.docker.com/_/php):8.0-fpm-buster
  - [composer](https://hub.docker.com/_/composer):2.0

### web container

- Base image
  - [nginx](https://hub.docker.com/_/nginx):1.18-alpine
  - [node](https://hub.docker.com/_/node):14.2-alpine

### db container

- Base image
  - [mysql](https://hub.docker.com/_/mysql):8.0

#### Persistent MySQL Storage

By default, the [named volume](https://docs.docker.com/compose/compose-file/#volumes) is mounted, so MySQL data remains even if the container is destroyed.
If you want to delete MySQL data intentionally, execute the following command.

```bash
$ docker-compose down -v && docker-compose up
```
