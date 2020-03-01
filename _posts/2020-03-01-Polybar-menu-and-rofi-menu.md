---
layout: entry
title: Polybar Menu Module
author: Thomas Yeun
author-email: thyeun@gmail.com
description: Polybar i3
publish: true
---


## i3wm

*i3* is a tiling window manager designed for [X11](https://en.wikipedia.org/wiki/X_Window_System), inspired by [wmii](https://en.wikipedia.org/wiki/Tiling_window_manager#X-tile-anchor), and written in [C](https://en.wikipedia.org/wiki/C_(programming_language)). It supports tiling, stacking, and tabbing layouts, which it handles dynamically. Configuration is achieved via plain text file and extending i3 is possible using its [Unix domain socket](https://en.wikipedia.org/wiki/Unix_domain_socket) and [JSON](https://en.wikipedia.org/wiki/JSON) based [IPC](https://en.wikipedia.org/wiki/Inter-process_communication) interface from many programming languages.

Like [wmii](https://en.wikipedia.org/wiki/Tiling_window_manager#X-tile-anchor), i3 uses a control system very similar to [vi](https://en.wikipedia.org/wiki/Vi). By default, window focus is controlled by the `'Mod1'` (Alt key/Win key) plus the right hand home row keys (`Mod1+J,K,L,;`), while window movement is controlled by the addition of the Shift key (`Mod1+Shift+J,K,L,;`).

## Polybar

*[Polybar](https://github.com/polybar/polybar)* is a fast and easy-to-use tool for creating status bars. It aims to be easily customizable, utilising many modules which enable a wide range of (editable) functionality, such as displaying workspaces, the date, or system volume. Polybar is especially useful for *window managers* that have a limited or non-existent status bar, such as *awesome* or *i3*. Polybar can also be used with *desktop environments* like *Plasma*.

## Module

You can configuration your polybar with extra module, such as *xwindows*, *xworkspaces*, *menu* and etc.

## Menu module

You can have your own menu module for polybar.

**Polybar Configuration**

Than open up your polybar config file `~/.config/polybar/config`, look for the line below

<pre><code>modules-left =  menu i3
</code></pre>

And add-in the `menu` module name.

To create the module, add-in the below line.

<pre><code>[module/menu]
type = custom/menu
expand-right = true

label-open = "  "
label-close = "  "
label-open-foreground = ${colors.black}
label-open-background = ${colors.green}
label-open-underline = ${colors.green1}
label-close-foreground = ${colors.black}
label-close-background = ${colors.green}
label-close-underline = ${colors.green1}
label-separator = •
label-open-radius = 9
label-close-radius = 9


menu-0-0-foreground = ${colors.black}
menu-0-0-background = ${colors.red}
menu-0-0-underline = ${colors.red1}

menu-0-1-foreground = ${colors.black}
menu-0-1-background = ${colors.green}
menu-0-1-underline = ${colors.green1}

menu-0-2-foreground = ${colors.black}
menu-0-2-background = ${colors.blue}
menu-0-2-underline = ${colors.blue1}

menu-0-3-foreground = ${colors.black}
menu-0-3-background = ${colors.cyan}
menu-0-3-underline = ${colors.cyan1}

menu-0-4-foreground = ${colors.black}
menu-0-4-background = ${colors.violet}
menu-0-4-underline = ${colors.violet1}

menu-0-5-foreground = ${colors.black}
menu-0-5-background = ${colors.orange}
menu-0-5-underline = ${colors.orange1}

menu-0-6-foreground = ${colors.black}
menu-0-6-background = ${colors.yellow}
menu-0-6-underline = ${colors.yellow1}

menu-0-0 = "  "
menu-0-0-exec = chromium &
menu-0-1 = "  "
menu-0-1-exec = firefox &
menu-0-2 = "  "
menu-0-2-exec = surf &
menu-0-3 = "  "
menu-0-3-exec = thunar &
menu-0-4 = "  "
menu-0-4-exec = subl3 &
menu-0-5 = "  "
menu-0-5-exec = code &
menu-0-6 = "  "
menu-0-6-exec = termite &
</code></pre>

And change the unicode as you like per each menu.

You will have the result as below

<img src="/images/2020-03-01/polybar-menu.jpg" style="margin: 0 auto; width: 688px;" />

