# 16.1 Existing Abstractions

ISL provides a number of abstract functions for processing natural numbers and lists. Figure 95 collects the header material for the most important ones. The first one processes natural numbers and builds lists:

```
> (build-list 3 add1)
(list 1 2 3)
```

The next three process lists and produce lists:

```
> (filter odd? (list 1 2 3 4 5))
(list 1 3 5)
> (sort (list 3 2 1 4 5) >)
(list 5 4 3 2 1)
> (map add1 (list 1 2 2 3 3 3))
(list 2 3 3 4 4 4)
```

In contrast, andmap and ormap reduce lists to a Boolean:

```
> (andmap odd? (list 1 2 3 4 5))
#false
> (ormap odd? (list 1 2 3 4 5))
#true
```