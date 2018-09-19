これは  リポジトリの[ issue をアーカイブ]()したものです。

# Github 運用：fork 先からのマージ手順

- 2017/11/16 07:58 by hidao80
- State: closed
- Archive of https://api.github.com/repos/Qithub-BOT/Qithub-API

## 本文

## 提案

現在、fork 先リポジトリ（以下forked）から本リポジトリへのマージするときの手続きは

1. 本リポジトリにブランチを作る
2. forked にブランチを作る or 本リポジトリのブランチを forked にマージ
3. forked で編集
4. 本リポジトリのブランチにマージ
5. 本リポジトリの master にマージ

となっていますが、あまりに要領が悪い（手間が多すぎる）と思います。

forked で SideCI を使って本リポジトリを汚さないという考え方は良いと思うのですが、KISS でないと思います。

## 自分の案

下記 2 点をクリアする場合、本リポジトリの master に直接マージすることを認めてはどうでしょうか。

1. forked でブランチを切っている
2. forked で動作確認 or レビューをクリアしている

ブランチをつくる元々の意義は

- master を常に稼動可能状態に保つ
- 1マージ（=PR）を意味のあるコミットのまとまりとする

ことだと思います。  
であれば、forked のブランチを本リポジトリの master に直接 PR しても、意義が満足しているので問題はないと考えます。

また、マージされるブランチは forked にしか存在せず、本リポジトリを汚しません。  
そのため、本リポジトリでマージするごとに毎回行なっていたブランチの削除は発生しません。  
**forked にできたブランチの後始末は forked オーナーの責任で、任意にすれば良い**と考えます。

## 補足

#57 参照。

## TL;DR（結論 2017/11/16 現在）

- Fork 先のブランチは Origin の master に直接マージ PR して OK。

----------------

- [x] 過去の Issues も検索しましたが該当するものはありませんでした。

-----

## コメント

-----

##### 344859238

2017/11/16 09:05 by KEINOS

なるほど。確かに煩雑になってきたな、と感じていました。

NightlyBuilt や新バージョンの同時開発といった用途とは違うので、「Fork 先のブランチは Origin の master に直接マージ PR して OK」に 👍 です。

現在、切っちゃったブランチ以降はこの提案で行きましょう！

-----

##### 344859831

2017/11/16 09:08 by hidao80

👍

-----

##### 344860403

2017/11/16 09:10 by hidao80

TL;DR 、結論しました。

-----

##### 344861434

2017/11/16 09:14 by KEINOS

👍 😄 