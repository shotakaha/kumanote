+++
author = ""
categories = []
date = "2015-11-29T12:22:14+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "Hugoのテーマの選び方とインストール"

+++
Hugoを使ってウェブサイトを作成する場合、まずはテーマを選ぶとよい。
テーマは[Hugo - Site Showcase](https://gohugo.io/showcase/ )や、
[Hugo Themes Site](http://themes.gohugo.io)を見て選ぶ。

インストールは [Hugo - Installing Themes](https://gohugo.io/themes/installing/) の通りにやればOK。


# テーマ（startbootstrap-clean-blog）の設定

ブログ用に良さそうだったので[startbootstrap-clean-blog](http://themes.gohugo.io/startbootstrap-clean-blog/)をインストールすることにした。

``` sh
$ cd $KUMANOTE/themes
$ git clone https://github.com/humboldtux/startbootstrap-clean-blog.git
$ rm -rf startbootstrap-clean-blog/.git/
```

``` sh
$ cd $KUMANOTE
$ emacs config.toml
```

``` toml
theme = "startbootstrap-clean-blog"
```
