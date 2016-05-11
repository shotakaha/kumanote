+++
author = ""
categories = []
date = "2015-11-30T12:12:20+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "Hugoで新規ページを作成する方法"

+++
新しいページを作成するときは、 `hugo new` コマンドを使う。

``` sh
$ hugo new post/hugo-create-new-post.md
```

上記コマンドにより、`content/post/hugo-create-new-post.md` が作成されるので、エディタで開く。
何かしら Front Matter （`+++`で囲まれた部分）が挿入済みになっているはず。

``` sh
$ emacs content/post/hugo/create-new-post.md
```

``` toml
+++
date = "2015-11-29T12:12:20+09:00"
title = "hugo create new post"
draft = true

+++
（ここからMarkdownで書いていく）
```


Front Matter に自動挿入する値は `archetypes/default.md` で設定できる。
