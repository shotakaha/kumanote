+++
author = "Kuma"
categories = ["hugo future imperfect"]
date = "2016-05-15T18:37:07+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "トップページのテンプレート"

+++
[前回のポスト]({{< relref "hugo-future-imperfect.md" >}} )の「よくないところ」で「index.htmlがない」ことを挙げたが、実は ``layouts/index.html`` は存在してた。

１番最近のポストを１つ、表示するようになっている。
具体的に何をしているのか、上から順に確認していく。
<!--more-->

``` html
{{ partial "header" . }}
    {{ $.Scratch.Set "shareNav" true }}
    {{ partial "navbar" . }}
    <!-- Main -->
    <div id="main">
        {{ range first 1 (where .Site.Pages "Type" "post") }}
            {{ .Render "content-single" }}

            {{ partial "share-menu" . }}
        {{ end }}
    </div>
    {{ partial "sidebar" . }}
{{ partial "footer" . }}
```


# 上から順に

``` go
{{ partial "header" . }}
```
[header部分]({{< relref "post/hugo-future-imperfect-partials-header.md" >}} )


``` go
{{ partial "navbar" . }}
```
[navbar部分]({{< relref "post/hugo-future-imperfect-partials-navbar.md" >}} )


``` go
{{ .Render "content-single" }}
```


``` go
{{ partial "share-menu" . }}
```
[share-menu部分]({{< relref "post/hugo-future-imperfect-partials-share-menu.md" >}} )


``` go
{{ partial "sidebar" . }}
```
[sidebar部分]({{< relref "post/hugo-future-imperfect-partials-sidebar.md" >}} )


``` go
{{ partial "footer" . }}
```
[footer部分]({{< relref "post/hugo-future-imperfect-partials-footer.md" >}} )
