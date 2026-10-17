To apply the same options to all chunks in the document at once, you can add them to the first chunk at the very top of your Quarto that has the label label: setup using the knitr::opts_chunk$set() function. These are called the global settings. For example, using the following code for your first code chunk ensures that none of the errors, warnings, or messages from any of the code chunks appear in your final report. It is also good practice to load all the packages you are using for your report within this first code chunk using the library() function. For example, we load the tidyverse and HDSinRdata packages.

```
```{r}
#| label: setup
#| include: false
knitr::opts_chunk$set(echo = TRUE, warning = FALSE,
                      error = FALSE, echo = FALSE)
library(tidyverse)
library(HDSinRdata)
```
```

If you want to display the code for your report in a code appendix, you can easily do this by creating an empty code chunk at the end of your .qmd file that looks like the following. This finds all other chunks and displays the code.

```
```{r ref.label = knitr::all_labels()}
#| echo: true
#| eval: false
```
```

# ## 22.2 Formatting Text in Markdown

To add text to your report, you can simply type directly into the Quarto file, between the code chunks. This code is formatted using Markdown, which allows us to specify how to format and display the text when it is knit. For example, adding a single asterisk * on either side of some text italicizes it, while adding a double asterisk ** on either side of text makes it bold. To indicate code, you can use backticks ` .