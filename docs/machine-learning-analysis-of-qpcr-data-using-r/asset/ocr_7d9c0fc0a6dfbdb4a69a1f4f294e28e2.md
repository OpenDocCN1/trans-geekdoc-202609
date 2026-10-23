# Listing 3.11

```
pred_prob = predict(mod, validation, type = "probabilities")
prediction = predict(mod, validation)
serial = validation$Index
rating = validation$Outcome
classified = data.frame(Serial = serial, Class = prediction, MR = validation$MR,
    FCN = validation$FCN, stringsAsFactors = FALSE)
split.screen(c(2, 1))
split.screen(c(1, 4), screen = 2)
screen(1)
plot(classified$MR[classified$Class == "positive"] ~ classified$FCN[classified$Class == "positive"],
    cex=1.5, pch=16, xlim=c(0.50), ylim=c(0,0.45), xlab=expression(bold("FCN")),
    ylab=expression(bold("MR")))
points(classified$MR[classified$Class == "negative"] ~ classified$FCN[classified$Class == "negative"],
    cex=1.5, pch=1)
points(classified$MR[classified$Serial == 171] ~ classified$FCN[classified$Serial == 171], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 71] ~ classified$FCN[classified$Serial == 71], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 148] ~ classified$FCN[classified$Serial == 148], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 80] ~ classified$FCN[classified$Serial == 80], cex=2.5,
    pch=0, lwd=2)
text(classified$FCN[classified$Serial == 171]-1, 0.02, 171)
text(classified$FCN[classified$Serial == 71]+0.3, 0.02, 71)
text(classified$FCN[classified$Serial == 148]+1, 0.02, 148)
text(classified$FCN[classified$Serial == 80], 0.02, 80)
points(classified$MR[classified$Serial == 4] ~ classified$FCN[classified$Serial == 4], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 10] ~ classified$FCN[classified$Serial == 10], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 76] ~ classified$FCN[classified$Serial == 76], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 117] ~ classified$FCN[classified$Serial == 117], cex=2.5,
    pch=0, lwd=2)
text(classified$FCN[classified$Serial == 4], 0.01, 4)
text(classified$FCN[classified$Serial == 10], 0.05, 10)
text(classified$FCN[classified$Serial == 76], 0.1, 76)
text(classified$FCN[classified$Serial == 117], 0.04, 117)
points(classified$MR[classified$Serial == 128] ~ classified$FCN[classified$Serial == 128], cex=2.5,
    pch=0, lwd=2)
```