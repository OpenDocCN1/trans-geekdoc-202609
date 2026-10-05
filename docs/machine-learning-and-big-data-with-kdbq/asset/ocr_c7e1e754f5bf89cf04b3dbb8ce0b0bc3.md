# Trees 489

```
enlist[r],$98<h>type r::quant.trees.growTree[xy;r] raze @[rr;
  where 99h=type each r;enlist];rr
]}each r::quant.trees.chooseSplit[xy;treeinput]
);
```

We can learn a tree: for each of the records in the initial split, we iterate
 reach pure nodes (leaves) or until the maximum specified level (maxdepth key)
is reached. When we reach a leaf, we return a flattened result and then recurse over
t next split record until there are none left. The flattened tree should contain all the
paths and a tree-like structure with all indices i parents. The provided function
acts as an input with the index of the predictor, its indices i and j, the
in gain, and four parameters which are carried through:

```
-quant.trees.learnTree[:params]
// params dictionary with parameters for learning the tree
// m number of features to randomly select defaults to all features
// maxdepth maximum depth of tree if pure nodes not reached defaults
// to 100
params[m]: [$m in key params;m;count params`]
params[maxdepth]: [$maxdepth in key params;params`maxdepth;100];
r0: ofinfoains xij`jofain bitmap`X appliedrule`rulepath
  classes`m`maxdepth
params,
infoains xij`jofain bitmap`appliedrule`rulepath(!(();ON;0N;0n
  ;count [params`y]wB;::(());));
tree: enlist[r0];
[$98<>type r::quant.trees.growTree;r0:dc`x`y`classes`m
  maxdepth`r
raze @[r,99h=type each r;enlist];
r;
tree: update p:(x'-_l) rulepath from tree;
  :'ip`path xcols update path:(x scan)each till x}p,i:i from tree;
);
```

We will now create a dictionary of the parameters we need to fit, or learn the tree:

dataset!();
daset[x]:value flip delete from iris;
daset[y]:[distinct[x?] iris[`class];
params:dataset,`rule classes!(asc distinct dataset`y);

View your features:

```
flip params`x
```

```
5.1 3.5 1.4 0.2
4.9 3 1.4 0.2
4.7 3.2 1.3 0.2
4.6 3.1 1.5 0.2
5 3.6 1.4 0.2
5.4 3.9 1.7 0.4
5 3.4 1.5 0.2
4.4 2.9 1.4 0.2
```