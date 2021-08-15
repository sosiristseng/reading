# Static Site Generators


Static site generators (SSGs) compiles simple text files (like markdown) into websites.

See also [awesome static site generators](https://github.com/myles/awesome-static-generators).

<!--more-->

## Sort by programming languages

### R
- [Bookdown](https://bookdown.org) : Write HTML, PDF, ePub, and Kindle books with R Markdown.

### Ruby
- [Jekyll](https://jekyllrb.com/) : The default SSG for GitHub pages.

### Javascript / npm
- [Docsify](https://docsify.js.org/) : Rendering Markdown files on-the-fly. [Awesome docsify](https://docsify.js.org/#/awesome).
- [Gatsby.js](https://www.gatsbyjs.com) : A blazing fast React-based SSG. Some javascript knowledge is required.
- [Hexo](https://hexo.io) : A fast, simple & powerful blog framework written in NodeJS. [Themes](https://hexo.io/themes/) and [plugins](https://hexo.io/plugins/).

### Go
- [Hugo](https://gohugo.io/) : The fastest framework for building websites, written in Go. [Themes](https://themes.gohugo.io/).

### Python
- [Nikola](https://getnikola.com/) : Static Site Generator written in Python.
- [Jupyterbook](https://jupyterbook.org/intro.html) : Building beautiful, publication-quality books and documents from jupytr notebooks.

### Julia
- [Franklin.jl](https://github.com/tlienart/Franklin.jl) :: Static site generation with live Julia code evaulation. [Examples](https://github.com/tlienart/Franklin.jl#docs).
- [PkgPage.jl](https://tlienart.github.io/PkgPage.jl/) : Creating (package) front-pages, powered by `Franklin.jl`.
- [StaticWebPages.jl](https://github.com/Azzaare/StaticWebPages.jl) : Create academics and personal CV web-pages.

## I've always wanted to have a tech blog that is
- looking nice 🥰
- fast and responsive
- having full-text search
- tracking the progress I made
- browser through keywords for my articles
- displaying math and chemical expressions


## Hugo

[Hugo](https://gohugo.io/) is the world’s fastest framework for building websites, written in Go.

**Pros 👍**

- Single dependency with one `hugo` excutable only.
- Extremely fast. It builds a large website within 5 seconds.
- Able to customize / override default settings without messing up the theme files.[^hugooverride]

[^hugooverride]: In Hugo, you are able to [override default layouts and settings](https://zwbetz.com/override-a-hugo-theme/) by placing counterpart file(s) in your site folder. Hugo will look at your custom setting first without messing with the theme folder, which is much more friendly for Git submodules and theme updates.

**Cons 👎**

- A limited number of extensions.
- GoLang knowledge is required if you want to make templates.

**Themes**

- [codeIT](https://github.com/sunt-programator/CodeIT) : used in this blog.
- [clarity](https://github.com/chipzoller/hugo-clarity)
- [color your world](https://gitlab.com/rmaguiar/hugo-theme-color-your-world)
- [meme](https://github.com/reuixiy/hugo-theme-meme)
- [zzo](https://github.com/zzossig/hugo-theme-zzo)

## Hexo

**Pros 👍**

- A huge set of plugins thanks to the npm ecosystem.
- Plentiful Chinese resources.
- Relatively fast. It builds a large website under 1 minute.

**Cons 👎**

- Hundreds of npm dependencies. If you are familiar with npm packages it might not be a problem.
- For LaTeX math typesetting, you need to change the renderer to either the pandoc one, which requires the `pandoc` binary or the markdown-it one, in which chemical typesetting (`mhchem`) does not work well.
- More complicated to override the templates in the theme.
- Less intuitive [asset management](https://hexo.io/docs/asset-folders.html).

**Themes**

- [Next](https://theme-next.js.org/)
- [fluid](https://fluid-dev.github.io/hexo-fluid-docs/)
- [butterfly](https://butterfly.js.org/)

## Docsify

[Docsify](https://docsify.js.org/) renders Markdown files to HTML on-the-fly.

**Pros 👍**

- Minimal dependency: just one `index.html` with JS/CSS and you're good to go.
- Fast. It skips the building step and renders Markdown file on-the-fly.
- Handy extensions on [awesome docsify](https://docsify.js.org/#/awesome).

**Cons 👎**

- No support for tags and categories.
- KaTeX extension does not support `mhchem`.

## Others

- [Jekyll](https://jekyllrb.com/), the default GitHub pages SSG written in Ruby. Generating a large site is slower compared to either Hugo or Hexo, taking several minutes.
- [Nikola](https://getnikola.com/), a SSG written in Python with first-class support of Markdown (`*.md`), reStructuredText (`*.rst`) and Jupyter Notebook (`*.ipynb`) files.
- [JupyterBook](https://jupyterbook.org), powered by the [Sphinx](https://www.sphinx-doc.org/en/master/) python documentation generator, builds beautiful, publication-quality books and documents from Markdown (`*.md`), reStructuredText (`*.rst`) and Jupyter Notebook (`*.ipynb`) files.
- [Gatsby.js](https://www.gatsbyjs.com) is a blazing fast React-based open-source framework for creating websites and apps. Some Javascript Node.js knowledge is required to build a site.

