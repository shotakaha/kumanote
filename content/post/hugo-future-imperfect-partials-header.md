+++
author = "Kuma"
categories = ["hugo future imperfect"]
date = "2016-05-15T21:48:23+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "headerの部分テンプレート"

+++
``layouts/partial/header.html``を見てみた
<!--more-->


# タイトル部分


``` html
{{ with $.Scratch.Get "generalTitle" }}
  <title>{{ . }}</title>
{{ else }}
  {{ with .Title }}
    <title>{{ . }}</title>
  {{ else }}
    <title>{{ .Site.Title }}</title>
  {{ end }}
{{ end }}
```

## タイトルの適用順

1. generalTitle
2. Title
3. Site.Title


# メタデータ部分


``` html
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
{{ .Hugo.Generator }}
{{ partial "favicon" . }}

{{ with .Params.author }}
    <meta name="author" content="{{ . }}">
{{ end }}
{{ with .Description }}
    <meta name="description" content="{{ . }}">
{{ else }}
    {{ with .Site.Params.description }}
        <meta name="description" content="{{ . }}">
    {{ end }}
{{ end }}

{{ template "_internal/twitter_cards.html" . }}
{{ template "_internal/opengraph.html" . }}
{{ template "_internal/schema.html" . }}
{{ template "_internal/google_news.html" . }}
```

## authorの適用順

1. Params.author

## descriptionの適用順

1. Description
2. Site.Params.description


## social系のメタデータ

Hugoにテンプレートがあるらしい

``` go
{{ template "_internal/twitter_cards.html" . }}
{{ template "_internal/opengraph.html" . }}
{{ template "_internal/schema.html" . }}
{{ template "_internal/google_news.html" . }}
```


# CSSの設定

``` html
        <!--[if lte IE 8]><script src="/js/ie/html5shiv.js"></script><![endif]-->

        <!-- Keeping the deprecated param, minifiedFilesCSS, for now. The new param
             that replaces this is customCSS. Utilizing a scratch variable cssFiles
             to keep the deprecated param. -->
        {{ if isset .Site.Params "minifiedFilesCSS" }}
            {{ $.Scratch.Set "cssFiles" .Site.Params.minifiedFilesCSS }}
        {{ else if isset .Site.Params "customCSS" }}
            {{ $.Scratch.Set "cssFiles" .Site.Params.customCSS }}
        {{ else }}
            {{ $.Scratch.Set "cssFiles" false }}
        {{ end }}

        <!-- If the value "default" is passed into the param then we will first
             load the standard css files associated with the theme -->
        {{ if or (in ($.Scratch.Get "cssFiles") "default") (eq ($.Scratch.Get "cssFiles") false) }}
            <link rel="stylesheet" href="/css/google-font.css" />
            <link rel="stylesheet" href="/css/font-awesome.min.css" />
            <link rel="stylesheet" href="/css/main.css" />
            <link rel="stylesheet" href="/css/add-on.css" />
            <link rel="stylesheet" href="/css/monokai-sublime.css">
        {{ end }}

        {{ if ne ($.Scratch.Get "cssFiles") false }}
            {{ range $.Scratch.Get "cssFiles" }}
                {{ if ne . "default" }}
                    <link rel="stylesheet" href="{{ . }}" />
                {{ end }}
            {{ end }}
        {{ end }}

        <!--[if lte IE 9]><link rel="stylesheet" href="/css/ie9.css" /><![endif]-->
        <!--[if lte IE 8]><link rel="stylesheet" href="/css/ie8.css" /><![endif]-->
        {{ if not (in (printf "%#v" .Site.BaseURL) "localhost") }}
            {{ template "_internal/google_analytics.html" . }}
        {{ end }}
    </head>
    <body>

        <!-- Wrapper -->
        <div id="wrapper">

```
