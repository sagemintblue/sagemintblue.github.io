---
title: "From Octopress to Jekyll"
comments: true
categories: octopress jekyll
---

Good grief it's been a while. Octopress is no longer in development. [GitHub Pages][1] now supports
[Jekyll][2] directly: A repo can be configured to build a Jekyll-based website automatically when
changes are pushed to a particular branch.

I'm considering using [Poole][3] to spruce up the site design, but I'm not yet sure if the GitHub
Pages "branch" deploy process supports the extensions which Poole requires. I'd like to keep things
simple before jumping into something that'd require a more complex deploy processes using GitHub
Actions.

And of course I just found [Hugo][4]...

[1]: https://pages.github.com/
[2]: https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll
[3]: https://getpoole.com/
[4]: https://gohugo.io/
