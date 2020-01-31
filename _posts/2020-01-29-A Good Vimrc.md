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

+ [Colors](#colors)
+ [Spaces And Tabs](#spaces)
+ [UI Config](#ui)
+ [Searching](#search)
+ [Folding](#fold)
+ [Custom Movements](#move)
+ [Custom Leader](#lead)
+ [CtrlP Settings](#ctrlp)
+ [Launch Config](#launch)
+ [Tmux Config](#tmux)
+ [Autogroups](#auto)
+ [Backups](#backup)
+ [Custom Functions](#func)
+ [Organization](#organ)
+ [Wrapping It Up](#wrap)

This article will almost certainly fall out of date with my vimrc in the very near future. You can find the most up to date version of it on [github](https://github.com/thyeun/dotfiles/blob/master/.vimrc).

## Colors {#colors}

<pre><code>colorscheme badwolf         " awesome colorscheme
</code></pre>

Colors! Colorschemes are subjective, but I've currently settled on [badwolf by Steve Losh](https://github.com/sjl/badwolf/). I found [solarized](https://github.com/altercation/Vim-colors-solarized.git) incredibly complete, but a little too bland for my taste. I enjoy colors that pop. I also spend a good deal of time with [molokai](https://github.com/tomasr/molokai.git) and still think it's a great scheme, but simply prefer badwolf at the moment.

Moving on:

<pre><code>syntax enable           " enable syntax processing
</code></pre>

The comment should be enough to describe this one. I'll take this moment to plug adding comments to most if not every line in your vimrc. If you're anything like me that file is going to get pretty long, and chances are you won't remember what every line does forever, so adding comments will help Future You know what the hell is going on in there.

Also, many settings in Vim have both a long name and a short name. For instance `background` is the same as bg. For future readability, I strongly recommend using the long name.

## Spaces & Tabs {#spaces}

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

## UI Config {#ui}

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

## Searching {#search}

I love Vim's search. I love it even more with the following settings.

<pre><code>set incsearch           " search as characters are entered
set hlsearch            " highlight matches
</code></pre>

These should be pretty self explanatory. They make searching better.

<pre><code>" turn off search highlight
nnoremap < leader >< space > :nohlsearch< CR >
</code></pre>

Vim will keep highlighted matches from searches until you either run a new one or manually stop highlighting the old search with `:nohlsearch`. I find myself running this all the time so I've mapped it to `,<space>`.

## Folding {#fold}

Vim folding is a pretty sweet feature that I don't make heavy use of, but when I want it, I want it to have reasonable settings.

<pre><code>set foldenable          " enable folding
</code></pre>

Shows all folds.

<pre><code>set foldlevelstart=10   " open most folds by default
</code></pre>

`foldlevelstart` is the starting fold level for opening a new buffer. If it is set to 0, all folds will be closed. Setting it to 99 would guarantee folds are always open. So, setting it to 10 here ensures that only very nested blocks of code are folded when opening a buffer.

<pre><code>set foldnestmax=10      " 10 nested fold max
</code></pre>

Folds can be nested. Setting a max on the number of folds guards against too many folds. If you need more than 10 fold levels you must be writing some Javascript burning in callback-hell and I feel very bad for you.

<pre><code>" space open/closes folds
nnoremap < space > za
</code></pre>

I change the mapping of `<space>` pretty frequently, but this is its current command. `za` opens/closes the fold around the current block. As an interesting aside, I've heard the `z` character is used to represent folding in Vim because it looks like a folded piece of paper. Probably not, but it makes a nice story. `:)`

<pre><code>set foldmethod=indent   " fold based on indent level
</code></pre>

This tells Vim to fold based on indentation. This is especially useful for me since I spend my days in Python. Other acceptable values are `marker`, `manual`, `expr`, `syntax`, `diff`. Run `:help foldmethod` to find out what each of those do.

## Movement {#move}

Here we start getting into custom bindings. This group of bindings all relate to movement commands.

<pre><code>" move vertically by visual line
nnoremap j gj
nnoremap k gk
</code></pre>

These two allow us to move around lines visually. So if there's a very long line that gets visually wrapped to two lines, `j` won't skip over the "fake" part of the visual line in favor of the next "real" line.

<pre><code>" move to beginning/end of line
nnoremap B ^
nnoremap E $

" $/^ doesn't do anything
nnoremap $ < nop >
nnoremap ^ < nop >
</code></pre>

These feel like my most controversial bindings, since they overwrite existing movement bindings. My thinking was that hitting `^` and `$` to jump to the beginning and end of a line was a little too uncomfortable for such an oft-used movement. So I rebound E and B, which are typically used to move forwards and backwards over visual words to these purposes. Next I bound the old way to `<nop>` to train myself to use the new ones.

<pre><code>" highlight last inserted text
nnoremap gV `[v`]
</code></pre>

This one is pretty cool. It visually selects the block of characters you added last time you were in `INSERT` mode.

## Leader Shortcuts {#lead}

Here we've reached the meat of my custom keybindings. This section will introduce many different plugins and custom functions that I use pretty frequently. Let's get started.

<pre><code>let mapleader=","       " leader is comma
</code></pre>

`\` is a little far away for a leader. I've found `,` to be a much better replacement.

<pre><code>" jk is escape
inoremap jk < esc >
</code></pre>

`<ESC>` is very far away. `jk` is a much better replacement as it's on the home row and I actually never type it when writing text. Except right now when I wrote this section of this post. Which I'm writing in Vim. The workaround if you ever need to enter this rare sequence of keys is to enter the `j`, wait for the leader-check timeout to fade, and then enter the `k`.

<pre><code>" toggle gundo
nnoremap < leader >u :GundoToggle< CR >
</code></pre>

In one of its cleverest innovations, Vim doesn't model undo as a simple stack. In Vim it's a tree. This makes sure you never lose an action in Vim, but also makes it much more difficult to traverse around that tree. [gundo.vim](https://github.com/sjl/gundo.vim) fixes this by displaying that undo tree in graphical form. Get it and don't look back. Here I've mapped it to `,u`, which I like to think of as "super undo".

<pre><code>" edit vimrc/zshrc and load vimrc bindings
nnoremap < leader >ev :vsp $MYVIMRC< CR >
nnoremap < leader >ez :vsp ~/.zshrc< CR >
nnoremap < leader >sv :source $MYVIMRC< CR >
</code></pre>

These are shortcuts to edit and source my vimrc and my zshrc. That's it.

<pre><code>" save session
nnoremap < leader >s :mksession< CR >
</code></pre>

Ever wanted to save a given assortment of windows so that they're there next time you open up Vim? `:mksession` does just that! After saving a Vim session, you can reopen it with `vim -S`. Here I've mapped it to `,s`, which I remember by thinking of it as "super save".

<pre><code>" open ag.vim
nnoremap < leader >a :Ag
</code></pre>

[The Silver Searcher](https://github.com/ggreer/the_silver_searcher) is a fantastic command line tool to search source code in a project. It's wicked fast. The command line tool is named `ag` (like the element silver). Thankfully there is a wonderful Vim plugin [ag.vim](https://github.com/rking/ag.vim) which lets you use `ag` without leaving Vim and pulls the results into a quickfix window for easily jumping to the matches. Here I've mapped it to `,a`.

## CtrlP {#ctrlp}

[ctrlp.vim](https://github.com/kien/ctrlp.vim) is my life in Vim. If you've never used a fuzzy file searcher this will open your eyes. If you're currently using [commandt.vim](https://github.com/wincent/Command-T), you're on the right track, but CtrlP is the spiritual successor. It's *can be* (see below) significantly faster and more configurable than CommandT (Thanks [Reddit!](https://www.reddit.com/r/vim/comments/1vt4dg/a_good_vimrc/)). Anyways here are my settings for CtrlP.

<pre><code>" CtrlP settings
let g:ctrlp_match_window = 'bottom,order:ttb'
let g:ctrlp_switch_buffer = 0
let g:ctrlp_working_path_mode = 0
let g:ctrlp_user_command = 'ag %s -l --nocolor --hidden -g ""'
</code></pre>

There are a few things happening here. The first is I'm telling CtrlP to order matching files top to bottom with `ttb`. Next, we tell CtrlP to always open files in new buffers with `let ctrlp_switch_buffer=0`. Setting `let g:ctrlp_working_path=0` lets us change the working directory during a Vim session and make CtrlP respect that change.

Now, let's talk about speed. CtrlP is entirely written in Vimscript, (which is pretty impressive) but CommandT has parts that are written in C. This means CommandT is, by default, faster than CtrlP. However, we can tell CtrlP to run an external command to find matching files. Now that we have `ag` installed, we can use it with CtrlP to make CtrlP wicked fast.. We do that with the following.

<pre><code>let g:ctrlp_user_command = 'ag %s -l --nocolor -g ""'
</code></pre>

If everything works out, you should see a noticeable improvement in the CtrlP speed. There are two caveats to this. Both `g:ctrlp_show_hidden` and `g:ctrlp_custom_ignore` do not work with custom user commands. I only care about the lack of support for custom ignores. Thankfully, `ag` has it's own convention for ignore files: a `.agignore` file that follows the same conventions as `.gitignore`. This is actually great! We only need to define our directories to ignore when searching in one place.

## Launch Config {#launch}

These are options set at launch to configure external tools exactly once.

<pre><code>call pathogen#infect()                      " use pathogen
call pathogen#runtime_append_all_bundles()  " use pathogen
</code></pre>

The `pathogen` options extract all of the Vim plugins from their location in `~/.vim/bundles` to their respective places in the `~/.vim` folder.

## Tmux {#tmux}

<pre><code>" allows cursor change in tmux mode
if exists('$TMUX')
    let &t_SI = "\< Esc >Ptmux;\< Esc >\< Esc >]50;CursorShape=1\x7\< Esc >\\"
    let &t_EI = "\< Esc >Ptmux;\< Esc >\< Esc >]50;CursorShape=0\x7\< Esc >\\"
else
    let &t_SI = "\< Esc >]50;CursorShape=1\x7"
    let &t_EI = "\< Esc >]50;CursorShape=0\x7"
endif
</code></pre>

These lines change the cursor from block cursor mode to vertical bar cursor mode when using tmux. Without these lines, tmux always uses block cursor mode.

## Autogroups {#auto}

<pre><code>augroup configgroup
    autocmd!
    autocmd VimEnter * highlight clear SignColumn
    autocmd BufWritePre *.php,*.py,*.js,*.txt,*.hs,*.java,*.md
                \:call < SID >StripTrailingWhitespaces()
    autocmd FileType java setlocal noexpandtab
    autocmd FileType java setlocal list
    autocmd FileType java setlocal listchars=tab:+\ ,eol:-
    autocmd FileType java setlocal formatprg=par\ -w80\ -T4
    autocmd FileType php setlocal expandtab
    autocmd FileType php setlocal list
    autocmd FileType php setlocal listchars=tab:+\ ,eol:-
    autocmd FileType php setlocal formatprg=par\ -w80\ -T4
    autocmd FileType ruby setlocal tabstop=2
    autocmd FileType ruby setlocal shiftwidth=2
    autocmd FileType ruby setlocal softtabstop=2
    autocmd FileType ruby setlocal commentstring=#\ %s
    autocmd FileType python setlocal commentstring=#\ %s
    autocmd BufEnter *.cls setlocal filetype=java
    autocmd BufEnter *.zsh-theme setlocal filetype=zsh
    autocmd BufEnter Makefile setlocal noexpandtab
    autocmd BufEnter *.sh setlocal tabstop=2
    autocmd BufEnter *.sh setlocal shiftwidth=2
    autocmd BufEnter *.sh setlocal softtabstop=2
augroup END
</code></pre>

This is a slew of commands that create language-specific settings for certain filetypes/file extensions. It is important to note they are wrapped in an `augroup` as this ensures the `autocmd`'s are only applied once. In addition, the `autocmd!` directive clears all the `autocmd`'s for the current group.

## Backups {#backup}

If you leave a Vim process open in which you've changed file, Vim creates a "backup" file. Then, when you open the file from a different Vim session, Vim knows to complain at you for trying to edit a file that is already being edited. The "backup" file is created by appending a ~ to the end of the file in the current directory. This can get quite annoying when browsing around a directory, so I applied the following settings to move backups to the /tmp folder.

<pre><code>set backup
set backupdir=~/.vim-tmp,~/.tmp,~/tmp,/var/tmp,/tmp
set backupskip=/tmp/*,/private/tmp/*
set directory=~/.vim-tmp,~/.tmp,~/tmp,/var/tmp,/tmp
set writebackup
</code></pre>

`backup` and `writebackup` enable backup support. As annoying as this can be, it is much better than losing tons of work in an edited-but-not-written file.

## Custom Functions {#func}

I've written a small number of custom functions. Here they are with comments explaining their purpose.

<pre><code>" toggle between number and relativenumber
function! ToggleNumber()
    if(&relativenumber == 1)
        set norelativenumber
        set number
    else
        set relativenumber
    endif
endfunc

" strips trailing whitespace at the end of files. this
" is called on buffer write in the autogroup above.
function! < SID >StripTrailingWhitespaces()
    " save last search & cursor position
    let _s=@/
    let l = line(".")
    let c = col(".")
    %s/\s\+$//e
    let @/=_s
    call cursor(l, c)
endfunction
</code></pre>

## Organization {#organ}

Once your vimrc starts to fill up, organization becomes an issue. I've grouped this article by logical sections. Not surprisingly,it makes sense to group my actual vimrc by the exact same logical sections. Even cooler, Vim will let us fold all of those sections up by default. So when you open your Vimrc you have a high level view like this:

<pre><code>" Doug Black
+--  5 lines: " Colors -------------------------------------
+--  5 lines: " Misc ---------------------------------------
+--  9 lines: " Spaces & Tabs ------------------------------
+--  8 lines: " UI Layout ----------------------------------
+--  5 lines: " Searching ----------------------------------
+--  8 lines: " Folding ------------------------------------
+--  9 lines: " Line Shortcuts -----------------------------
+-- 21 lines: " Leader Shortcuts ---------------------------
+--  7 lines: " Powerline ----------------------------------
+--  6 lines: " CtrlP --------------------------------------
+--  3 lines: " NERDTree -----------------------------------
+--  4 lines: " Syntastic ----------------------------------
+--  6 lines: " Launch Config ------------------------------
+--  9 lines: " Tmux ---------------------------------------
+--  4 lines: " MacVim -------------------------------------
+-- 25 lines: " AutoGroups ---------------------------------
+--  7 lines: " Backups ------------------------------------
+-- 50 lines: " Custom Functions ---------------------------
</code></pre>

Here's how we make that happen. First, we tell vim to fold sections by *markers*, rather than *indentation*. That looks like this

<pre><code>foldmethod=marker
</code></pre>

Then we want it to close every fold by default so that we have this high level view when we open our vimrc.

<pre><code>foldlevel=0
</code></pre>

Now, this is a file-specific setting, so we can use a `modeline` to make Vim only use these settings for *this* file. Modelines are special comments somewhere in a file that can can declare certain Vim settings to be used only for that file. So we'll tell Vim to check just the final line of the file for a modeline.

<pre><code>set modelines=1
</code></pre>

Next, we'll add our modeline to the bottom of the file.

<pre><code>" vim:foldmethod=marker:foldlevel=0
</code></pre>

Finally, we need to visually wrap each section in the fold marker. The fold markers are `{{{` and `}}}`.That looks like this.

<pre><code>" Section Name {{{
set number "This will be folded
" }}}
</code></pre>

That's it. I find this a great way to keep your vimrc highly structured, easy to navigate, and incredibly readable.

## Wrapping It Up {#wrap}

I hope this helped you. The reality is that this was a ton of stuff and I still stand by this platitude:

<pre><code>Don't put anything in your .vimrc you don't understand!
</code></pre>

So, if you grab lines from this, make sure you add comments explaining exactly what is going on. If you can't, `:help [setting]` is your best friend.

Thanks for reading! Don't forget to send me your .vimrc tips at [@thyeun](https://twitter.com/thyeun).

