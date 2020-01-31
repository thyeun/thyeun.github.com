---
layout: entry
title: Zsh Vi Mode
author: Thomas Yeun
author-email: thyeun@gmail.com
description: Zsh Vi Mode 
publish: true
---


## The Omnipresence Of Vim

Vim is the best editor you've ever used.

Vim emulation seems to be everywhere: Eclipse has Vrapper, Sublime has Vintage, Emacs has Evil. Vim bindings are so ubiquitous, you can even find them in desktop applications such as Chrome and web apps like Gmail. This is great. You are happy.

But do you vi while you zsh?

## Zsh Line Editing

When you type characters at your zsh prompt you're engaging the zsh line editing module, often abbreviated zle. The zle module lets you do fancy things like delete the entire line you're working on and move by words instead of individual characters. The zle module operates in two modes:

<pre><code>
{
   # Emacs mode
   bindkey -e

   # Vi mode
   bindkey -v
}</code></pre>