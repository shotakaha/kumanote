+++
date = "2015-11-30T22:44:13+09:00"
draft = false
title = "Hugoのテーマを使ってみる"
categories = [ "hugo" ]
+++

GitHubに[hugoThemes](https://github.com/spf13/hugoThemes) がある。
各テーマの見た目は[デモ](http://themes.gohugo.io)を参考にするとよい（かも）。
インストールはとりあえず [Installing Themes](https://gohugo.io/themes/installing/) の通りにやればOK。

ただし、すべてのプロジェクトで全テーマをチェックアウトするのはアホらしいので、
大元を１つ用意し、そこへのシンボリックリンクを張ることにする。
このときのリンク名は `/themes` にしないといけない。

テーマは`--theme`オプションでテーマを指定することができる。
テーマ名は `/themes/` 内にあるディレクトリ名（`THEMENAME/`）を指定しないとエラーになる。

``` bash
## 大元を用意する
cd ~/repos/github/
$ git clone --recursive https://github.com/spf13/hugoThemes.git

## プロジェクト内にシンボリックリンクを張る
$ cd ~/public_html/kumanote/
$ ln -s ~/repos/github/hugoThemes themes

## テーマの適用
$ hugo server --watch --buidDrafts --theme=hyde
```

テーマの指定は`config.toml`に書くこともできる。
これで毎回`--theme`オプションを指定しなくてもよくなる。
各テーマのGitHubページに設定方法が書いてあるのでよく読む。

今回は、とりあえず [startbootstrap-clean-blog](http://themes.gohugo.io/startbootstrap-clean-blog/ ) を使ってみることにする。
