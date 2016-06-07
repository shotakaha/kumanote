+++
author = "Shota"
categories = ["homebrew", "go", "hugo"]
date = "2016-06-04T11:47:54+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "Homebrewのgoをインストール"

+++
インストール済みの`hugo`パッケージの情報を調べたところ、依存パッケージの`go`がインストールされてないことが分かりました。

というのも、これまでMacPortsをメインで使っていたため、`go`はMacPortsのパッケージを使っていたからなのですが、今回、これをHomebrewのにすることにしました。

（`hugo`はMacPortsにパッケージがないため、Homebrewを入れていました。自分でビルドするのもめんどうだと思ったので）


# 現状の確認

まずは現状の確認から。
MacPortsの`go`が使われていることを確認します。
記憶にないのですが、`go @1.6`と`go-1.4`が入ってました。

``` sh
$ where go
/opt/local/bin/go

$ port installed | ag go
  go @1.6.2_0 (active)
  go-1.4 @1.4.3_0 (active)
```

まず、MacPortsの`go`を`deactivate`します。

``` sh
$ sudo port deactivate go go-1.4
--->  Deactivating go @1.6.2_0
--->  Cleaning go

--->  Deactivating go-1.4 @1.4.3_0
--->  Cleaning go-1.4

$ where go
go not found
```

# brew info go

次に、Homebrewの`go`パッケージを確認します。

``` sh
$ brew info go
go: stable 1.6.2 (bottled), HEAD
Go programming environment
https://golang.org
Not installed
From: https://github.com/Homebrew/homebrew-core/blob/master/Formula/go.rb
==> Options
--without-cgo
	Build without cgo
--without-godoc
	godoc will not be installed for you
--without-race
	Build without race detector
--without-vet
	vet will not be installed for you
--HEAD
	Install HEAD version
==> Caveats
As of go 1.2, a valid GOPATH is required to use the `go get` command:
  https://golang.org/doc/code.html#GOPATH

You may wish to add the GOROOT-based install location to your PATH:
  export PATH=$PATH:/usr/local/opt/go/libexec/bin
```

オプションがいくつかありますが、今回は何も付けずにインストールします。

``` sh
$ brew install go
==> Downloading https://homebrew.bintray.com/bottles/go-1.6.2.el_capitan.bottle.tar.gz
######################################################################## 100.0%
==> Pouring go-1.6.2.el_capitan.bottle.tar.gz
==> Caveats
As of go 1.2, a valid GOPATH is required to use the `go get` command:
  https://golang.org/doc/code.html#GOPATH

You may wish to add the GOROOT-based install location to your PATH:
  export PATH=$PATH:/usr/local/opt/go/libexec/bin
==> Summary
🍺  /usr/local/Cellar/go/1.6.2: 5,778 files, 325.3M
```

インストール後のメッセージには`GOPATH`を設定しとくといいよ、とあるので、`GOPATH`とはなんなのかちょっと調べてみました。


# GOPATH

`GOPATH`のドキュメントを探してみました。
以下に日本語のドキュメントがあったので、抜粋しました。

* [GOPATH環境変数](http://golang-jp.org/doc/code.html#GOPATH )

> GOPATH環境変数はワークスペースの場所を示す。
  これがGoコードを開発する際に**設定が必要な唯一の環境変数**のはず。
  始めるにあたり、ワークスペースディレクトリを作成し、適宜GOPATHをセットする。
  ワークスペースはどこでも好きな場所に置いてよい。
  ただし、**Goをインストールしたパスを指定してはいけない！**
  このドキュメントでは`$HOME/go`として説明している。

ということで、いまのところ`Go言語`でプログラムを作ることはないので、設定せずに放置しておきます。
