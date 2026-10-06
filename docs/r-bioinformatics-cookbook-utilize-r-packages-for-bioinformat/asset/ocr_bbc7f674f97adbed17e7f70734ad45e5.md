+   3. Run that on the command line:

```
quarto render mtcars.qmd --to html
```

+   4. Get a Citation Style Language (CSL) file to determine how references will be formatted:

```
csl_path <- fs::path_package("extdata", "bioinformatics.csl",
package="rbioinfcookbook",
file.copy(csl_path, 'somewhere/on/your/system/bioinformatics.
csl')
```

+   5. Extend the YAML to include a PDF block; note—add the existing HTML code:

```
pdf:
pdf-engine: xelatex
papersize: A4\ocumentclass: report
toc: true
toc-title: "Workflow"
lof: true
mainfont: Arial
monofont: Courier
fontsize: "24"
colorlinks: true
cap-location: margin
csl: bioinformatics.csl
```

+   6. Render the document:

```
quarto render mtcars.qmd --to html,pdf
```

+   7. Get a Microsoft Word .docx file to act as a style template for the Microsoft Word doc:

```
docx <- fs::path_package("extdata", "custom-reference-doc.
docx",
package="rbioinfcookbook",
file.copy(docx_path, 'somewhere/on/your/system/custom-reference-
doc.docx')
```

+   8. Extend the YAML header for .docx output:

```
docx:
reference-doc: custom-reference-doc.docx
fig-align: center
fig-width: 20
number-sections: true
citeproc: true
```