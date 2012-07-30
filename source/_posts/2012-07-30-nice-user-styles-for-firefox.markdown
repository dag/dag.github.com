---
layout: post
title: "Nice User Styles for Firefox"
date: 2012-07-30 23:30
comments: true
categories: Firefox
---

Two things annoy me when browsing the web:

* The outline given to focused elements is a useful hint from an
  accessibility perspective, such as for keyboard navigation, but in
  Firefox it's even displayed when you click a link with the mouse.
* Textareas with a proportional font.  I often input code, for example when
  commenting on reddit or on GitHub issues.  A fixed-width font is much
  better for these situations.

So I decided to do something about it.

<!-- more -->

    $ cd ~/.mozilla/firefox/*.default
    $ mkdir chrome
    $ vim chrome/user/userContent.css

{% codeblock lang:css %}
a:hover, a:active { outline: none; }
textarea { font-family: monospace !important; }
{% endcodeblock %}
