# 課題

ユーザーが日記を投稿・閲覧・いいねできる機能の API の実装を行う。
API を実装する上で必要なテーブルの設計も行う。

## 開発準備

1. [gsskt_backend](https://github.com/howtv/gsskt_backend) のリポジトリで `practice/summer-intern/diary` を checkout
1. `practice/summer-intern/diary` から `practice/summer-intern/diary_{@your_name}` という形式で作業ブランチを切る

gsskt_backend を立ち上げてリクエスト（[GET] `/3.0/service/diaries/1`）を送り以下表示されたら準備完了！

```json
{
    "id": 1,
    "authorID": 1111,
    "title": "志望企業が決められない",
    "body": "私はどこに向かっているのか",
    "likedCount": 3,
    "liked": false,
    "createdAt": "2019-09-02T16:16:22+09:00",
    "updatedAt": "2021-09-04T16:16:22+09:00"
}
```

## 提出方法

1. 作業内容をコミットしてプッシュ
1. プルリクエストを作成

プルリクエストの説明に作成したテーブルの DDL を記載して完了。

## 機能要件

### [GET] `/3.0/service/diaries`

- 全ユーザーの日記の一覧を取得することができる
- `likedCount` の多い順、`createdAt`の新しい順、`updatedAt` の新しい順でソートできる
    - デフォルトは `createdAt` の新しい順

### [POST] `/3.0/service/diaries`

- `title`、`body` を送信することで新しい日記を投稿できる
- `author_id` は `gs_users.ID` と同じ値を格納する
- 正会員以外からのリクエストはエラーとする

### [GET] `/3.0/service/diaries/{@id}`

- 指定された `id` の日記の情報を取得できる
- 存在しない日記の `id` が指定された場合はエラーとする

### [PATCH] `/3.0/service/diaries/{@id}`

- `title`, `body` を送信することで指定された `id` の日記を更新することができる
- `updatedAt` を更新する
- 日記の投稿主以外からのリクエストはエラーとする

### [DELETE] `/3.0/service/diaries/{@id}`

- 指定された `id` の日記を削除することができる
- 日記の投稿主以外からのリクエストはエラーとする

### [POST] `/3.0/service/diaries/{@id}/like`

- 指定された `id` の日記にいいねすることができる
- 正会員以外からのリクエストはエラーとする

### [DELETE] `/3.0/service/diaries/{@id}/like`

- 指定された `id` の日記へのいいねを解除することができる
- 正会員以外からのリクエストはエラーとする

## 参考 API

- 企業攻略の一覧を取得する
    - [GET] `service/company-guides`
- エントリーシートの単体詳細を取得する
    - [GET] `service/entrysheets/:id`
- 下書きを作成する
    - [POST] `service/drafts`
- 下書きを更新する
    - [PUT] `/service/drafts/:id`
- 下書きを削除する
    - [DELETE] `service/drafts/:id`
