# Computing new data columns from existing ones and applying arbitrary functions mutate() 37

```
tissue1 = c(5.1, 7.3, 8.2)
tissue2 = c(4.8, 6.1, 9.5)
tissue3 = c(8.5, 12.5, 6.5))
```

```
df <- df |>
rowwise() |>
mutate(mean = mean(c(tissue1, tissue2, tissue3)),
  stddev = sd(c(tissue1, tissue2, tissue3))
)
```

+   4. Operate on nested:
df <- data.frame(gene_id = c("genel", "gene2", "gene3\),
  tissue1_value = c(5.1, 7.3, 8.2),
  tissue1_pvalue = c(0.01, 0.05, 0.001),
  tissue2_value = c(4.8, 6.1, 9.5),
  tissue2_pvalue = c(0.03, 0.04, 0.001))
)
tidyr::nest(-gene_id, .key = "tissue")

```
df <- df |> mutate(tissue = purrr::map(tissue, mutate(.x,
value_log2 = log2([.1]), pvalue_log2 = log2([.2])))
```

The various ways we can work with mutate() on different data frames to different ends.

# How it works..

In step 1, we start by creating a data frame containing three genes, columns representing the values of each gene. Then, we use the mutate() [custom-style='P - Code’] function in its most basic form to apply the log2 transformation of the values into new columns.

In step 2, we apply the transformation conditionally with mutate_if(), which applies the specified function to all columns that match the specified condition (in this case, is.numeric), and mutate_at() to apply the log2 function to all columns that start with the name tissue.

In step 3, we create a bigger data frame of expression and use the rowwise() function in conjunction with mutate(), mean and stddev, which can the mean and standard deviation of the expression values across all three tissues for each gene. If we just use mutate() on the vector, the function will be applied to the entire column instead of the rows. We need to calculate the mean and standard deviation of the expression values across all tissues, which would be difficult to achieve just using mutate() on vectors in the standard-wise fashion.