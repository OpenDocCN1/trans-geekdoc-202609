Set up the color palettes for the different datasets:

```
data_col_func <- circlize::colorRamp2(seq(0, max(mat), length
out = 6), viridisLite::magma(6))

ecotype_colors <- c(RColorBrewer::brewer.pal(12, "Set3"),
RColorBrewer::brewer.pal(5, "Set1")
names(ecotype_colors) <- unique(ecotype)

part_colors <- RColorBrewer::brewer.pal(3, "Accent")
names(part_colors) <- unique(part)
```

Create the annotation that will sit alongside the main heatmap:

```
top_annot <- HeatmapAnnotation("Ecotype" = ecotype,
"Plant Part" = part,
col = list("Ecotype" = ecotype_
colors,
"Plant Part" = part_
annotation_name_side = "left")
```

```
side_annot <- rowAnnotation(length = gex$Length, size = 16, unit(1, "mm"),
axis_param = list(axis = seq(1), max(at_tf_gex$Length),
out=4)
 )
```

Create the first heatmap:

```
ht_1 <- Heatmap(mat, name="log (TPM)", row_km = 6,
col = data_col_func,
top_annotation = top_annot,
right_annotation = side_annot,
cluster_columns = TRUE,
column_split = ecotype,
show_column_names = FALSE,
column_title = " "
)
```

Manipulate the TF data into a simpler version and select to display it:

```
of_interest <- c("BHLH", "WRKY", "bZIP")
short_family <- at_tf_gex$Family
short_family[! short_family %in% of_interest] <- "other"
```