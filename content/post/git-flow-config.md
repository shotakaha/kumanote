+++
categories = ["git", "git-flow"]
date = "2015-12-01T17:15:17+09:00"
description = ""
image = "/img/about-bg.jpg"
title = "git-flowを使ってみる"

+++

Gitでバージョン管理をする際に、頻繁に使う操作をまとめた
`git-flow`というコマンドがあるらしいので、早速使ってみる。


# 新規Gitリポジトリの作成

`git init`の代わりに`git flow init`を使えばよい。
マスターブランチ、開発ブランチの名前はどうする？
トピックプランチのプリフィックスはどうする？
とか聞かれるが、`RET`を押しておいて問題ない。

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

新しく`[gitflow "branch"]`と`[gitflow "prefix"]`というセクションが追加されているのが分かる。
`versiontag`の部分は空欄になっているが、後で`versiontag = v`などに書き換えてもよい。


# 既存のGitリポジトリをgit-flow化する

さて`git flow init`で`/.git/config`がどう書き換えられるか分かったので、既存のGitリポジトリにも適用してみる。
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
