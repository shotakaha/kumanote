+++
categories = ["Development"]
date = "2015-12-01T20:44:17+09:00"
description = ""
draft = true
image = "/img/about-bg.jpg"
tags = ["hugo"]
title = "Hugoドキュメントの全体設定"

+++

Hugoの全体設定は`config.toml`に書けばよい。
現在の設定は`hugo config`で確認できる。
詳細は [Configuration](http://gohugo.io/overview/configuration/ )を読むこと。

``` bash
$ hugo config
```


# 自分で設定した変数

`config.toml`を以下のように設定した場合、

``` toml
baseurl = "http://localhost:8888/~shotakaha/kumanote/public/"
languageCode = "ja"
title = "KumaNOTE"
theme = "startbootstrap-clean-blog"

[author]
  name = "Shota Takahashi"

[permalinks]
  #post = "/blog/:year/:month/:day/"
  #post = "/blog/:filename"
```

こんな感じの設定が返ってくる。

``` conf
baseurl = "http://localhost:8888/~shotakaha/kumanote/public/"
languagecode = "ja"
title = "KumaNOTE"
theme = "startbootstrap-clean-blog"

author = map[name:Shota Takahashi]

permalinks = map[]
```


# デフォルトで設定されてる変数

ディレクトリの設定はこんな感じ。

``` conf
archetypedir = "archetypes"
cachedir = "/var/folders/8q/6cpss2w528b78bff279ggc_w0000gn/T/hugo_cache/"
contentdir = "content"
datadir = "data"
defaultextension = "html"
defaultlayout = "post"
layoutdir = "layouts"
publishdir = "public"
staticdir = "static"
workingdir = "/Users/shotakaha/public_html/kumanote"
```

他の値が詰まってるのはこんな感じ。

``` conf
metadataformat = "toml"
paginate = 10
paginatepath = "page"
rssuri = "index.xml"
sitemap = {ChangeFreq: Priority:-1}
taxonomies = map[tag:tags category:categories]
```

値がないのはこんな感じ。

``` conf
footnoteanchorprefix = ""
footnotereturnlinkcontents = ""
newcontenteditor = ""
sectionpagesmenu = ""
```

# フラグ

``` conf
builddrafts = false
buildfuture = false
canonifyurls = false
disablelivereload = false
disablepathtolower = false
disablerss = false
disablesitemap = false
hascjklanguage = false
ignorecache = false
uglyurls = false
verbose = false
watch = false
pluralizelisttitles = true
preservetaxonomynames = false
relativeurls = false
removepathaccents = false
```








# Pygment


``` conf
pygmentscodefences = false
pygmentsoptions = ""
pygmentsstyle = "monokai"
pygmentsuseclasses = false
```

# BlackFriday

- [BlackFriday - GitHub](https://github.com/russross/blackfriday )


``` conf
blackfriday = &{Smartypants:true
                AngledQuotes:false
                Fractions:true
                HrefTargetBlank:false
                SmartDashes:true
                LatexDashes:true
                PlainIDAnchors:false
                Extensions:[] ExtensionsMask:[]}
```


# テンプレートで使える変数

`params`はこんな感じ。
この変数は`.Site.Params.XXX`の形でテンプレートで使うことができる。

``` toml
[params]
  DateForm = "Mon, Jan 2, 2006"
  Description = "A Note of Kuma, for Kuma, by Kuma"
  Author = "Shota Takahashi"
  email = "shotakaha@gmail.com"

[[params.social]]
  title = "twitter"
  url = "https://twitter.com/shotakaha"
[[params.social]]
  title = "github"
  url = "https://github.com/shotakaha"
[[params.social]]
  title = "facebook"
  url = "https://www.facebook.com/shotakaha"
```

``` conf
params = map[social:[map[title:twitter url:https://twitter.com/shotakaha]
                     map[url:https://github.com/shotakaha title:github]
                     map[title:facebook url:https://www.facebook.com/shotakaha]]
             DateForm:Mon, Jan 2, 2006
             Description:A Note of Kuma, for Kuma, by Kuma
             Author:Shota Takahashi
             email:shotakaha@gmail.com]
```

`menu`はこんな感じ。`Hoge`はおまけ。

``` toml
[[menu.main]]
  name = "home"
  url = "/"
  weight = -200
[[menu.main]]
  name = "Archives"
  url = "/post/"
  weight = -180
[[menu.main]]
  name = "Hoge"
  url = "/hoge/"
  weight = -180
```

``` conf
menu = map[main:[map[name:home url:/ weight:-200]
                 map[url:/post/ weight:-180 name:Archives]
                 map[weight:-180 name:Hoge url:/hoge/]]]
```

リスト内の順番がぐちゃぐちゃなのはなんでだろう？


# ignoreFiles

`hugo server --watch`などしていると、Emacsで編集中に中間ファイル（？ #から始まるファイルのこと）の生成によってエラーがでてしまう。
ウェブサイトのビルドに関係ないんだけど、気になるなぁと思っていたら、
[issued #1189 - Hugo](https://github.com/spf13/hugo/issues/1189 )にて解決済みだった。

``` toml
ignoreFiles = [".#"]
```
