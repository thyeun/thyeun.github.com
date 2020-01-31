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
+ [Spaces And Tabs](http://thyeun.github.io/2020/01/29/A-Good-Vimrc.html#spaces&tabs)
+ [UI Config](http://thyeun.github.io/2020/01/29/A-Good-Vimrc.html#uiconfig)
+ [Searching](http://thyeun.github.io/2020/01/29/A-Good-Vimrc.html#searching)
+ [Folding](http://thyeun.github.io/2020/01/29/A-Good-Vimrc.html#folding)
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

This article will almost certainly fall out of date with my vimrc in the very near future. You can find the most up to date version of it on [github](https://github.com/thyeun/dotfiles/blob/master/.vimrc).

## Colors

<pre><code>colorscheme badwolf         " awesome colorscheme
</code></pre>

Colors! Colorschemes are subjective, but I've currently settled on [badwolf by Steve Losh](https://github.com/sjl/badwolf/). I found [solarized](https://github.com/altercation/Vim-colors-solarized.git) incredibly complete, but a little too bland for my taste. I enjoy colors that pop. I also spend a good deal of time with [molokai](https://github.com/tomasr/molokai.git) and still think it's a great scheme, but simply prefer badwolf at the moment.

Moving on:

<pre><code>syntax enable           " enable syntax processing
</code></pre>

The comment should be enough to describe this one. I'll take this moment to plug adding comments to most if not every line in your vimrc. If you're anything like me that file is going to get pretty long, and chances are you won't remember what every line does forever, so adding comments will help Future You know what the hell is going on in there.

Also, many settings in Vim have both a long name and a short name. For instance `background` is the same as bg. For future readability, I strongly recommend using the long name.

## Spaces & Tabs

The incantations you must throw into your vimrc to get tabs/spaces working the way you want can be pretty confusing, so here's a quick refresher.

<pre><code>set tabstop=4       " number of visual spaces per TAB
</code></pre>

`tabstop` is the number of spaces a tab counts for. So, when Vim opens a file and reads a `<TAB>` character, it uses that many spaces to visually show the `<TAB>`.

<pre><code>set softtabstop=4   " number of spaces in tab when editing
</code></pre>

`softabstop` is the number of spaces a tab counts for when *editing*. So this value is the number of spaces that is *inserted* when you hit `<TAB>` and also the number of spaces that are *removed* when you backspace.

<pre><code>set expandtab       " tabs are spaces
</code></pre>

`expandtab` turns `<TAB>`s into spaces. That's it. So `<TAB>` just becomes a shortcut for "insert four spaces".

Taken together, these are great options for editing files in languages that prefer spaces over tabs, since this ensures no `<TAB>`s are actually used. I spend most of my day in python and bash, where spaces are the norm. I like it, since it means my source code looks the same on every machine.

## UI Config

These are options that change random visuals in Vim.

<pre><code>set number              " show line numbers
</code></pre>

Showing line numbers should need no justification.

<pre><code>set showcmd             " show command in bottom bar
</code></pre>

`showcmd` shows the last command entered in the very bottom right of Vim. I have it set here but it's actually not shown in my Vim since I use [powerline](https://github.com/Lokaltog/powerline) plugin (which we will get to later).

<pre><code>set cursorline          " highlight current line
</code></pre>

`cursorline` draws a horizontal highlight (or underline, depending on your colorscheme) on the line your cursor is currently on. I've found that this makes it easier to follow exactly what line you left off on when you're switching back to a Vim session or switching between windows in Vim.

<pre><code>filetype indent on      " load filetype-specific indent files
</code></pre>

This both turns on filetype detection and allows loading of language specific indentation files based on that detection. For me, this means the python indentation file that lives at `~/.vim/indent/python.vim` gets loaded every time I open a `*.py` file.

<pre><code>set wildmenu            " visual autocomplete for command menu
</code></pre>

This is a pretty cool feature I didn't know Vim had. You know how Vim automatically autocompletes things like filenames when you, for instance, run :e `~/.vim<TAB>`? Well it will provide a graphical menu of all the matches you can cycle through if you turn on `wildmenu`.

<pre><code>set lazyredraw          " redraw only when we need to.
</code></pre>

Vim loves to redraw the screen during things it probably doesn't need to—like in the middle of macros. This tells Vim not to bother redrawing during these scenarios, leading to faster macros.

<pre><code>set showmatch           " highlight matching [{()}]
</code></pre>

With `showmatch`, when your cursor moves over a parenthesis-like character, the matching one will be highlighted as well.

## Searching

I love Vim's search. I love it even more with the following settings.

<pre><code>set incsearch           " search as characters are entered
set hlsearch            " highlight matches
</code></pre>

These should be pretty self explanatory. They make searching better.

<pre><code>" turn off search highlight
nnoremap < leader >< space > :nohlsearch< CR >
</code></pre>

Vim will keep highlighted matches from searches until you either run a new one or manually stop highlighting the old search with `:nohlsearch`. I find myself running this all the time so I've mapped it to `,<space>`.

## Folding

Vim folding is a pretty sweet feature that I don't make heavy use of, but when I want it, I want it to have reasonable settings.

<pre><code>set foldenable          " enable folding
</code></pre>

Shows all folds.

<pre><code>set foldlevelstart=10   " open most folds by default
</code></pre>

