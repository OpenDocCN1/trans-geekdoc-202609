# Unsupervised Machine Learning: The Apriori Algorithm

```
colDummiesStepPrevX();
// counter of the steps within the iteration
step:0;
// candidate dummy variables
colDummiesStep1();
// control variable for improvement being possible
canImprove:ib;
```

Further, we explicitly define the global acceptance threshold of the Apriori algorithm. We choose 0.2 for example:

thresh:0.2;

```
bucketParams((`largeTabDummiescolDummiesStepALLcolDummiesStepALLX`
colDummiesStepPrev `colDummiesStepPrevX `step `colDummiesStep1
canImprove`threshold`)(`largeTabDummies;colDummiesStepALL;
colDummiesStepALLX;colDummiesStepPrev;colDummiesStepPrevX;step;
colDummiesStep1;canImprove;threshold));
```

Let us stress that the bucket contains also the data in its wide form. We run the iteration of the algorithm manually:

```
bucketParams:quant.apriori.aprioriRun[bucketParams];
```

The set of accepted combinations contains individual values after the first step singlets, i.e. the algorithm has chosen individual values which are frequent enough:

```
bucketParams[`colDummiesStepALL`]
```

```
enlist `a1_0;`enlist `a1_1;`enlist `a1_2;`enlist `a1_3;`enlist
`a2_0;`enlist `a2_1;`enlist `a2_2;`enlist `a3_0;`enlist
`a3_1;`enlist `a3_2;`enlist `a4_0;`enlist `a4_1;`enlist `a5_0
`;`enlist `a5_1;`)
```

The algorithm performed the first step:

```
bucketParams[`step`]
```

```
1j
```

and shows that after first iteration, it can run further and improve:

```
bucketParams[`canImprove`]
```

```
1b
```

Let us know another step:

```
bucketParams:quant.apriori.aprioriRun[bucketParams];
```

The set of accepted combinations contains, on top of the singlets, also pairs of frequent combinations:

```
bucketParams[`colDummiesStepALL`]
```