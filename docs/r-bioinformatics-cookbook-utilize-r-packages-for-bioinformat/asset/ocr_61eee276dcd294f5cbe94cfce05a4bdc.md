# Getting ready

We'll need a sample R Markdown document provided by the rbioinfcookbook package, so install the fs package, and the ggplot2 package, if you haven't got it already. You'll also need to follow the instructions for installing Quarto at the start of the chapter. Make sure you also have installed TinyTeX, which is needed by Quarto, also discussed at the start of the chapter.

# How to do it...

We can prep a marked-up document for rendering to various formats as follows:

+   Save the example file accessible:

```
qmd_path <- fs::path_package("extdata", "mtcars.qmd",
package=rbioinfcookbook)
file.copy(qmd_path, 'somwhere/on/your/system/mtcars.qmd')

bib_path <- fs::path_package("extdata", "mtcars.bib",
package=rbioinfcookbook)
file.copy(bib_path, 'somwhere/on/your/system/mtcars.bib')
```

+   In your editor, add a YAML header for HTML:

```
----
title: "mtcars Analysis"
ubtitle: "an analysis in many formats"
author: "anrwizard@email.com"
date-modified: "%r format(Sys.time()), '%d %B, %Y')"
email-obfuscation: javascript
ibliography: mtcars.bib
execute:
  echo: true
  warning: false
format:
  html:
    theme: cyborg
    toc: true
    toc-location: left
    html-math-method: katex
    css: styles.css
    number-sections: true
    cap-location: top
    code-fold: true
    code-line-numbers: true
    citations-hover: false
---
```