# 課題説明
- gsskt_backend のリポジトリで、 `practice/summer-intern/diary` をcheckout してください。
- このブランチから、 `practice/summer-intern/diary/{@your_name}` という形式で作業ブランチを切って下さい。
- このブランチには、 `/{@version}/diaries` 系のエンドポイントが仮で実装されているので、このエンドポイントを完成させて下さい。
- 追加で作成するテーブルのDDLはPullRequestに記載して下さい。

# 機能要件
## [GET] `/{@version}/diaries`
- 日記の一覧を取得することができる
- liked_countの多い順、createdAtの新しい順、updatedAtの新しい順でソートできる
- デフォルトではcreatedAtの新しい順で返却される

## [POST] `/{@version}/diaries`
- `title`, `body` を送信することで新しい日記を投稿することができる`
- `author_id` は `gs_users.ID` と同じ値を格納する
- 会員以外からのリクエストはエラーとする

## [GET] `/{@version}/diaries/{@id}`
- 指定されたIDの日記の情報を取得できる
- 存在しない日記のIDが指定された場合はエラーとする

## [PATCH] `/{@version}/diaries/{@id}`
- `title`, `body` を送信することで指定されたIDの日記を更新することができる
- `updatedAt` を更新する
- 日記の投稿主以外からのリクエストはエラーとする

## [DELETE] `/{@version}/diaries/{@id}`
- 指定されたIDの日記を削除することができる
- 日記の投稿主以外からのリクエストはエラーとする

## [POST] `/{@version}/diaries/{@id}/like`
- 指定されたIDの日記にイイねすることができる
- 会員以外からのリクエストはエラーとする

## [DELETE] `/{@version}/diaries/{@id}/like`
- 指定されたIDの日記へのイイねを解除することができる
- 会員以外からのリクエストはエラーとする
