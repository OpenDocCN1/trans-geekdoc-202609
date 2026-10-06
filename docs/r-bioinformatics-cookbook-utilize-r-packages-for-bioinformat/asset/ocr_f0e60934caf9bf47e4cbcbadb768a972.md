```
package = "rbiocookbook"
)

seqs <- readAAStringStringSet(seqfile)
```

+   2. Make a basic dot plot:

```
dotPlotg(as.character(seqs[[1]]),
as.character(seqs[[2]]))
```

+   3. Change the dot plot and apply themes and labels:

```
dotPlotg(as.character(seqs[[1]]), as.character(seqs[[2]]),
width=7, wstep=5,
nmatch4=4) + theme_bw() +
labs(x=names(seqs)[1], y=names(seqs)[2] )
```

+   4. Make a function that will create a dot plot automatically:

```
make_dot_plot <- function(i=1, j=1, seqs = NULL){
seqi <- as.character(seqs[[i]])
seqj <- as.character(seqs[[j]])
namei <- names(seqs)[i]

namej <- names(seqs)[j]
return(dotPlotg(seqi, seqj) + 
theme_bw() + labs(x=namei, y=namej))
}
```

+   5. Set up data structures to run the function:

```
combinations <- expand.grid(1:length(seqs),1:length(seqs))
plots <- vector("list", nrow(combinations))
```

+   6. Run the function on all the possible combinations:

```
for (r in 1:nrow(combinations)) {
i <- combinations[r,]$Var1[[1]]
j <- combinations[r,]$Var2[[1]]
plots[r] <- make_dot_plot(i,j, seqs)
}
```

+   7. Plot the grid of plots:

```
cowplot::plot_grid(plotlist = plots)
```

That is all we need to do.