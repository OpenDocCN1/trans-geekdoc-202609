
# Nearest Neighbours

Let us consider our data set to be of the following format:
tableFunction:([] coord1:"f($);coord2:"f($);coord3:"f($);...; val:"f($));

where we consider n independent variables coord and one dependent variable val. We further assume dependent variables are normalized using the normalization techniques. The feature selection based on neighbours is built as follows:

First, we define the weighted L2-norm, $|x-x'|_w$, as:

```
.quantQ.knn.weightedL2norm:[x;y;weight]
// x, y -- n-dimensional arrays (two points in feature space)
// weight -- n-dimensional array of weights
// t wsum weight*(x-y);
;
```

where $x, y$ are three vectors of the same length, n, and the function returns $|x-y|_w$.

We implement a locator value of the function in the neighbourhood coordinate of a point y, where the neighbourhood is weighted by its proximity to the point using the weighted L2-norm

```
.quantQ.knnMeanFunction:[coordX;coordY;weights;beta]
// coordX -- n-dimensional array (point to make regression)
// coordY -- kn n array, k observations of n-dimensional arrays
// value -- n-dimensional array of dependent variables
// weights -- n-dimensional array of weights
// beta -- parameter of the algorithm
// returns MSE-based code
:(1%sum exp neg (1%beta) * .quantQ.weightedL2norm[coordX;weights]
-- each coordY)*sum
valueY*exp neg (1%beta)* .quantQ.knnL2norm[coordX;weights]
-- each coordY);
;
```

In order to implement the algorithm, we have to implement five special functions which form the basis of the algorithm. First, we implement the error function, $e(w)$, a negative of the mean-squared error of the weighted estimator and unbiased one. The function has the same arguments as the previous KNNMeanFunction.

```
.quantQ.knnError:[coordX;coordY;value;beta]
// coordX -- n-dimensional array (point to make regression)
// coordY -- kn n array, k observations of n-dimensional arrays
// value -- n-dimensional array of dependent variables
// weights -- n-dimensional array of weights
// beta -- parameter of the algorithm
// returns error at local point
// neg 0.5*t*t:(quantQ.knn.KNNMeanFunction[coordX;coordY;value;weights;
-- beta)-
.quantQ.kNNNMeanFunction[coordX;coordY;value](count weight)*1;
-- beta]);
;
```

Let us further define an a function and u function, respectively:

```
.quantQ.knn.aFunc:([coordX;coordXB;coordXbb;beta;weights])
// coordX, coordXB, and coordXbb -- n-dimensional arrays (three points)
// weights -- n-dimensional array of weights
// parameter of the algorithm
// returns aFunc
// exp neg ((quantQ.knn.weightedL2norm([coordX;coordXB;weights]+
// quantQ.knn.weightedL2norm(coordX;coordXbb;weights])%beta);
```

```
.quantQ.knn.uFunc:([coordX;coordXB;coordXbb;weights])
// coordX, coordXB, and coordXbb -- n-dimensional arrays (three points)
// weight -- n-dimensional array of weights
// returns uFunc
:weights*(t:t:(coordX-coordX))+(u:(coordX-coordX)));
```

We can proceed with the gradient of the gradient function, $\nabla_{\hat{\mu}}(x)$:

```
.quantQ.knn.gradFunc:([coordX;coordY;beta;weights]) each
// coordX -- k x n array, k observations of n-dimensional arrays
// valueY -- n-dimensional array of dependent variables
// weights -- n-dimensional array of weights
// parameter of the algorithm
// returns gradient of a function
:[:1%sum([coordY,beta;weights;x]
	{:quantQ.knn.aFunc([coordX[0];coordY[x]];beta;weights]
	)]coordX,coordY,beta;weights])
	t(t till:count coordY))*neg(4%beta*)
sum [valueY[x[1]],
	valueY[x[1]],
		quantQ.knn.aFunc(coordY[0];coordY[1];beta;
		weights*)
		quantQ.knn.uFunc(coordY[0];coordY[1];weights])
	valueY;coordY,beta;weights]; each
	t(t till:count coordY
```

Finally, we construct the gradient of the error, $V(w)$, which we search for features of dependent variables:

```
.quantQ.knn.gradError:([coordFull;weights;beta;fraction])
// coordFull -- k n array, k observations of n-dimensional arrays
// valueFull -- n-dimensional array of dependent variables
// fraction -- relative size of the data used
// knn -- number of neighbours used for regression around point
// weight -- n-dimensional array of weights
// beta -- parameter of the algorithm
dim: count coordFull;
setS: asc(neg(fraction*dim));
```

We combine all above-defined functions in the iterative algorithm to select features following descent approach from data set coordFull and valueFull. The iterative algorithm initializes the weights to 1. The function defines iteration which represents one of the algorithm, one update of weights. The updating is based on the gradient of the error, where the updates are weighted by decaying ratio, driven by learningRatio and decay. The algorithm relies on nearest neighbours and the size of neighbourhood for kNN is given by kNN, k observations as another parameter. Further, the parameter $\beta$ or inverse temperature, is provided as beta. In every iteration, we need to calculate score measure and derivatives. We do not use the full sample for these calculations, but a fraction of the entire set, fractionS. Finally, if we specify list of iterations, nIterations, the algorithm will be wrapped within a dictionary for convenience.

```
.quantQ.knn.KNNFeatureSelection:[bucket]
// bucket -- dictionary with variables of the model
// bucket[coordFull] -- k n array, k observations of n-dimensional arrays
// bucket[valueFull] -- k-dimensional array of dependent variables
// bucket[learningRatio] -- learning ratio
// bucket[decay] -- parameter for decaying learning ratio
// bucket[kNN] -- number of neighbours used for regression around each point
// bucket[beta] -- parameter of the algorithm
// bucket[fractionS] -- relative size of the data used in each
// bucket[nIterations] -- number of iterations
features: count flip bucket[coordFull];
// initiate weights with 1s
weightinit:1.0;
// one-iterationUpdateWeights, defined internally
kNNUpdateWeights:[coordFull;valueFull;learningRatio;decay;kNN;beta;
    // fractionS:bucket;
    // weight*(bucket[weight]+learningRatio*(decay exp bucket[cnt]))
    .quantQ.knn.gradError[coordFull;valueFull;bucket[weight];beta;
        fractionS;kNN];bucket[cnt]+1);
```

# MACHINE LEARNING

```
// loop to iterate the algorithm nIterations times, return outcome
:(kNNUpdateWeights[bucket[`coordFull`];bucket[`valueFull`];bucket[
  learningRatio];
  bucket[`decay`];bucket[`kNN`];bucket[`beta`];bucket[`fractionS`]];
  bucket[`nIterations`];
  weight`cnt`!(weightInit;0));
```

Time to illustrate its usage with an example. We define a data set with three independent variables and one dependent variable:

```
coord1:100;
coord2:100;
coord3:100;
val: (0.2+coord1)+(0.5*coord2)+(100*0.3);
```

The dependent variable val does not depend on variable coord3 while the strongest link is with coord2. Let us next pack the variables in a table:

```
tableFunction:([coord1;coord2;coord3]; val);
```

The kNNfeatureSelection function requires as an input dictionary with number of parameters. Defining the following values:

```
coordFull: flip value exec coord1, coord2, coord3 from tableFunction;
valueFull: exec val from tableFunction;
kNN:5;
learningRatio:0.01;
decay:0.05;
beta:0.5;
fractionS:0.5;
iterations:100;
```

and wrapping them into the dictionary:

```
bucket:(`coordFull`valueFull`kNN`learningRatio`decay`beta`fractionS`
  iterations);
  (coordFull:valueFull;kNN;learningRatio;decay;beta;fractionS;
  iterations);
```

We can explore the outcome:

```
last kNNtab
```

```
(`weight`cnt`!(1.122086 1.209277 1.036502;100j));
```
