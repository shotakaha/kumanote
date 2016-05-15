+++
author = "Kuma"
categories = ["hugo future imperfect"]
date = "2016-05-12T10:11:28+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "Hugo Future Imperfect の設定"

+++
テーマのディレクトリにある``exampleSite``にある``config.toml``を読んで、必要な箇所をコピーしてくる。
（既に自分の``config.toml``があるのでこうしたけど、新規作成するなら丸々コピーでOK）

<!--more-->

# いろいろな設定

設定する項目ごとに、（主に``[params]``を）プチプチ分けて書いてみた。
実際の``config.toml``ではひと纏まりにしておく。


* メタデータなど

``description``はHTMLのメタデータ、
``navbarTitle``は画面上部のメニューバーの左端のタイトルのこと。

``` toml
[params]
# Sets the meta tag description, usually reserved for the main page
description = "A Note Of Kuma, For Kuma, By Kuma"
# This will appear on the top left of the navigation bar
navbarTitle = "KumaNOTE"
...
```

* ソーシャルのアイコン

各種SNSのアイコンを、サイドバーに配置するかの設定。
とりあえず、デフォルトのまま上下に配置。

アカウント名は、下に書いた``[social]``で設定する

``` toml
[params]
...
# Social media buttons that appear on the sidebar
socialAppearAtTop    = true
socialAppearAtBottom = true
...
```


* 記事のあるディレクトリ

記事は``$baseurl/post/``に置いているのだが、``/post/``にするとうまくいかない。

``` toml
[params]
...
# set this to the section name if section is not post
viewMorePostLink     = "post/"
...
```

* その他

``` toml
[params]
...
# Optional Params
categoriesByCount    = true
includeReadingTime   = true

# The set of favicons used are based on the write-up from this link:
# https://github.com/audreyr/favicon-cheat-sheet
# Please see the favicon partial template for more information
loadFavicon          = false
faviconVersion       = ""

# Load custom CSS or JavaScript files. This replaces the deprecated params
# minifiedFilesCSS and minifiedFilesJS. The variable is an array so that you
# can load multiple files if necessary. You can also load the standard theme
# files by adding the value, "default".
# customCSS            = ["default", "/path/to/file"]
# customJS             = ["default", "/path/to/file"]

# Loading min files for exampleSite
# customCSS            = ["/css/main.min.css"]
# customJS             = ["/js/main.min.js"]
```


# サイドバーの設定

* サイドバーのテキスト情報

``` toml
[params.intro]
header    = "KumaNOTE"
paragraph = "A Note of Kuma, for Kuma, by Kuma"
about     = "Welcome to KumaNOTE"
```

* サイドバーに使う画像アイコンの設定

``` toml
# This will also appear on the sidebar.
# A width of less than 100px is recommended
# This is optional
[params.intro.pic]
src       = "/logo/bear.png"
# modify your picture in the shape of a circle or
# future imperfect's hexagonal shape
circle    = false
imperfect = true
width     = ""
alt       = "KumaNOTE"
```

* 「最近の投稿」に表示する数

``` toml
# Adjust the amount of recent posts on the sidebar.
# This is optional. The default value 5 will be used
[params.postAmount]
sidebar = 2
```



# メニューバーの設定

なんて呼ぶか分からないけれど、画面上部のナビゲーションバーを追加するセクション。``menu``はHugo内の特別な変数。

* ``[[menu.main]]``

# ソーシャルの設定

自分のGitHubやFacebookのアカウントへのリンクのアイコンを設定できる。

まず、``[params]``の部分で``socialAppearAtTop``と``socialAppearAtBottom``を``true``にしておく必要がある。
そして``[social]``の部分に、各サービスに自分のアカウント名を書いておく。


``` toml
[params]
# Social media buttons that appear on the sidebar
socialAppearAtTop    = true
socialAppearAtBottom = true

[social]
github          = "shotakaha"
bitbucket       = "shotakaha"
jsfiddle        = ""
codepen         = ""
foursquare      = ""
dribbble        = ""
deviantart      = ""
behance         = ""
flickr          = ""
instagram       = ""
youtube         = "shotakaha"
...
```
