The score of each student can be converted to a z-score using the following functions:

```
>>> stats.zscore(classscore)

[ 0.8008868 0.38555699 1.33462036 1.92778497 -1.15667098
-0.02965823
-0.91940514 0.26292407 -0.08897469 0.38555699 -0.20760761
-0.91940514
1.13541056 0.62282284 -0.91940514 -0.32624053 -1.39393683
0.14828115
0.14828115 0.74145657 -0.20760761 0.50418992 -1.27539039
0.68007223
-0.80077216 0.97872161 -0.13038036 -0.44887345 -1.63120267
-1.1566709
2.16505281 0.86008868 -1.63120267 -0.44887345 -0.20760761
-0.08897469 0.50418992 0.14829115 1.45325329
1.33462036
0.97872161 0.50418992 0.86008868 2.28368373 -0.6821393
1.63120267
-0.44887345 -0.80077222 -1.86846851 -0.6821393 0.02965823
0.62282284
-0.44887345 0.62282284 -0.08897469 0.74145657 0.86008868
-2.24385727]
```

In the following case, a student with a score of 60 out of 100 has a z-score of 1.334. To make a lot of sense of it, you'll apply the standard normal table.
This helps in defining the probability of a score.
It is important to know that the probability of acquiring a score above 60 would be:

![](bbox=[0.147, 0.637, 0.533, 0.835])

The standard normal table can allow you to compute the probability of the occurrence of the score, but you do not need to conduct the difficult task of