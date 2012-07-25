---
layout: post
title: "GHC 7.4 on Fedora 17"
date: 2012-07-24 16:28
comments: true
categories: [Fedora, Haskell]
---

Fedora 17 ships the previous release of the Haskell Platform and GHC 7.0.4.
To get the latest platform and GHC 7.4.1 you can install from the "rawhide"
repository.

<!-- more -->

First make sure to install the packages you want from your
normal repositories so as to avoid pulling a lot of dependencies from
rawhide:

    $ sudo yum install haskell-platform

You may substitute `haskell-platform` for `ghc` if you don't want the whole
platform.  Next we install the repository description for rawhide.  It will
be a disabled repository by default so we enable it temporarily and update
the packages we want:

    $ sudo yum install fedora-release-rawhide
    $ sudo yum --enablerepo rawhide update haskell-platform

This "rawhide" repository is what will eventually become Fedora 18.  If you
use the commands above it will be enabled temporarily for the duration of
that "yum install", but your system will be otherwise unaffected.

Should you regret what you have done you can easily revert the
installation:

    $ sudo yum distro-sync

This will synchronize all your installed packages to the versions available
in your *enabled* repositories.  If this fails you might try removing all
the haskell packages first:

    $ sudo yum remove haskell-platform 'ghc-*'

*Updated in accordance with recommendations from juhp; see comments below.
Also updated with improved recovery method.*
