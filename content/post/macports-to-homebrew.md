+++
author = ""
categories = ["homebrew", "macports"]
date = "2016-06-02T10:50:44+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "MacPortsからHomebrewへ"

+++
`ROOT6`がHomebrewでインストールできるみたいなので、Homebrewを本格的に使ってみようかなと思っています。
ただ、あいにくHomebrewとMacPortsは相性がよくないようで、一緒に使うことは非推奨らしいです。(現在は Hugo のみ Homebrew でインストールしています)

かといって、これまででMacPorts依存症になってしまっているため、一気に乗り換えるのは不安が。。。
ということで、依存関係の多いパッケージはたぶんめんどくさいことになるので、とりあえず単体のパッケージから始めます。
最初は`nkf`。


# 現状の確認

とりあえず`nkf`のパスとバージョンを確認しました。
MacPortsの`nkf (/opt/local/bin/nkf)`が使われていることが分かります。

``` sh
$ where nkf
/opt/local/bin/nkf

$ nkf --version
Network Kanji Filter Version 2.1.3 (2013-11-22)
Copyright (C) 1987, FUJITSU LTD. (I.Ichikawa).
Copyright (C) 1996-2013, The nkf Project.
```

# Homebrewでパッケージ検索＆インストール

Homebrewに`nkf`があるか探します。
ありました。

``` sh
$ brew search nkf
nkf
```

`brew install`コマンドを使って`nkf`をインストールします。

``` sh
$ brew install nkf
==> Downloading https://homebrew.bintray.com/bottles/nkf-2.1.4.el_capitan.bottle.tar.gz
######################################################################## 100.0%
==> Pouring nkf-2.1.4.el_capitan.bottle.tar.gz
🍺  /usr/local/Cellar/nkf/2.1.4: 4 files, 342.5K
```

パスを確認すると`/usr/local/bin/nkf`が追加されてます。

``` sh
$ where nkf
/opt/local/bin/nkf
/usr/local/bin/nkf
```

v2.1.4 (MacPortsより新しい？) がインストールされたみたいです。

``` sh
$ /usr/local/bin/nkf --version
Network Kanji Filter Version 2.1.4 (2015-12-12)
Copyright (C) 1987, FUJITSU LTD. (I.Ichikawa).
Copyright (C) 1996-2015, The nkf Project
```


# MacPortsのnkfをdeactivateする

MacPortsの`nkf`はとりあえず`deactivate`しておきます。
本当に不要になったときに`uninstall`します。

``` sh
$ sudo port deactivate nkf
--->  Deactivating nkf @2.1.3_3
--->  Cleaning nkf
```

パスを確認すると`/opt/local/bin/nkf`が削除されています。

``` sh
$ where nkf
/usr/local/bin/nkf
```

# まとめ

依存関係のない`nkf`を、以下の手順でHomebrew版に変更しました。

1. Homebrewでパッケージを探して、インストールする
2. MacPortsのパッケージをdeactivateする

こんな感じで少しずつHomebrewへ移行していこうと思います。
