+++
author = "Shota"
categories = ["hugo"]
date = "2016-05-17T07:18:02+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "hugo server watch してる時に、ロックファイルを無視する設定"

+++
``hugo server --watch``を使っているときに、以下のようなエラーが出てくる時の対処法。

``` sh
...
ERROR: 2016/05/17 Cannot read symbolic link '.../kumanote/content/post/.#hugo-ignorefiles.md',
error was: lstat .../kumanote/content/post/... : no such file or directory
...
```

Hugo community の [hugo server watch should ignore emacs lock files](https://discuss.gohugo.io/t/hugo-server-watch-should-ignore-emacs-lock-files/1265 )や、そこで参照されている [issue1189](https://github.com/spf13/hugo/issues/1189 ) を参照すると、``config.toml``に``ignoreFiles=[無視したいファイルの正規表現]``を書けばよいらしい。

上記エラーでは、Emacsを編集してるときの中間ファイルである``.#``で始まるファイルが原因なので、以下のように書いてみた。

``` toml
ignoreFiles = [".#"]
```

あれ？前はこの方法でできてた気がするんだけど、うまくいってないみたい？
