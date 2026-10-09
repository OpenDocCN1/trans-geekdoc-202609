are in expectation partisan, then the vote for member $i$ on issue $j$ could be predicted as

$$ \mathbb{E}[x_{ij}] = \varphi_{ij}v_{ri}, $$

where, $v_{ri}$ is the member's score along, say, a traditional left-right axis. This is precisely the sort of model that PCA can estimate.

After loading the vote data into R, we can run PCA using `prcomp`:

```
```
> head(votes[1,1:6])

                    Vote.1 Vote.2 Vote.3 Vote.4 Vote.5 Vote.6
BONNER (R AL-1)         -1      1     -1      0      0      1
BRIGHT (D AL-2)          1     -1      1      1      1      1
ROGERS (R AL-3)         -1      1     -1     -1     -1      1
ADERHOLT (R AL-4)       -1      1     -1     -1      1      1
GRIFFITH (D/R AL-5)      1     -1      1      1      1     -1
BACHUS (R AL-6)         -1      1     -1      1      1      1

> pcavote <- prcomp(votes, scale=TRUE)
```
```

Figure 7.12 shows the screeplot for the resulting variances attributed to each PC direction. Notice that there are huge drops in variance from 1st to 2nd and 2nd to 3rd PCs. The political science literature finds that a single component is able to explain the vast majority of variation in how politicians vote. A second dimension has been useful to understand voting at a few specific points in time, for example, during the civil war 1860s or during the civil rights battle 1960s when a north versus south (or racist versus less-racist) divide arises across party lines. We can ask the question of our data: “Is there an interpretable second dimension to the political space of 2009 to 2010?”