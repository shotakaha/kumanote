+++
date = "2015-11-28T02:47:43+09:00"
draft = true
title = "記事を公開する"
categories = [ "hugo" ]
+++

``` bash
$ hugo undraft content/post/undraft-post.md
```

新規作成した記事はデフォルトでドラフト状態（ `draft = true` ）になっているので、
`-D (--buildDrafts)` フラグをつけてビルドしないと表示されない。

公開するには `hugo undraft` コマンドを使う。
これでドラフト状態でなくなる（ `draft = false` ）と同時に、
日付（ `date` ）も更新される。

使い方が分からなくなったら `hugo help undraft` で確かめればよい
