+++
date = "2015-11-28T01:31:07+09:00"
draft = true
title = "Hugoのテーマを使ってみる"
categories = [ "hugo" ]
+++

GitHubに[hugoThemes](https://github.com/spf13/hugoThemes) がある。
各テーマの見た目は[デモ](http://themes.gohugo.io)を参考にするとよい（かも）。
インストールはとりあえず [Installing Themes](https://gohugo.io/themes/installing/) の通りにやればOK。

ただし、すべてのプロジェクトで全テーマをチェックアウトするのはアホらしいので、
大元を１つ用意し、そこへのシンボリックリンクを張ることにする。
このときのリンク名は `/themes` にしないといけない。

テーマを適用する時には `/themes` 内にあるディレクトリ名を指定しないとエラーになる。

``` bash
## 大元を用意する
$ cd ~/repos/github/
$ git clone --recursive https://github.com/spf13/hugoThemes.git

## プロジェクト内にシンボリックリンクを張る
$ cd ~/public_html/kumanote/
$ ln -s ~/repos/github/hugoThemes themes

## テーマの適用
$ hugo server --watch --buidDrafts --theme=hyde
```
