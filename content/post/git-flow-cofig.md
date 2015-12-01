+++
categories = ["Development"]
date = "2015-12-01T17:15:17+09:00"
description = ""
draft = false
image = "/img/about-bg.jpg"
tags = ["git", "git-flow"]
title = "git-flowを使えるようにする"

+++

バージョン管理にはGitを使っているが、git-flowというwrapperみたいなのがあるらしいので早速使ってみる。

# とりあえず新規Gitリポジトリを作成

`git init`の代わりに`git flow init`を使えばよくて、
質問はすべて`RET`を押しておけば問題ない。

``` bash
$ cd ~/repos/git-flow-test
$ git flow init

Initialized empty Git repository in /Users/shotakaha/repos/git-flow-test/.git/
No branches exist yet. Base branches must be created now.
Branch name for production releases: [master]
Branch name for "next release" development: [develop]

How to name your supporting branch prefixes?
Feature branches? [feature/]
Release branches? [release/]
Hotfix branches? [hotfix/]
Support branches? [support/]
Version tag prefix? []
```

このときGitリポジトリの設定ファイル（=`.git/config`）がどうなってるのかを確認してみる。

``` bash
$ less .git/config

[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[gitflow "branch"]
    master = master
    develop = develop
[gitflow "prefix"]
    feature = feature/
    release = release/
    hotfix = hotfix/
    support = support/
    versiontag =
```

新しく`[gitflow]`というセクションが追加されているのが分かる。
`versiontag`のprefix部分は空欄にしてしまったが、後で`versiontag = v`などに変更してもよい。


# 既存のGitリポジトリに適用

さて`git flow`の初期化方法が分かったので、既存のGitリポジトリに適用してみる。
以下は僕の`.emacs.d`のリポジトリの設定

``` bash
$ less ~/.emacs.d/.git/config

[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    url = https://github.com/shotakaha/prelude.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[remote "upstream"]
    url = https://github.com/bbatsov/prelude.git
    fetch = +refs/heads/*:refs/remotes/upstream/*
[branch "trunk"]
    remote = origin
    merge = refs/heads/trunk

```

これに`[gitflow]`セクションを追記する。
`git-flow`では開発用ブランチのデフォルト値が`develop`だが、
僕の場合、それに相当するのが`trunk`なので`develop = trunk`にしている。


``` bash
...（省略）...
[branch "trunk"]
    remote = origin
    merge = refs/heads/trunk
[gitflow "branch"]
    master = master
    develop = trunk
[gitflow "prefix"]
    feature = feature/
    release = release/
    hotfix = hotfix/
    support = support/
    versiontag = v

```

これで既存のリポジトリでも`git-flow`が使えるようになった。
とても簡単。


# magit-gitflowを使う

さてさてEmacs + Gitには欠かせない`Magit`パッケージ。
実は`magit-gitflow`という`git-flow`用の拡張もある。

`MELPA`からインストールして、GitHubページにあるとおりに設定をしておき、
上記のようにリポジトリの設定もできていれば、すぐに使うことができる。

`magit-status`の画面で`C-f`するだけで`magit-gitflow`ポップアップが表示される。
あとは普段の`Magit`のようにキーを入力するだけ。

これで`git-flow`のコマンドを知らなくてもなんとなく操作できるようになった。
あとは`git-flow`のコンセプトを理解すればよい。
