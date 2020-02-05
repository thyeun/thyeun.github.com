---
layout: entry
title: SublimeText Getting Started
author: Thomas Yeun
author-email: thyeun@gmail.com
description: SublimeText installation with Package control and apply a theme to use.
publish: true
---


Today we try to explain the process of installing the SublimeText a text editor and use the Package control apply the theme. SublimeText is easier than emacs and vim, free of foresight is a program that favorite designer of sports cars, so pretty. Compared to the other text editor. As well as, if not necessarily in the sports car designers encounter the code is the first program I think is necessary SublimeText. However, installing this program is by using a theme or swiwodo Package control, applying a somewhat strange egen Syntax highlighting allows designers to enroll in the code. If such designers, albeit a little help, I think.

## SublimeText Installation

1. [SublimeText 3 Beta Installation Page](http://www.sublimetext.com/3) To access and download the installation file for your OS. The latest official version is 2.0.2, but many extensions SublimeText 3 Beta enough reliable and, above all, including the Material Theme It is recommended that you install are under the Beta version because it supports only SublimeText 3.

2. Run the downloaded file to install. If the program is open as shown below normal installation is now complete.
<img src="/images/2015-11-14/sublime-default.png" style="margin: 0 auto; width: 752px;" />


## Package Control Installation

Extensions or themes in SublimeText are easy to install, Package Control installation such as Syntax highlighting add or remove are similar concept with the Extension Manager from Adobe.

1. Connect to [Package Control Installation](https://packagecontrol.io/installation).

2. Inside `SUBLIME TEXT 3` copy the code from *[Package Control Website](https://packagecontrol.io/installation), the actual code may be different than the image below.*
<img src="/images/2015-11-14/sublime-code.png" style="margin: 0 auto; width: 688px;" />

3. Inside SublimeText press ```Ctrl + ` ``` or go to `View`>`Show Console`, paste the copies of contents and hit enter.
<img src="/images/2015-11-14/sublime-console.png" style="margin: 0 auto; width: 752px;" />

4. An *alert* will appear after the installation are completed.
<img src="/images/2015-11-14/sublime-popup.png" style="margin: 0 auto; width: 532px;" />

5. Restart the SublimeText.

6. Go to `Preferences` > `Package Control`, after the installation are successful.

  <img src="/images/2015-11-14/sublime-preferences.png" style="margin: 0 auto; width: 410px;" />

## Material Theme Apply

  1. Connect to [Material Theme Website](http://equinusocio.github.io/material-theme/).
    <img src="/images/2015-11-14/sublime-theme.png" style="margin: 0 auto; width: 1000px;">

  2. Press the `INSTALL NOW` button.
    <img src="/images/2015-11-14/sublime-themeinstall.png" style="margin: 0 auto; width: 1000px;">

  3. You will see the below information when you scroll down.

        >**Easy installation**
        >
        >You can install this awesome theme through the Package Control. Search for “Material Theme”, install, restart SublimeText and enjoy!

  4. After restart, go to `Preferences`>`Pakage Control` open the Panel.
  <img src="/images/2015-11-14/sublime-panel.png" style="margin: 0 auto; width: 752px">

  5. Select `Package Control: Install Package`. Shortly after that it has no choice but to look at what changes at the bottom of the SublimeText at the bottom of the bar `[=   ]` back bar so you can see what are loaded.
  <img src="/images/2015-11-14/sublime-install.png" style="margin: 0 auto; width: 752px">

  6. Inside the panel of the package list, choose `Material Theme` and see what are already install.
  <img src="/images/2015-11-14/sublime-search.png" style="margin: 0 auto; width: 752px">

  7. Once a theme is installed, the following message appears in the editor window. The theme is now the state does not apply, but the installation. Let's continue to apply the theme.
  <img src="/images/2015-11-14/sublime-doc.png" style="margin: 0 auto; width: 752px">

  8. A message will appear the below information.

<pre><code>If installing manually (not through Package Control), add the following to your Settings - User file and restart Sublime Text after:
"theme": "Material-Theme.sublime-theme",
 "color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme",
</code></pre>
  The document says, follow the above information, but only if you installed it manually, so this also applies installed using the Package Control does not automatically apply to manually. Copy the code within the  bracket. 
<pre><code>"theme": "Material-Theme.sublime-theme",
"color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme",</code></pre>
  9. Go to `Preferences` in the menu, open the setting windows `Settings - User`.
   <img src="/images/2015-11-14/sublime-user.png" style="margin: 0 auto; width: 410px;">
   <img src="/images/2015-11-14/sublime-pref.png" style="margin: 0 auto; width: 752px;">

  10. Copy the two line of the extra code and paste it after line 8, dont even paste the code inside `{``}`. Save it by pressing `Ctrl + s`.
  <img src="/images/2015-11-14/sublime-apply.png" style="margin: 0 auto; width: 752px;">
  
  Before,

<pre><code>"ignored_packages":
["Vintage"]</code></pre>
  
  After,

<pre><code>"ignored_packages":
["Vintage"],
"theme": "Material-Theme.sublime-theme",
"color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme"</code></pre>

  11. After change of the code by pressing  `Ctrl + s` to save it, it will automatically applied the theme. Reboot in order to use all the SublimeText once installation is complete.


## Material Theme Adjusting The Color Change Style

[Material Theme Website](http://equinusocio.github.io/material-theme/)As you can see from the Material Theme, it has three version, `Default`, `Lighter`, and `Darker`. Just like the characters and the themes change every line in the Lighter versions installed size, let's fix it.

  1. Connect to [Material Theme Installation Page](https://packagecontrol.io/packages/Material%20Theme).

  2. Scroll down inside **Theme styles** and copy the code below.

<pre><code>"theme": "Material-Theme-Lighter.sublime-theme",
"color_scheme": "Packages/Material Theme/schemes/Material-Theme-Lighter.tmTheme",</code></pre>

  3. Go to `Preferences` and choose `Settings - User`.
    <img src="/images/2015-11-14/sublime-user.png" style="margin: 0 auto; width: 410px;">

  4. Replace the code for Material Theme.  

  <h5>Original code of Material Theme</h5>
  <pre><code>"theme": "Material-Theme.sublime-theme",
"color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme",</code></pre>
  <h5>Code for Material Theme Lighter</h5>
  <pre><code>"theme": "Material-Theme-Lighter.sublime-theme",
"color_scheme": "Packages/Material Theme/schemes/Material-Theme-Lighter.tmTheme",</code></pre>
   Comparing the two code Lighter theme can be seen that the addition of a named Lighter in the default theme code.

  5. Pressing `Ctrl + s` to save it, Material Theme Lighter will appear like the image below.
    <img src="/images/2015-11-14/sublime-lighter.png" style="margin: 0 auto; width: 752px;">

  6. Let try to adjust the text style. Connect to [Material Theme Installation Page](https://packagecontrol.io/packages/Material%20Theme), look for the area **Recommended UI and font settings for a better experience:** .

  7. Copy the code and paste in `Preferences.sublime-settings` the document you opened above.

<pre><code>"overlay_scroll_bars": "enabled",
"line_padding_top": 3,
"line_padding_bottom": 3,
"always_show_minimap_viewport": true,
"bold_folder_labels": true,
"indent_guide_options": [ "draw_normal", "draw_active" ], // Highlight active indent
"font_options": [ "gray_antialias" ], // On retina Mac</code></pre>

  8. Similar by pressing `Ctrl + s`, will change the style of the theme.
    <img src="/images/2015-11-14/sublime-ui.png" style="margin: 0 auto; width: 752px;">

  9. Change the font type `"font_options": [ "gray_antialias" ]`.
    <img src="/images/2015-11-14/sublime-regular.png" style="margin: 0 auto; width: 752px;">

  10. Adjust the font size `"font_size"` and `"line_padding_top"`, `"line_padding_bottom"`.

  11. Save the settings and restart the SublimeText.

---

Did you read well? Designers who are expected to continue to increase posted in the relevant subjects to be enrolled in the code a little easier. See you then have to find a basic SublimeText use. Thanks for reading.
