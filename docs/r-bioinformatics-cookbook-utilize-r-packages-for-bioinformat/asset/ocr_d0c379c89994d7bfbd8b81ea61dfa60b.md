# There's more...

If you need to get the full example file for this recipe, you can extract it from the rbioinfocookbook package like this:

```
qmd_path <- fs::path_package(`extdata`, "presentation.qmd",
package=`rbioinfocookbook`)
file.copy(qmd_path, `somewhere/on/your/system/presentation.qmd`)

ref_path <- fs::path_package(`extdata`, "reference_presentation.pptx",
package=`rbioinfo cookbook`)
file.copy(ref_path, `somewhere/on/your/system/reference_presentation.pptx`)
```

This, again, should help you see the document in one go and save some typing.

# Creating websites from collections of Quarto documents

Pandoc is a versatile tool that can convert documents between many different formats, including Markdown, HTML, LaTeX, and PDF. It can be used to convert a collection of Markdown documents into a static website. The basic website is to write the content in Markdown files, use Pandoc to convert the Markdown files to HTML files, and then serve the HTML files using a web server. Quarto enables this workflow by providing templates, a series of extra markup, and rendering configurations that simplify the render through Pandoc.

The produced website can be hosted like any other. In particular, but perhaps not obvious, utility for bioinformatics is GitHub, which can be used as a hosting platform for the static website. GitHub allows users to create a repository to store the rendered sites, and then GitHub Pages to host the static website. GitHub Pages is a free service that can host static websites that are built from a GitHub repository; Quarto also provides various tiers of hosting for your site.

In this recipe, we'll look at how to configure and render multiple Markdown documents into a site using Quarto.

# Getting ready

We'll need a set of R Markdown documents that constitute the individual pages of the website. Some useful ones are provided by the rbioinfo cookbook package, so install that. We'll also need the fs package that we'll use to locate our sample files. You'll also need to have followed the instructions for installing Quarto at the start of the chapter. Make sure you have installed TinyTeX, which is needed by Quarto, as discussed at the start of the chapter.