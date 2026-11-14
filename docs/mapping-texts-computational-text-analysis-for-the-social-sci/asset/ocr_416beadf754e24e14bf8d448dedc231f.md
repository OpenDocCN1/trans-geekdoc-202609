15 We'll never load them all at once! The last loaded packages' functions will "mask" any other functions with the same name. So, only load packages you need. We can also be explicit by using the double colon :: between the package name and the function.

following code loads the text2map package. This provides access to all its functions during this session.

```
library(text2map)
```

To explore those functions and to get further documentation, use:

```
?text2map # main package page
help(package = text2map) # lists all functions
browseVignettes("text2map") # loads any "vignettes"
```

For this book, we'll need several packages (see Appendix). Install them now.15 The following are all the packages we'll need that are available from CRAN:

```
cran_pkgs <- c(
  "backbone", "-c("
  "factoextra", "gender", "ggpubr", "ggraph",
  "ggrepl", "ggtern", "glmnet", "gmodels", "googleLanguageR",
  "guardianapi", "gutenbergr", "hunspell", "igraph", "irr",
  "lexicon", "lsa", "marginaleffects", "Matrix", "network", "proustr",
  "qadpDictionaries", "quanteda", "quanteda.textmodels", "remotes",
  "reshape2", "reticulate", "rsample", "rsvd", "rtrek",
  "sengm", "sentimentr", "sna", "stm", "stminsights",
  "stringi", "tesseract", "text2map", "text2vec", "textclean",
  "textstem", "tidytext", "tidymodels", "tidyquant", "tidytext",
  "tidyverse", "tokenizers", "topicdoc", "topicmodels", "udpipe"
)
install.packages(cran_pkgs)
```

The following packages are hosted on repositories other than CRAN. We'll first install those hosted on GitHub. To install them, we need remotes .

```
library(remotes)
install_github("trinker/entity")
install_github("trinker/tagger")
install_github("trinker/termo")
install_github("trinker/coreNLPsetup")
install_github("quanteda/quanteda.corpora")
install_github("lmullen/genderdata")
```

We also wrote specialized text analysis packages to support this work, hosted on GitLab. Install them by running the following:

```
repo <- "culturalcartography/"
pkgs <- c("text2map.theme", "text2map.corpora",
"text2map.pretrained", "text2map.dictionaries")
gl_pcks <- paste0(repo, pcks)
install_gitlab(gl_pcks)
```

# Using Python in R

A few R functions we'll use depend on packages written in Python — another popular programming language. To deal with this, we'll install