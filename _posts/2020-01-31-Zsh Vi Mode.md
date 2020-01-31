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

When you type characters at your zsh prompt you're engaging the zsh line editing module, often abbreviated `zle`. The `zle` module lets you do fancy things like delete the entire line you're working on and move by words instead of individual characters. The `zle` module operates in two modes:

<pre><code>
# Emacs mode
bindkey -e

# Vi mode
bindkey -v
</code></pre>

Emacs mode is the default. Gross. Let's change it to Vi.

## Vi Mode

Engaging Vi mode is easy. As previously mentioned, all you need is this line:

<pre><code>
bindkey -v
</code></pre>

This allows you to press `<ESC>` to switch to `NORMAL` mode. Predictably, this lets you move around the line in standard Vim fashion. You can then use any of the standard vim insert keystrokes to move back to insert mode.

The default setup will you get pretty far, but if you use it frequently you will quickly realize it has a few shortcomings. First,there is noticeable lag when moving between modes. Second, there is no visual indication of which mode you're currently in. We will address these shortcomings in the next two sections.

## Kill The Lag

By default, there is a 0.4 second delay after you hit the `<ESC>` key and when the mode change is registered. This results in a very jarring and frustrating transition between modes. Let's reduce this delay to 0.1 seconds.

<pre><code>
export KEYTIMEOUT=1
</code></pre>
