+++
author = "Shota"
categories = ["homebrew"]
date = "2016-06-03T11:14:07+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "Homebrewの使い方"

+++
さて、昨日、MacPortsからHomebrewへの移行を決意しました。
ということで、`brew`コマンドの使い方を少し調べてみました。


# ヘルプを表示する

`brew help`は唯一、覚えるべきコマンドです。
単に`brew`だけでもよいです。

``` sh
$ brew help
$ brew
```

# インストール済みのパッケージ一覧を表示する

`brew list` を使います。
昨日、インストールした`nkf`と、過去にインストールした`hugo`が表示されました。

``` sh
$ brew list
hugo
nkf
```

インストールされているパスを知りたい場合は、`brew list FORMULA`とします。
実行ファイル、Bash補完、マニュアルの場所がリストされます。


``` sh
$ brew list hugo
/usr/local/Cellar/hugo/0.15/bin/hugo
/usr/local/Cellar/hugo/0.15/etc/bash_completion.d/hugo.sh
/usr/local/Cellar/hugo/0.15/share/man/ (24 files)
```

# パッケージの情報を知る

`brew info FORMULA`を使います。
試しに`hugo`の情報を見てみました。

ホームページはどこなのか、いつ取ってきたのか、とか分かりますし、依存パッケージなども分かります。

``` sh
$ brew info hugo
hugo: stable 0.15 (bottled), HEAD
Configurable static site generator
https://gohugo.io/
/usr/local/Cellar/hugo/0.15 (29 files, 15.6M) *
  Poured from bottle on 2016-02-15 at 10:49:24
From: https://github.com/Homebrew/homebrew-core/blob/master/Formula/hugo.rb
==> Dependencies
Build: go ✘
==> Caveats
Bash completion has been installed to:
  /usr/local/etc/bash_completion.d
```


# まとめ

とりえあず`brew help`が使えれば生きていけそうです。
