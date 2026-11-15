Now, we can summarize the label distribution in counts:

```
> summary(data$label)
   0   1   2   3   4   5   6   7   8   9
4132 4684 4177 4351 4072 3795 4137 4401 4063 4188
```

Or combined with proportion (%):

```
> proportion <- prop.table(table(data$label)) * 100
> cbind(count=table(data$label), proportion=proportion)
  count proportion
0 4132  9.838095
1 4684  11.152381
2 4177  9.945238
3 4351  10.359524
4 4072  9.695238
5 3795  9.035714
6 4137  9.850000
7 4401  10.478571
8 4063  9.673810
9 4188  9.971429
```

Classes are balanced.

Now, we explore the distribution of features, the pixels. As an example, we take the 4 pixels from the central 2*2 block (that is, pixel376, pixel377, pixel404, and pixel405) in each image and display the histogram for each of the 9 digits:

```
> central_block <- c("pixel376", "pixel377", "pixel404", "pixel405")
> par(mfrow=c(2, 2))
> for (i in 1:9) {
+   hist (c(as.matrix(data[data$label==i, central_block])),
+   main=sprintf("Histogram for digit %d", i),
+   xlab="Pixel value")
+ }
```