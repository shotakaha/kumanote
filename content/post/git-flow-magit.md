+++
categories = ["git", "git-flow", "magit", "emacs"]
date = "2015-12-01T17:17:23+09:00"
description = ""
image = "/img/about-bg.jpg"
tags = ["git", "gitflow"]
title = "magit-gitflowの使い方"

+++
さて、`git-flow`を使うことにしたので、それをEmacsの`Magit`から使える拡張パッケージ`magit-gitflow`も使うことにする。


# Magit = Emacs + Git

Emacsには、元々`vc`という汎用的なバージョン管理コマンド機能がついているんだけど、汎用的であるがゆえ、個々のバージョン管理コマンドの個性が活かせないデメリットもある。

`Magit`は、Gitに特化したパッケージで、Gitでできることがほぼ全てEmacs上でできるようになっている。

# magit-flow = Magit + git-flow

`magit-gitflow`は、その名のとおり、`Magit`の`git-flow`拡張版。
これをいれておけば、`git-flow`のコマンドを知らなくてもなんとなく操作できるようになる。

使い方は`magit-status`の画面で`C-f`するだけ。
`magit-gitflow`ポップアップが表示されるので、あとは普段`Magit`を使うときみたいにキーを入力するだけ。
