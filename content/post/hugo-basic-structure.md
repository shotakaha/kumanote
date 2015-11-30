+++
date = "2015-11-29T21:10:49+09:00"
draft = true
title = "Hugoドキュメントの基本"
categories = ["hugo"]
+++

Hugoドキュメントを読んでいて [Contents](http://gohugo.io/content/organization/ ) の部分を理解しておくことは大事な気がしたので、そのメモである。
キーワードは `Front Matter`、`Section`、`Type`、`Archetypes` の４つ。

#### 1. Front Matter

`Front Matter`は`hugo new` でファイルを作成した時にページ上部に自動生成される`+++`（TOMLの場合）で囲まれた部分のこと。
ここにはページ毎のメタ情報を書き込むことができる。
デフォルトでは `date`、`draft`、`title`の３つだが、[Template Variables](http://gohugo.io/templates/variables/)にある変数（全部小文字でOK）や、独自の変数（自分で設定する必要がある）を追記することができる。

#### 2. Section
`Section`はそのコンテンツのパスの一番上のディレクトリ部分のこと。
たとえば、この記事（パスは`/post/hugo-basic/structure/index.html`になってるはず）だと `post` の部分になる。

#### 3. Type
`Type`はデフォルトだと`Section`と同じになるが、`Front Matter`のところに`type = photo`と書けば`photo`タイプに変更できる。
この`Type`に応じてカスタマイズしたテンプレートを用意することができる。
この記事では`.md`の`Front Matter`で何も指定していないので、上と同じ`post`である。

#### 4. Archetypes

`Archetypes`は`Front Matter`のテンプレート的なものである。
先に述べたように`Front Matter`は自由に追記可能だが、毎回入力する内容はテンプレートにしておくとよい。
テンプレートのファイル名は`Type`と同じにする。
つまり`post`タイプのコンテンツのテンプレートは`/archetypes/post.md`。
`Type`の一致するファイルがない場合は`/archetypes/default.md`が使われる。

全体設定で`themes = THEMENAME`を設定している場合は`THEMENAME/archetype/TYPE.md`、`THEMENAME/archetype/default.md`の順番に使われる。
