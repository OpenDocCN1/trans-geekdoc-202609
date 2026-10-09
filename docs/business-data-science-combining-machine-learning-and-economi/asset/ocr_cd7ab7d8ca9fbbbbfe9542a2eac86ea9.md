```
> r <- tapply(semavg$y, semavg$dma, function(y) y[2]-y[1])
> d <- semavg[match(names(r), semavg$dma), "d"]
> rbar <- tapply(r,d,mean)
> rbarvar <- tapply(r, d, function(r) var(r)/length(r))
> rbar[2] - rbar[1]
```

1
-0.006586852
> sqrt(sum(rbarvar))
[1] 0.005555082

The results are unchanged from our previous regression analyses.

REGRESSION DISCONTINUITY ESTIMATORS take advantage of another common near-experimental design: treatment allocation is determined by a threshold on some “forcing variable,” and subjects that are close to the threshold, on either side, are comparable for causal estimation purposes. For example, Hahn et al. [1999] evaluate the causal effect of a discrimination law that applies only to firms with more than 15 employees. Here, the number of employees is the forcing variable and the authors compare firms on either side of the 15-employee threshold. Similar situations arise all over the place: grade thresholds determine access to education programs, income thresholds influence availability of social programs, and my kids had free entry at the museum until they turned 4. We’ll consider a common digital marketing setting where the rules for ad display depend upon whether the highest (or second highest) ad auction “score” passes a reserve threshold.

The nice thing about a regression discontinuity (RD) design is that you know the only confounding variable that you need to control for: the forcing variable. Recall our earlier discussion of imperfect experimental designs. You need to control for (i.e., include in the regression) any variable that is correlated with both treatment allocation and the response. In a strict RD, the treatment is *fully determined* by the forcing variable so you just need to control for that variable. In the examples just given, you’d need to control for each firm’s number of employees or each advertiser’s score in the ad auction.