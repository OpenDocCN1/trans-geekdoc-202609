# Nearest Neighbours 433

```
// returns gradient of error at given weights
:neg sum([coordFull;valueFull;weights;beta;i;kNN]
coordX:coordFull[i]
valueX:valueFull[i]
dim: coordFull
vecDist:quantQ.knn.weightedL2norm[coordFull[i];weights] each
    coordFull;
    neighbourhood:where vecDist<=first (kNN-1)_(asc vecDist))
        x1:coordFull[neighbourhood]
        y1:valueFull[neighbourhood]
        .quantQ.knn.gradfunc(coordX;x1;y1;weights)**(valueX-
            .quantQ.knn.meanFunction(coordX,x1,y1,weights));
}[coordFull;valueFull;weights;beta;kNN]
```

We combine all above-defined functions in the iterative algorithm to select the features following the descent approach from data set coordFull and valueFull. The iterative algorithm initializes the weights to 1. The function defines iteration which represents one of the algorithm, one update of weights. The updating is based on the gradient of the error, where the updates are weighted by the decaying ratio, driven by learningRatio and decay. The algorithm relies on nearest neighbours and the size of the neighbourhood used for kNN is given by kNN, k observations as another parameter. Further, the parameter β or inverse temperature, is provided as beta. In every iteration, we need to calculate the properties of score measure and the derivatives. We do not use the full sample for these calculations, but a fraction of the entire set, fractionS. Finally, if we specify the list of iterations, nIterations, the algorithm will be wrapped within a dictionary for convenience.

```
.quantQ.knn.KNNFeatureSelection:[bucket]
// bucket -- dictionary with variables of the model
// bucket[coordFull] -- k n array, k observations of n-dimensional arrays
// bucket[valueFull] -- k-dimensional array of dependent variables
// bucket[learningRatio] -- learning ratio
// bucket[decay] -- parameter for decaying learning ratio
// bucket[kNN] -- number of nearest neighbours used for regression
// around each point
// bucket[beta] -- parameter of the algorithm
// bucket[fractionS] -- relative size of the data used in each
// bucket[nIterations] -- number of iterations
features: count flip bucket[coordFull];
// initiate weights with 1s
weightinit:nFeatures=1.0;
// one-iterationUpdateWeights, defined internally
kNNUpdateWeights:[coordFull;valueFull;learningRatio;decay;kNN;beta;
    // fractionS:bucket;
    // weight*cnt[bucket[weight]+learningRatio*(decay exp bucket[cnt
        ])]
    .quantQ.knn.gradError[coordFull;valueFull;bucket[weight];beta;
        fractionS;kNN];bucket[cnt]+1);
```