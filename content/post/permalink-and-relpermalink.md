+++
author = "Shota"
categories = ["hugo"]
date = "2016-05-18T12:10:56+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "Permalink と RelPermalink"

+++
[テンプレートで使える変数](https://gohugo.io/templates/variables/ ) に、``.Permalink``と``.RelPermalink``がある。
これらがどのように違うのか確認してみた。

以下のように、記事の見出し部分に``.Permalink``を使っているので、そこに``.RelPermalink``も併記してみた。
``canonifyurls``によって違いが出るはずなので``true/false``の場合で比較した。

``` html
<h3>Permalink   : <a href="{{ .Permalink }}">{{ .Title }}</a></h3>
<h3>RelPermalink: <a href="{{ .RelPermalink }}">{{ .Title }}</a></h3>
```

# canonifyurls = true のとき

``` toml
baseurl = "http://kuma.kek.jp/~shotakaha/kumanote/"
canonifyurls = true
```

``` html
<h3>Permalink   : <a href="http://kuma.kek.jp/~shotakaha/kumanote/post/permalink-and-relpermalink/">Permalink と RelPermalink</a></h3>
<h3>RelPermalink: <a href="http://kuma.kek.jp/~shotakaha/kumanote/post/permalink-and-relpermalink/">Permalink と RelPermalink</a></h3>
```

``content/`` の部分が ``baseurl`` に置換され、``Permalink`` も ``RelPermalink`` も差がない



# canonifyurls = false のとき


``` toml
baseurl = "http://kuma.kek.jp/~shotakaha/kumanote/"
canonifyurls = false
```

``` html
<h3>Permalink   : <a href="http://kuma.kek.jp/~shotakaha/kumanote/post/permalink-and-relpermalink/">Permalink と RelPermalink</a></h3>
<h3>RelPermalink: <a href="/~shotakaha/kumanote/post/permalink-and-relpermalink/">Permalink と RelPermalink</a></h3>
```

``RelPermalink``では、``baseurl``のトップドメインがなくなっている。
``baseurl``の部分が丸々なくなると思っていたので、意外。
そしてなんだか中途半端な印象。どこで使うんだろう。
