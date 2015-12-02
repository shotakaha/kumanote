+++
categories = ["Development", "golang"]
date = "2015-11-30T22:48:39+09:00"
description = ""
draft = true
image = "/img/about-bg.jpg"
tags = ["go", "golang", "templates", "themes", "development"]
title = "startbootstrap-clean-blogテーマを使ってみる"

+++

# 新規ポストの作成と Front Matter

とりあえず`config.toml`を`startbootstrap-clean-blog`用に設定し、いつも通りポストを新規作成する。

``` bash
$ hugo new post/startbootstrap-clean-blog.md
```

そうすると、なにやら`Front Matter`がいつもと違う。増えてる。
ということで[前回の記事](../hugo-basic-structure/ )で分かったように、
`startbootstrap-clean-blog`の`archetype`（つまり`themes/startbootstrap-clean-blog/archetypes/post.md`）を覗いてみる。

すると

``` md
+++
tags = [
     "go",
     "golang",
     "templates",
     "themes",
     "development",
 ]
 categories = [
     "Development",
     "golang",
 ]
 image = "/img/about-bg.jpg" #optional image - "/img/about-bg.jpg" is the default
 description = ""
 draft = true
 +++
```

となっていて、実際に出力されたファイルは


``` md
+++
categories = ["Development", "golang"]
date = "2015-11-30T22:48:39+09:00"
description = ""
draft = true
image = "/img/about-bg.jpg"
tags = ["go", "golang", "templates", "themes", "development"]
title = "startbootstrap-clean-blog"
+++
```

となっていた。
