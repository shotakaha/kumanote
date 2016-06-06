+++
date = "2015-11-28T02:38:13+09:00"
draft = false
title = "Hugoを使い始めてみた感想"
categories = [ "hugo" ]
+++
静的ウェブサイトジェネレータ [Hugo](https://gohugo.io)を使ってみることにした。

実はHugoのことは３ヶ月くらい前に一度調べたことがあって、全く記憶にないのだけれど、その時に `hugo` コマンドはインストールしていたみたい。

（たぶん、`Go`をMacPortsでインストールし、[Homebrew](http://brew.sh)をインストールしてからの、`Hugo`のインストールをしたのだと思われる）

# Hugo Quickstart Guid

とりあえず、[Quickstart](http://gohugo.io/overview/quickstart/) にしたがって入力。
あっさりと、それっぽい感じのウェブページが作成できてしまった。
しかも、スタイルなど余計なことを考えず、コンテンツとなる文書をひたすら書けばいいだけなのでこれはなかなか楽しい。

# Markdown or ReST

コンテンツは`Markdown`で書くことになっている。
しかし、[Front Matterのドキュメント](https://gohugo.io/content/front-matter/) を読むと `Hugo v0.14` から `reStructuredText` もexperimentalにサポートしているらしい。

`Sphinx`ドキュメントの作成で`ReST`を覚えたので、使えたら楽ちんなのだけど、別途`rst2html`が必要。
郷に入っては郷に従うことにしよう。

とりあえず毎日１本ずつ使ってみた感想や内容を書いていくのが当面の目標。
