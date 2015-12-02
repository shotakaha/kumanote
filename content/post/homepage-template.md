+++
categories = ["Development"]
date = "2015-12-02T20:27:17+09:00"
description = "その１：眺めてみる"
draft = true
image = "/img/about-bg.jpg"
tags = ["hugo", "templates", "themes", "development"]
title = "ホームページのテンプレートを作成する"

+++

現在のテーマは`startbootstrap-clean-blog`にしている。
これをベースにホームページ（＝トップページ）のテンプレートを作成してみる。


# テーマのテンプレートを覗いてみる

今回はとりあえずテーマのテンプレートがどうなっているのかを眺めてみる。
テンプレートは`themes/startbootstrap-clean-blog/layouts/index.html`あるので、
内容を確認する。

``` bash
$ less themes/startbootstrap-clean-blog/layouts/index.html
```

とりあえず上から順番に眺めていく。

``` html
{{ partial "header.html" .}}
```

ここでは `themes/startbootstrap-clean-blog/layouts/partials/header.html`が読み込まれている。
このファイルの内容も後で確認することにする。


``` html
<header class="intro-header" style="background-image: url('{{ .Site.BaseURL}}/img/home-bg.jpg')">
```

`<header>`タグのクラスは`startbootstrap`のドキュメントを参照すること。
`'{{ .Site.BaseURL}}/img/home-bg.jpg'`の`.Site.BaseURL`には`config.toml`の`baseurl`が代入される。


``` html
<h1>{{ title .Site.Title }}</h1>
```

`.Site.Title`には`config.toml`の`title`が代入されるのだが、その前の`title`はなんだろう？
吐き出されたHTMLのソースを確認しても何もなかった。


``` html
{{ if isset .Site.Params "Description" }}<span class="subheading">{{ title .Site.Params.Description }}</span>{{ end }}
```

雰囲気だけで読んでみると、`if isset`とあるので、
`.Site.Params`（=`config.toml`の`[params]`）に`Description`がセットされてれば、
それを`<span>`タグを使って出力、ということなんだろう。
なるほど。`if`文はこうやって使えばいいのか。


``` html
{{ range first 4 (where .Data.Pages "Type" "post") }}
{{ .Render "summary"}}
{{ end }}
```

これも雰囲気だけで読み解く。
なんか分からない部分ばっかりだけど、`.Data.Pages "Type" "post"`に対して最初の４つだけ`.Render "summary"`する。
HTMLの出力を確認すると`post/`ディレクトリの４つの記事がレンダリングされている。

# まとめ

1. テンプレートの改造には`partials`を使えば良さそう
1. テンプレートは雰囲気で読むことができる
