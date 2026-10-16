
go = `{'nb' : nb_go, 'knn': knn_go}[which_go]`

sd = `split_data(datasets.load_iris())`

`msr(go, sd)`

With all this excitement, let's see where we end up using Naive Bayes:

```
!python scripts/perf_01.py mem nb

!python scripts/perf_01.py time nb
```

`nb_go`: ~0.1445 MiB
`nb_go`: ~0.1004 sec

And with k-NN:

```
!python scripts/perf_01.py mem knn

!python scripts/perf_01.py time knn
```
