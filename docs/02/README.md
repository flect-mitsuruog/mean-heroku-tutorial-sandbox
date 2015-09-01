# アプリケーション構成の確認

1. MEANスタックとは
1. インフラ構成について
1. フロントエンド構成について
1. バックエンド構成について

## 1. MEANスタックとは
MEANスタックとは、Webアプリケーションを構築するために利用する技術スタックです。  
Node.jsを使った場合に良く利用する構成の頭文字を取って名前をつけたものです。

- __M__：MongoDB
- __E__：Express
- __A__：AngularJS
- __N__：Node.js

## 2. インフラ構成について

ハンズオンではLocal環境とHeroku環境(PaaS)の両方を利用します。  
Local環境でインストールされている一部ソフトウェアは、Heroku上では`アドオン`という形で利用します。

// TODO
__簡単な関連図（ローカル対Heroku）__

## 3. フロントエンド構成について

フロントエンドの構成は次のようになっています。
```
├── client
│   ├── app                 - フロントエンド側のアプリケーション一式
│   ├── assets              - 画像ファイルなど静的リソース
│   ├── components          - 再利用可能なUIコンポーネント(navbarなど)
```

フロント側のコードを変更する際は、`client`配下のファイルを変更していきます。  
`client/app`配下には、各画面をコンポーネントという形で分割して配置しています。
```
main
├── main.js                 - Routes(画面コンポーネントとURLマッピング)
├── main.controller.js      - Controller(ロジック)
├── main.controller.spec.js - Test
├── main.html               - View(テンプレート)
└── main.less               - Styles
```

## 4. バックエンド構成について
バックエンドの構成は次のようになっています。

```
└── server
    ├── api                 - APIコード一式
    ├── auth                - 認証系の共通部品
    ├── components          - 再利用可能なコンポーネント
    ├── config              - アプリの設定ファイル系
    │   └── local.env.js    - ローカル環境設定ファイル
    │   └── environment     - 各環境ごとの設定ファイル(dev, test, prod)
    └── views               - 画面(エラーページ)
```
バック側のコードを変更する際は、`server`配下のファイルを変更していきます。  
`server/api`配下には、各APIを分割して配置しています。

```
thing
├── index.js                - Routes(APIとURLマッピング)
├── thing.controller.js     - Controller(ロジック)
├── thing.model.js          - Database model(エンティティ)
├── thing.socket.js         - Register socket events(今回は利用しません！)
└── thing.spec.js           - Test
```

----
[:point_right: 3. Herokuの準備とデプロイ](../03)

[:point_left: 1. 開発環境の準備](../01)  
