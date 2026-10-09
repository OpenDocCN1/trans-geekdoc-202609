As an introductory example, recall the NBC data from Chapter 7. Instead of looking at the pilot surveys, we'll instead look at predicting the show genre (comedy, reality, or drama) from the viewer demographics. These demographics include percent of viewership for each show that falls in a number of categories defined by region, race, and how the household consumes TV.

```
```
> nbc <- read.csv("nbc_showdetails.csv")
> genre <- nbc$Genre
> demos <- read.csv("nbc_demographics.csv", row.names=1)
> round(demos[1:4, 11:17])

           WIRED.CABLE.W.PAY WIRED.CABLE.W.0.PAY DBS.OWNER
Living with Ed             36                   44        20
Monarch Cove               31                   40        29
Top Chef                   43                   34        23
Iron Chef America          44                   30        26

         BROADCAST.ONLY VIDEO.GAME.OWNER DVD.OWNER VCR.OWNER
Living with Ed             0                66          98        90
Monarch Cove               0                55          94        74
Top Chef                   0                51          92        78
Iron Chef America          0                57          94        84
```
```

For illustration, we allow CART to split down to single-show leaves.

```
```
> genretree <- tree(genre ~ ., data=demos, mincut=1)
> genretree
node), split, n, deviance, yval, (yprob)
* denotes terminal node
```
```