---
layout: post
title: Fighting with the WP.com post editor
date: 2013-01-20 16:15
comments: true
categories: wordpress
---

As soon as I start a code-oriented blog I find out that the WordPress post editor doesn't have a
keyboard shortcut for applying `<code/>` to selected text.. Bah!

I'm looking for a few ways around this:

* An external editor (web-based or otherwise) which supports auto-conversion of [markdown] into html
  and uploads to WP.com.
* Chrome extension or [userscript] to hack in an additional `ctrl-shift-c` keyboard shortcut for the
  [TinyMCE editor][tinymce] used by WP.

Relevant links:

* <http://www.beginwp.com/list-of-keyboard-shortcut-wordpress/> - Seems to suggest a keyboard shortcut
  for insertion of `<code/>` does exist, but I couldn't get it to work in Mac Chrome 24.0.1312.52.
* <http://davejamesmiller.com/snippets/wordpress-keyboard-shortcuts-to-indentoutdent-and-format-as-code-in-tinymce>
* <http://wordpress.org/extend/plugins/wysiwyg-inline-code-command/>
* <http://wordpress.stackexchange.com/questions/33444/how-to-add-tinymce-keyboard-shortcut>
* <http://wordpress.org/extend/plugins/wp-markdown/>

Update 2013-01-21

I found a number of useful projects on which I could build the chrome extension I'd mentioned above,
including [marked] and [EpicEditor], but then I landed on [Octopress] and may have to migrate
there. What's not to love about a blogging framework you have complete control over and can host
directly on Github?

[markdown]: http://daringfireball.net/projects/markdown/
[userscript]: http://userscripts.org/
[marked]: https://github.com/chjj/marked/
[epiceditor]: http://epiceditor.com/
[octopress]: http://octopress.org/
[tinymce]: http://www.tinymce.com/
