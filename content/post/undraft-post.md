+++
date = "2015-11-29T05:01:35+09:00"
draft = false
title = "Hugoで記事を公開する手順"
categories = [ "hugo" ]
+++

``` bash
$ hugo undraft content/post/undraft-post.md
```

新規作成した記事はデフォルトでドラフト状態（ `draft = true` ）になっているので、
`-D (--buildDrafts)` フラグをつけてビルドしないと表示されない。

公開設定にするには `hugo undraft` コマンドを使う。
これでドラフト状態でなくなる（ `draft = false` ）と同時に、
日付（ `date` ）も更新される。

使い方が分からなくなったら `hugo help undraft` で確かめればよい
