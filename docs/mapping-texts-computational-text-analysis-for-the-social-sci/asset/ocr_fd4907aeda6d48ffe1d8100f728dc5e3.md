```
mat
```

Below `cbind()` creates `matrix` , but now it's `character` as that is the type encompassing both numbers and words (output in margin).

```
d4 <- c(0, 4, 2)
d5 <- c("space", "is", "big")
mat2 <- cbind(d4, d5)
typeof(mat2)
```

We can tell because double quotes surround each element. When we use `data.frame()` , though, one column is `numeric` , and the other is `character` , creating an object of class `data.frame` . Technically, a `data.frame` is a set of (vertical) lists of the same length. Each list retains its data type.

```
cbind(mat2)
```

```
data.frame(d4, d5)
```

To help us navigate these objects, whenever we have a `named` list or dataframe, we can use the `$` operator to call that element by name. Let's create a list

```
lrrs_list <- list(first = "fireman",
                  second = "math teachers",
                  third = "and so on in that fashion")
names(lrrs_list)
```

```
[1] "first" "second" "third"
```

To access the element named `third` , we would:

```
lrrs_list$third
```

```
[1] "and so on in that fashion"
```

Most data structures we encounter are variations on the above. Specifically, objects can be within other objects: for example, a list where the elements are lists (or even lists of lists of lists, and so on in that fashion).

# # Dialects of R

There are two `dialects` of `R` which we label *nesting* and *chaining*.11

+   *   Nesting: An object is transformed by an inner function, then sent to the next outward function.
+   *   Chaining: An object is transformed by a function, then sent to the next right function.

```
 c1 c2
[1,] 1.2 0
[2,] 2.8 4
[3,] 3.0 2
```

```
[1] "character"
```

```
   d4 d5
[1,] "0" "space"
[2,] "4" "is"
[3,] "2" "big"
```

```
  d4  d5
1  0 space
2  4 is
3  2 big
```