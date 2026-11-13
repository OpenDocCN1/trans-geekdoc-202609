```
$ fy..MPa. : num 302 302 338 338 288 ...
$ fc..Mpa. : num 18.2 34.7 37.1 34.1 27 33.3 33.3 33.4 33.4 27.9 ...
$ N.Test...kN. : num 1326 1219 1308 1330 1557 ...
...
```

```
#Displaying the first six rows of the dataset
head(data)
D..mm. t..mm. L..mm. fy..MPa. fc..Mpa. N.Test..kN.
1 168.8 2.64 305 302.4 18.2 1326
2 168.8 2.64 305 302.4 34.7 1219
3 169.3 2.62 305 338.1 37.1 1308
4 169.3 2.62 305 338.1 34.1 1330
5 168.3 3.60 305 288.4 27.0 1557
6 168.3 3.60 305 288.4 33.3
summary(data)
D..mm. t..mm. 1432
L..mm.
fy..MPa.
Min. : 44.45 Min. : 0.520 Min. : 152.3 Min. :178.3
1st Qu.: 108.00 1st Qu.: 2.703 1st Qu.: 399.0 1st Qu.:274.9
Median : 129.00 Median : 4.000 Median : 662.0 Median :324.7
Mean : 158.83 Mean : 4.275 Mean :1055.1 Mean :335.7
3rd Qu.: 190.00 3rd Qu.: 5.000 3rd Qu.:1200.0 3rd Qu.:363.3
Max. :1020.00 Max. :16.540 Max. :5560.0 Max. :853.0
fc..Mpa. N.Test..kN.
Min. : 7.59 Min. : 45.2
1st Qu.: 29.15 1st Qu.: 710.8
Median : 37.40 Median : 1273.0
Mean : 47.50 Mean : 2349.7
3rd Qu.: 51.08 3rd Qu.: 2273.2
Max. :185.94 Max. :46000.0
```

```
#Selecting a train-test split
smp_size <- floor(0.8 * nrow(data))
```

```
#Partitioning data and setting the seeds for reproducibility
set.seed(123)
train_ind <- sample(seq_len(nrow(data)), size = smp_size)
trainrf <- data[train_ind, ]
testrf <- data[-train_ind, ]
```

```
#Fitting the algorithm
set.seed(187)
rf.mod <- randomForest(N.Test...kN.~.,ntree=100,mtry=5, data=trainrf)
plot(rf.mod)
```