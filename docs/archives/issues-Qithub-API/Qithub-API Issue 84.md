これは  リポジトリの[ issue をアーカイブ]()したものです。

# プラグイン：help とバージョンの確認について

- 2017/12/18 06:29 by KEINOS
- State: closed
- Archive of https://api.github.com/repos/Qithub-BOT/Qithub-API

## 本文

## 相談

トゥートでプラグインを使う場合に、ヘルプでプラグインの概要が分かるようにしたい

## 自分の案

`@qithub:roll-dice --help` で500文字以内の使い方が返信される。


`@qithub:roll-dice --version` でプラグインのバージョンが返信される。


`@qithub:help` で、qithub の使い方概要が返信される。


## 実装案

プラグイン・ディレクトリの README.md の内容を返信するとか。

----------------

- [x] 過去の Issues も検索しましたが該当するものはありませんでした。
- 関連 issue #77 #86
----------------

## TL;DR（結論 2018/01/09 現在）

- Qithub の標準機能として採用
- `info.json` のファイル設置により実現させる（`info.json` の詳細な仕様に関しては issue #86 を参照）
- `help`プラグインも用意して `＠qithub:help` にてプラグインの使い方のヘルプとする

### 仕様

#### コマンドのフォーマット

    ＠qithub:<Name_Plugin> <Command_Args>

    例）
    ＠qithub:roll-dice 1d6
    ＠qithub:roll-dice --help
    ＠qithub:roll-dice --version
    ＠qithub:roll-dice --foo
    ＠qithub:roll-dice --bar

#### 動作仕様

以下の仕様によりヘルプ、バージョン、もしくはその他のプラグイン情報確認を実現する。

- `<Command_Args>` のコマンド引数が `--[key]` で始まっていた場合
    - `info.json` に記載された第１階層目のキー名（[key]）の値が表示される（プラグインは実行されない）
    - `info.json` に `help` と `version` のキーと値が記載されていればバージョンやヘルプを実装できる
- 引数が `--` で始まっていない場合は、プラグインを実行し、引数が渡される
- 各プラグインの同階層に `info.json` ファイルが設置してあった場合のみこの機能が有効になる。


  

-----

## コメント

-----

##### 352389439

2017/12/18 10:40 by hidao80

大筋 👍👌😄。

ですが、README と Usage は用向きが違うような…😅

現在の開発方針では、**プラグインの基底クラスを用意しない方針**だと思うので、`--help`や`--version`を**実装させる強制力に乏しい**気がします。🤔

プラグインの実装ガイドラインとしてはありですが、全てのプラグインが実装しているかというと、自信が持てない部分もあり。😅

## 案A

1. プラグイン実装内容ガイドラインを作る。
1. 内部的には CLI であることを明記。
1. コマンドはスペース区切りであることを明記。
1. `--help`、`--version`オプションの実装を**努力目標とする**ことを明記。
1. Qithub に `help` プラグインを標準搭載する。(=scripts/plugins/help/ を含んだ状態でリリースする)

-----

##### 352418799

2017/12/18 12:59 by KEINOS

では、まずは **Qithub のヘルプはプラグインで実装**し、その他のプラグインは `help` と `version` のオプション実装は必須ではなく README.md と同じレベルの**努力目標**ということにしましょう。

### 対案

現在、同一プラグイン内に複数言語の `main.xxx` があった場合、Qithub RESTful API 経由の場合はクエリで言語指定できるのですが、指定がない場合は内部リストで先にヒットしたものが実行されるようになっています。（`main.go`と`main.php`があった場合、指定がないと`php`が優先されるなど）

可能ならデフォルトの言語を指定してもらいたいのですが、そこで、"info.json"というファイルを `scripts/plugins/<YourPlugin>/info.json` に設置していた場合は、それらを読み込むのはどうでしょう。そこに「バージョン」や「ヘルプ」も記載する感じで。

```
{
    "version": "version number",
    "help": "Help msg",
    "default_ext": "php"
}
```
- [JSONのサンプル](https://paiza.io/projects/g_MjO3MIFnTc_wfZIJ6Rcw)

-----

##### 352424657

2017/12/18 13:25 by hidao80

なるほど！ help や version のデータを持っておき、**--help や --version は Qithub システム API に用意しておいて json だけ書けば動作するようにするのもアリ**ですね😁

-----

##### 353538175

2017/12/22 07:20 by KEINOS

結論を TL;DR に追記しました。

`help`プラグインを作成するなかで仕様の叩き台を作成したので issue #86 にあげました。

なので、この issue はクローズしてもいいかと。


-----

##### 353542739

2017/12/22 07:51 by KEINOS

> なので、この issue はクローズしてもいいかと。

やはり、`--help` と `--version` と **`help`プラグインの PR をしてから**でお願いします！



-----

##### 353544407

2017/12/22 08:02 by hidao80

👍

-----

##### 358219804

2018/01/17 07:26 by KEINOS

PR #88 で実装しましたので、クローズお願いし 💪 

`--version` や `--help` などのリクエスト時、プラグインの同階層に `info.json` があり JSON 配列のキーに該当キー（`--[key]`）があった場合に、その中身を返すようにしました。

-----

##### 358220031

2018/01/17 07:27 by hidao80

👌👍
