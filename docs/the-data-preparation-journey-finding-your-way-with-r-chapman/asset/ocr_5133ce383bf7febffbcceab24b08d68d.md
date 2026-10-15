```
ls.str(jcush_haven)
```

```
## GHJIDHDI :  num [1:8688] 3 3 2 3 2 4 2 4 0 2 ...
## health_desc_lab :  dbl+lbl [1:8688] 3, 3, 2, 3, 2, 4, 2, 4, 0, 2, 4, 4, 4, 2, 2, 2, 1, 4...
## SAMPLEID :  chr [1:8688] "10003330835" "100004903392" "10010137168" ...
## SDJIGHD :  num [1:8688] 4 2 1 3 2 3 2 1 3 2 ...
## SPJ1_TYP :  num [1:8688] 1 1 1 1 1 1 1 1 1 ...
```

# FIGURE 12.5 ls.str(jcush_haven).

The levels() function can be used to inspect the result of this mutate.

```
head(jcush_haven$health_desc_lab)
```

```
## Found more than one class "haven_labelled" in cache; using the first,
##  from namespace 'memisc'

## Also defined by 'haven'

## Found more than one class "haven_labelled" in cache; using the first,
##  from namespace 'memisc'

## Also defined by 'haven'

## <labelled<double>[6]>
## [1] 3 3 2 3 2 4
##
## Labels:
##   value    label
##     0    Poor
##     1    Fair
##     2    Good
##     3  Very Good
##     4  Excellent
##     9 Not Stated
```

A third option is to use the functions within the {labelled} package (Lamarange, 2022).