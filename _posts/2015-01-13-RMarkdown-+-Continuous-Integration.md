---
title: RMarkdown & Continuous Integration
layout: post
---

I added continuous integration using [Travis-CI](https://travis-ci.com) to my
[Make + RMarkdown example](https://github.com/audy/make-rmarkdown). When GitHub
receives a `git push`, Travis will clone the repository and run `make` which
will build all RMarkdown files and notify you of any failures.

This could also be used to build RMarkdown files automatically if the output
could somehow be sent elsewhere. One way to do this would be to send them to a
remote machine using secure-copy or FTP.

This configuration does not handle dependency management. I added a script to
install dependencies but this is less than ideal. R has really only one good
solution for package management called
[Packrat](https://rstudio.github.io/packrat/). Packrat requires all dependencies
to be tracked in Git. I'm not a fan of "vendoring" all dependencies and this
could lead to licensing issues if you publish your code under MIT (many R
libraries are GPL) but Packrat has at least been reliable in my experience.

See [`.travis.yml`](https://github.com/audy/make-rmarkdown/blob/master/.travis.yml)