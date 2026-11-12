![](bbox=[0.203, 0.123, 0.792, 0.425])

**FIGURE 1.29** Result of the application of the `bwlabel` function for the labeling of objects. (a) Original binary image from which we want to detect the objects, (b) result of using $L=1$, (c) result of using $L=2$, and (d) result of using $L=3$.

of `con` is omitted, the default connectivity of 8-connected is considered. The objects contained in `L` are labeled from one to the number of the object found $n$.

If Figure 1.29a is considered the binary image to be labeled, the result of applying the `bwlabel` function is three different objects or labels. To select each of the contained labels, a logic function can be used that allows obtaining the label in question. For example, to select label 2, we consider the following commands:

```
```
L=bwlabel(I, 4);
L2=L==2;
```
```

After these commands, it is possible to observe the image shown in Figure 1.29c.

# ## Notes

+   1. It is called the reference point because it is not necessarily the center, unlike the coefficient matrix of a filter.
+   2. Invariant to rotation.