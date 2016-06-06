+++
author = "Shota"
categories = ["homebrew"]
date = "2016-06-06T15:27:22+09:00"
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "zを再インストール"

+++
[z - jump around](https://github.com/rupa/z)というディレクトリ移動の補助コマンドを、MacPortsからHomebrewに変えます。

# 現状確認とdeactivate

``` sh
$ port installed z
The following ports are currently installed:
  z @1.8_0 (active)

$ sudo port deactivate z
--->  Deactivating z @1.8_0
--->  Cleaning z
```

# 再インストール

``` sh
$ brew info z
z: stable 1.9, HEAD
Tracks most-used directories to make cd smarter
https://github.com/rupa/z
Not installed
From: https://github.com/Homebrew/homebrew-core/blob/master/Formula/z.rb
==> Caveats
For Bash or Zsh, put something like this in your $HOME/.bashrc or $HOME/.zshrc:
  . `brew --prefix`/etc/profile.d/z.sh

$ brew install z
==> Downloading https://github.com/rupa/z/archive/v1.9.tar.gz
==> Downloading from https://codeload.github.com/rupa/z/tar.gz/v1.9
######################################################################## 100.0%
==> Caveats
For Bash or Zsh, put something like this in your $HOME/.bashrc or $HOME/.zshrc:
  . `brew --prefix`/etc/profile.d/z.sh
==> Summary
🍺  /usr/local/Cellar/z/1.9: 4 files, 19.6K, built in 6 seconds
```

# Caveats

以下の設定を .bashrc/.zshrc に書いておきます。

``` sh
==> Caveats
For Bash or Zsh, put something like this in your $HOME/.bashrc or $HOME/.zshrc:
  . `brew --prefix`/etc/profile.d/z.sh
```

.bashrc/.zshrcを複数のPCで共有しているなら、`if ... fi`で囲んでおくとよいかもです。

``` sh
if [ -f `brew --prefix`/etc/profile.d/z.sh ]; then
    . `brew --prefix`/etc/profile.d/z.sh
fi
```
