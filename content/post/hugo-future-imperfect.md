+++
author = "Shota"
categories = ["hugo"]
date = "2016-05-10T22:05:32+09:00"
description = "いい感じのHugo Theme"
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "Hugo Future Imperfectがいい感じ"

+++

Hugoの[Discussion](https://discuss.gohugo.io/t/very-nice-new-theme-for-blogging/2956 )で紹介されてたので、使ってみることにした。

[作成者のウェブサイト](https://jpescador.com/blog/future-imperfect-theme-release-on-the-go-hugo-static-website-engine/ ) にも、使い方が書いてあった（ほとんどREADMEに書いてある内容）ので、その通りにテーマをインストールする。


# テーマのインストール


``` sh
$ cd $KUMANOTE/themes
$ git clone https://github.com/jpescador/hugo-future-imperfect.git
$ rm -rf hugo-future-imperfect/.git/
```

``` sh
$ cd $KUMANOTE
$ emacs config.toml
```

``` toml
theme = "hugo-future-imperfect"
```

まだまだ足りないパーツはあるものの、結構いい感じなので、採用！


# いいところ！

* シンプルな２カラム
* 配色もシンプル
* 画面上部のナビゲーションバーもすてき
* サイドバーに最近のポストが表示される
* いい感じのページネータが付いてる

# よくないところ（＝改善したいところ）

* index.htmlがない
* 単一ページ（/layouts/page/single.html）もない
* ページの配色にアクセントがない
* 日本語だとフォントがいまいち？
