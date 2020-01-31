---
layout: entry
title: A Good Vimrc
author: Thomas Yeun
author-email: thyeun@gmail.com
description: Vimrc
publish: true
---


## How To Vimrc

There is just one rule you must follow when crafting your own .vimrc.

<pre><code>Don't put any lines in your vimrc that you don't understand.
</code></pre>

There are tons of tutorials such as this one on the internet that contain all kinds of awesome hacks to make your Vim better, but the absolute worst way to make your environment better is to just copy it wholesale from others.

Spending the time to actually learn what's going into the construction of your editor is invaluable. In the same way that copying notes off a projector by hand often leads to increased information retention, adding features one by one to your vimrc aids in overall Vim comprehension.

With that said, the rest of this article will be me explaining each and every line in my current vimrc in its entirety with the hope that you will find some tricks you haven't seen before. But! My vimrc is far from perfect. I'm always looking for additions that would make my environment better so if you think I missed something important please let me know: [@thyeun](https://twitter.com/thyeun).

I will break it up into logical sections.

+ [Colors](http://thyeun.github.io/2020/01/29/A-Good-Vimrc.html#colors)
+ Spaces And Tabs
+ UI Config
+ Searching
+ Folding
+ Custom Movements
+ Custom Leader
+ CtrlP Settings
+ Launch Config
+ Tmux Config
+ Autogroups
+ Backups
+ Custom Functions
+ Organization
+ Wrapping It Up

This article will almost certainly fall out of date with my vimrc in the very near future. You can find the most up to date version of it on github.

## Colors

<pre><code>colorscheme badwolf         " awesome colorscheme
</code></pre>

Colors! Colorschemes are subjective, but I've currently settled on [badwolf by Steve Losh](https://github.com/sjl/badwolf/). I found [solarized](https://github.com/altercation/Vim-colors-solarized.git) incredibly complete, but a little too bland for my taste. I enjoy colors that pop. I also spend a good deal of time with [molokai](https://github.com/tomasr/molokai.git) and still think it's a great scheme, but simply prefer badwolf at the moment.

Moving on: