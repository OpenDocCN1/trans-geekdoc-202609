to do. The comments are there to help explain the steps, but you may also want to print the output to figure out what it is doing.

```
sample_strA <- " A systematic search will be performed in PubMed,
Embase, and the Cochrane Library, using the following search query:
('out-of-hospital cardiac arrest' OR 'OHCA') AND ('MIRACLE 2' OR
'OHCA' OR 'CAHP' OR 'C-GRAPH' OR 'SOFA' OR 'APACHE' OR 'SAPS' OR
'SWAP' OR 'TTM')."

sample_strB <- "Searches will be conducted in MEDLINE via PubMed, Web
of Science, Scopus and Embase. The following search strategy will be
used:(child OR infant OR preschool child OR preschool children OR
preschooler OR pre-school child OR pre-school children OR pre school
child OR pre school children OR pre-schooler OR pre schooler OR pre
scholar OR pre scholars OR children OR adolescents OR adolescent OR
children)AND(attention deficit disorder with hyperactivity OR ADHD OR
attention deficit disorder OR ADD OR hyperkinetic disorder OR minimal
brain disorder) Submitted "
```

```
sample_str <- sample_strB

# separate parentheses, remove extra white space, and split into words
sample_str <- str_replace(sample_str, ")\\", ""\\)")
sample_str <- str_replace(sample_str, ")\\", ""\\(")
sample_str <- str_squish(sample_str)
sample_str_words <- str_split_1(sample_str, " ")

# find indices with parentheses
end_ps <- grepl(x = sample_str_words, pattern = "\\)")
start_ps <- grepl(x = sample_str_words, pattern = "\\(")

# find words between first and last parentheses
search_query <- sample_str_words[which(end_ps)[1]:which(start_ps)[1]]
search_query <- paste(search_query, collapse=" ")
search_query
#> [1] ") adolescents OR adolescent OR children OR schooler pre OR
↳ pre-schooler OR children school pre OR child school pre OR
↳ children pre-school OR child pre-school OR preschooler OR children
↳ preschool OR child preschool OR infant OR child (

# find search terms
search_terms <- str_replace_all(search_query, "\\)", "")
search_terms <- str_replace_all(search_query, "\\(", "")
sample_terms <- str_squish(search_query)
```