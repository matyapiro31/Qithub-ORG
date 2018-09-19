これは  リポジトリの[ issue をアーカイブ]()したものです。

# プロセス：「新着Qiita記事」の宣言と取りまとめトゥートの公開ステータス

- 2017/11/17 04:23 by KEINOS
- State: closed
- Archive of https://api.github.com/repos/Qithub-BOT/Qithub-API

## 本文

## 提案

そろそろ「新着Qiita記事」の始まりと終わりの２トゥートを「公開」で出す時期かなと思います。 （issue #11 より）

### 現在
- 宣言トゥート（始まり）　　：未収載
- 新着記事トゥート（中間）　：未収載（Qiitadonian記事）、非公開（その他ユーザー）
- 取りまとめトゥート（終了）：未収載

例：https://qiitadon.com/@qithub/99017294210537809

## 自分の案

公開と同時に一気に BOT の認知が上がると思うので、 issue #42 のプラグインの規制緩和（クエリの引数をそのまま渡す実装）が出来ると同時に行うのが適切なタイミングかと。

----------------

- [x] 過去の Issues も検索しましたが該当するものはありませんでした。

----------------

## TL;DR（進捗 2017/11/18 現在）

- issue #42 の実装が公開できるタイミングで、宣言トゥートと取りまとめトゥートを公開する予定
- 宣言・取りまとめの公開設定の PR で issue クローズ予定


-----

## コメント

-----

##### 345251617

2017/11/17 14:02 by hidao80

👍👌😊

#42 の実装が公開できるタイミングで、宣言トゥートと取りまとめトゥートを公開するに👍

-----

##### 345267858

2017/11/17 15:04 by KEINOS

👍 

では、宣言・取りまとめを公開設定にした PR でこの issue はクローズする方向で！


-----

##### 346991898

2017/11/26 08:16 by KEINOS

PR #68 で fix しましたー。本場環境にデプロイすると「宣言トゥート」と「取りまとめトゥート」は「公開」ステータスでトゥートされるハズ。
いよいよ、公開っすかー。((((; ﾟДﾟ)))ｶﾞｸﾌﾞﾙ

-----

##### 347040079

2017/11/26 21:32 by hidao80

いよいよ公開ですね！😊

でもまあ、βテスト的な立ち位置であることを強調して、アーリーアダプタな人たちに触ってもらいましょう。

稼働が始まらないと（利用してもらわないと）気がつかない不具合もありそうですし。