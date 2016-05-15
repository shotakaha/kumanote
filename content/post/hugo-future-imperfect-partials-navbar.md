+++
author = "Kuma"
categories = ["hugo future imperfect"]
date = "2016-05-15T21:58:03+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "navbarの部分テンプレート"

+++

``/layouts/partials/navbar.html`` を見てみる
<!--more-->

``` html
<!-- Header -->
<header id="header">
  {{ if and (.IsNode) (or (.IsHome) (eq .Title "Posts")) }}
  <h1><a href="/">{{ .Site.Params.navbarTitle }}</i></a></h1>
  {{ else }}
  <h2><a href="/">{{ .Site.Params.navbarTitle }}</i></a></h2>
  {{ end }}
```

``` go
  {{ if and (.IsNode) (or (.IsHome) (eq .Title "Posts")) }}
```
（の部分がよく分からないけれど）に応じて ``<h1>`` か ``<h2>`` に変わるようになっている


---

``` html
  <nav class="links">
    <ul>
      {{ range .Site.Menus.main }}
      <li>
        <a href="{{ .URL }}">
          {{ with .Identifier }}
          <i class="{{ . }}">&nbsp;</i>{{ end }}{{ .Name }}
        </a>
      </li>
      {{ end }}
    </ul>
  </nav>
```

``.Identifier`` にはfont-awsomeのクラスを指定しておけばよい。

``` toml
[[menu.main]]
  name = "Archives"
  url = "/post"
  identifier = "fa fa-newspaper-o"
  weight = 1
```

上の ``navbarTitle`` の部分でホームに``/``を割り当てているので、``[menu.main]]``に``/``をいれなくてもよい。

---

``` html
  <nav class="main">
    <ul>
      {{ if $.Scratch.Get "shareNav" }}
      <li id="share-nav" class="share-menu" style="display:none;">
        <a class="fa-share-alt" href="#share-menu">Share</a>
      </li>
      {{ end }}
      <li class="search">
        <a class="fa-search" href="#search">Search</a>
        <form id="search" method="get" action="//google.com/search">
          <input type="text" name="q" placeholder="Search" />
          <input type="hidden" name="q" value="site:{{ .Site.BaseURL }}">
        </form>
      </li>
      <li class="menu">
        <a class="fa-bars" href="#menu">Menu</a>
      </li>
    </ul>
  </nav>
</header>
```

右上に表示される「シェア」ボタン。
これはこのままでOK。たぶん。


---

``` html
<!-- Menu -->
<section id="menu">

  <!-- Search -->
  <section>
    <form class="search" method="get" action="//google.com/search">
      <input type="text" name="q" placeholder="Search" />
      <input type="hidden" name="q" value="site:{{ .Site.BaseURL }}">
    </form>
  </section>
```

右上のGoogle検索ボックスだけど、このサイト自体をGoogle検索できるようにしてないので、オフにしたほうがいいのかもしれない。


---


``` html
  <!-- Links -->
  <section>
    <ul class="links">
      {{ range .Site.Menus.main }}
      <li>
        <a href="{{ .URL }}">
          <h3>
            {{ with .Identifier }}
            <i class="{{ . }}">&nbsp;</i>
            {{ end }}
            {{ .Name }}
          </h3>
        </a>
      </li>
      {{ end }}
    </ul>
  </section>
```

これも右上のコンテンツ一覧のボタン。なんて呼ぶのだろう？コンパクトにするボタン。


---


``` html
  <!-- Recent Posts -->
  <section>
    <ul class="links">
      <header>
        <h3>Recent Posts</h3>
      </header>
      {{ with .Site.Params.postAmount.sidebar }}
      {{ $.Scratch.Set "postLimit" . }}
      {{ else }}
      {{ $.Scratch.Set "postLimit" 5 }}
      {{ end }}

      {{ range first ($.Scratch.Get "postLimit") (where .Site.Pages "Type" "post") }}
      <li>
        <a href="{{ .Permalink }}"><p>{{ .Title }}</p></a>
      </li>
      {{ end }}
    </ul>
  </section>
```

左サイドバーに表示される「最新ポスト」の部分。

この部分って、部分テンプレートになってるかと思ったらベタ書きなんだ。

---


``` html
  <!-- Actions -->
  <!--
       <section>
       <ul class="actions vertical">
       <li><a href="#" class="button big fit">Log In</a></li>
       </ul>
       </section>
     -->
</section>
```

これはなんだろう？よく分からない。

「Log In」関係なのかな。よく分からない。
