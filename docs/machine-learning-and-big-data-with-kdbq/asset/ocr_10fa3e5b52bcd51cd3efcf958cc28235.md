# Linear Regression with Regularisation

```
// update r
r-=sum step+betaDir*xS;
// update beta
beta+=step+betaDir;
// update path
path,([ step:1+last path[`step`];beta: enlist beta)
// new direction
// new set of variables
betaUsed:newDir:quant betaUsed or corNewWhere;
// new direction
newDir:quantQ.ols.fit[y;x where betaUsed[`beta`];
// normalize by L1 to make steps comparable
newDir:newDir%(sum abs newDir)
// new direction
betaDir:([beataUsed]w0);
betaDir([where i=betaUsed]:newDir;
// update r
r-=sum step+betaDir*xS;
// update beta
beta+=step+betaDir;
// update path
path,([ step:1+last path[`step`];beta: enlist beta)
]
];
];
// step 2++, there is no space for improvement
$(1(count path) and (1-prd betaUsed)
[
// correlation with existing direction
corDir: abs cor[r;sum betaDir*xS];
$[corThrcorDir;
// stop the algorithm
continue:;
// continue algorithm
[
// update r
r-=sum step+betaDir*xS;
// update beta
beta+=step+betaDir;
// update path
path,([ step:1+last path[`step`];beta: enlist beta)
]
];
];
// update bucket
bucket[`beta`]:beta;
bucket[`betaUsed`]:betaUsed;
bucket[`betaDir`]:betaDir;
bucket[`r`]:r;

```