---
layout: post
title: "Latest GHC on Fedora 17"
date: 2012-07-24 16:28
comments: true
categories: [Fedora, Haskell]
---

Fedora 17 ships the previous release of the Haskell Platform and GHC 7.0.4.
To get the latest platform and GHC 7.4.1 you can install them from
"rawhide" like this:

{% codeblock lang:console %}
$ sudo yum install fedora-release-rawhide
$ sudo yum --enablerepo rawhide install haskell-platform  # or "ghc"
{% endcodeblock %}

This "rawhide" repository is what will eventually become Fedora 18.  If you
use the commands above it will be enabled temporarily for the duration of
that "yum install", but your system will be otherwise unaffected.

Should you regret what you have done you can easily revert the
installation:

{% codeblock lang:console %}
$ sudo yum distro-sync
{% endcodeblock %}

This will synchronize all your installed packages to the versions available
in your enabled repositories (and "rawhide" is disabled by default).
