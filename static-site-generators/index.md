# Static Site Generators


Static site generators (SSGs) compiles simple text files (like markdown) into websites.

See also [awesome static site generators](https://github.com/myles/awesome-static-generators).

<!--more-->

## Sort by programming languages

### R

- [Bookdown](https://bookdown.org) : Write HTML, PDF, ePub, and Kindle books with R Markdown.

### Ruby

- [Jekyll](https://jekyllrb.com/) : The default SSG for GitHub pages.

## Rust

- [mdBook](https://github.com/rust-lang/mdBook) : Create book from markdown files. Like Gitbook but implemented in Rust.
- [Zola](https://github.com/getzola/zola) : A fast static site generator in a single binary with everything built-in.

### Javascript / npm

- [Docsify](https://docsify.js.org/) : Rendering Markdown files on-the-fly. [Awesome docsify](https://docsify.js.org/#/awesome).
- [Gatsby.js](https://www.gatsbyjs.com) : A blazing fast React-based SSG. Some javascript knowledge is required.
- [Hexo](https://hexo.io) : A fast, simple & powerful blog framework written in NodeJS. [Themes](https://hexo.io/themes/) and [plugins](https://hexo.io/plugins/).

### Go

- [Hugo](https://gohugo.io/) : The fastest framework for building websites, written in Go. [Themes](https://themes.gohugo.io/).

### Python

- [Jupyterbook](https://jupyterbook.org/intro.html) : Building beautiful, publication-quality books and documents from jupytr notebooks.
- [MkDocs](https://www.mkdocs.org) : MkDocs is a fast, simple and downright gorgeous static site generator that's geared towards building project documentation. [Material theme](https://squidfunk.github.io/mkdocs-material/)
- [Nikola](https://getnikola.com/) : Static Site Generator written in Python.

### Julia

- [Franklin.jl](https://github.com/tlienart/Franklin.jl) : Static site generation with live Julia code evaulation. [Examples](https://github.com/tlienart/Franklin.jl#docs).
- [PkgPage.jl](https://tlienart.github.io/PkgPage.jl/) : Creating (package) front-pages, powered by `Franklin.jl`.
- [StaticWebPages.jl](https://github.com/Azzaare/StaticWebPages.jl) : Create academics and personal CV web-pages.


## SSGs I used so far

### Hugo

[Hugo](https://gohugo.io/) is the world’s fastest framework for building websites, written in Go.

**Pros 👍**

- Extremely fast. It builds a large website within 3 seconds.
- Single dependency with one `hugo` excutable only.
- Able to costomize and override theme default without messing up the theme files.[^hugooverride]

[^hugooverride]: In Hugo, you are able to [override default layouts and settings](https://zwbetz.com/override-a-hugo-theme/) by placing counterpart file(s) in your site folder. Hugo will look at your custom setting first without messing with the theme folder, which is much more friendly for Git submodules and theme updates.

**Cons 👎**

- Limited extensions and modules.
- Some GoLang knowledge maybe required besides HTML if you want to make templates.

**Themes**

- [DoIT](https://hugodoit.pages.dev/) : used in this blog.
- [book](https://github.com/alex-shpak/hugo-book)
- [clarity](https://github.com/chipzoller/hugo-clarity)
- [meme](https://github.com/reuixiy/hugo-theme-meme)

**See also**

[My blog post]({{< relref "hugo-setup.md" >}}) about Hugo site setup.

### Hexo

**Pros 👍**

- A huge set of plugins thanks to the `npm` ecosystem.
- Plentiful Chinese resources.
- Relatively fast. It builds a large website under 1 minute.

**Cons 👎**

- Hundreds of nodeJS dependencies. If you are familiar with npm package management it might not be a problem.
- For LaTeX math typesetting, you need to change the renderer to either the `pandoc` one or the `markdown-it` one.
- Less intuitive [asset management](https://hexo.io/docs/asset-folders.html).

**Themes**

- [Next](https://theme-next.js.org/)
- [fluid](https://fluid-dev.github.io/hexo-fluid-docs/)
- [butterfly](https://butterfly.js.org/)

### Docsify

[Docsify](https://docsify.js.org/) renders Markdown files to HTML on-the-fly.

**Pros 👍**

- Minimal dependency: just one `index.html` and some markdown files.
- It skips the building step and renders Markdown file on-the-fly.
- Handy extensions on [awesome docsify](https://docsify.js.org/#/awesome).

**Cons 👎**

- No support for tags, categories, and footnotes extensions.
- The KaTeX extension does not support `mhchem` extension.

## Others

- [Jekyll](https://jekyllrb.com/), the default GitHub pages SSG written in Ruby. Generating a large site is slower compared to either Hugo or Hexo, taking several minutes.
- [Nikola](https://getnikola.com/), a SSG written in Python with first-class support of Markdown (`*.md`), reStructuredText (`*.rst`) and Jupyter Notebook (`*.ipynb`) files.
- [JupyterBook](https://jupyterbook.org), powered by the [Sphinx](https://www.sphinx-doc.org/en/master/) python documentation generator, builds beautiful, publication-quality books and documents from Markdown (`*.md`), reStructuredText (`*.rst`) and Jupyter Notebook (`*.ipynb`) files.
- [Gatsby.js](https://www.gatsbyjs.com) is a blazing fast React-based open-source framework for creating websites and apps. Some Javascript Node.js knowledge is required to build a site.

