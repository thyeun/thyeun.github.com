---
layout: entry
title: Polybar Profile module
author: Thomas Yeun
author-email: thyeun@gmail.com
description: i3
publish: true
---


## i3wm

*i3* is a tiling window manager designed for [X11](https://en.wikipedia.org/wiki/X_Window_System), inspired by [wmii](https://en.wikipedia.org/wiki/Tiling_window_manager#X-tile-anchor), and written in [C](https://en.wikipedia.org/wiki/C_(programming_language)). It supports tiling, stacking, and tabbing layouts, which it handles dynamically. Configuration is achieved via plain text file and extending i3 is possible using its [Unix domain socket](https://en.wikipedia.org/wiki/Unix_domain_socket) and [JSON](https://en.wikipedia.org/wiki/JSON) based [IPC](https://en.wikipedia.org/wiki/Inter-process_communication) interface from many programming languages.

Like [wmii](https://en.wikipedia.org/wiki/Tiling_window_manager#X-tile-anchor), i3 uses a control system very similar to [vi](https://en.wikipedia.org/wiki/Vi). By default, window focus is controlled by the `'Mod1'` (Alt key/Win key) plus the right hand home row keys (`Mod1+J,K,L,;`), while window movement is controlled by the addition of the Shift key (`Mod1+Shift+J,K,L,;`).

## Polybar

*[Polybar](https://github.com/polybar/polybar)* is a fast and easy-to-use tool for creating status bars. It aims to be easily customizable, utilising many modules which enable a wide range of (editable) functionality, such as displaying workspaces, the date, or system volume. Polybar is especially useful for *window managers* that have a limited or non-existent status bar, such as *awesome* or *i3*. Polybar can also be used with *desktop environments* like *Plasma*.

## Module

You can configuration your polybar with extra module, such as *xwindows*, *xworkspaces*, *menu* and etc.

## Profile module

To make your own profile module for polybar, you need to install mugshot.

**Arch Linux**

<pre><code>pacman -S mugshot </pre></code>

Than open up your polybar config file `~/.config/polybar/config`, look for the line below

<pre><code>modules-right =  arch-aur-updates mail cpu memory date profile </pre></code>

And add-in the `profile` module name.

To create the module, add-in the below line.

<pre><code>[module/profile]
type = custom/script
exec = echo "  "
interval = 1
click-left = exec mugshot
format-foreground = ${colors.black}
format-background = ${colors.blue}
format-underline = ${colors.blue1} </pre>
</code>

And change the unicode as you like on line `exec = echo "  "`.

You will the result once you left click as below

<img src="/images/2020-02-07/profile.png" style="margin: 0 auto; width: 688px;" />

