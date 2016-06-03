+++
categories = ["git", "git-flow", "magit", "emacs"]
date = "2015-12-01T17:17:23+09:00"
description = ""
image = "/img/about-bg.jpg"
tags = ["git", "gitflow"]
title = "magit-gitflowの使い方"

+++

# magit-gitflowを使う

さてさて、Emacs + Gitには欠かせない`Magit`パッケージ。
実は`magit-gitflow`という`git-flow`用の拡張がある。
`MELPA`からインストールできる。

GitHubページにあるとおりにEmacsの設定をし、
上記のようにリポジトリの設定ができていれば、準備はOK。

`magit-status`の画面で`C-f`すると`magit-gitflow`ポップアップが表示される。
あとは普段`Magit`を使うときみたいにキーを入力するだけ。

これで`git-flow`のコマンドを知らなくてもなんとなく操作できるようになった。
あとは`git-flow`のコンセプトを理解すればよい。



コンセプトというと大げさだけど`git-flow`の使い方、というか、
やってることと、というか、を知りたくて調べたときのメモ。

# 参考サイト

- [git-flow cheatsheet](http://danielkummer.github.io/git-flow-cheatsheet/index.ja_JP.html )
