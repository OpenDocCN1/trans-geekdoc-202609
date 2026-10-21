form:

```
repeat {
    find line;
    eliminate support;
}
until no data points remain;
```

As outlined above, RANSAC involves quite considerable computational load—amounting to O(N³)—which should be compared with O(N) for the HT. Hence it is better to reduce N in some way when using RANSAC. This explains why it is useful to concentrate on the local maxima rather than employing the full list of edge points. However, an alternative is to employ repeated random sampling from the full list until sufficient hypotheses have been tested to be confident that all significant lines have been detected. [Note that these ideas reflect the original meaning of the term RANSAC, which stands for RANdom SAmpling Consensus—"consensus" indicating that any hypothesis has to form a consensus with the available support data (Fischler and Bolles, 1981).] Confidence that all significant lines have been detected can be obtained by estimating the risk that a significant line will be missed because no representative pair of points lying on the line was considered.

We are now in a position to consider results obtained by applying RANSAC to a particular case of straight line detection. In the test described, pairs of points were employed as hypotheses, and all edge points were local maxima of the intensity gradient. The case shown in Fig. 1.12 corresponds to detection of a block of wood in the shape of an icosahedron. Note that one line on the right of Fig. 1.12(a) was missed because a lower limit had to be placed on the level of support for each line: this was necessary because below this level of support the number of chance collinearities rose dramatically even for the relatively small number of edge points shown in Fig. 1.12(b), leading to a sharp rise in the number of false positive lines. Overall, this example shows that RANSAC is a highly important contender for location of straight lines in digital images. Not discussed here is the fact that RANSAC is useful for obtaining robust fits to many other types of shape, in 2-D and in 3-D.

Finally, it should be mentioned that RANSAC is less influenced than the HT by aliasing along straight lines. This is because HT peaks tend to be fragmented by aliasing, so the best hypotheses can be difficult to obtain without drastic smoothing of the image. The reason why RANSAC wins in this context is that it does not rely on individual hypotheses being accurate: rather it relies on enough hypotheses easily being generatable, and by the same token, discardable.

# 1.3.5 A graph-theoretic approach to object location

This section considers a commonly occurring situation involving considerable constraints—objects appearing on a horizontal worktable or conveyor at a known distance from the camera. It is also assumed (a) that objects are flat or can appear in only a restricted number of stances in three dimensions, (b) that objects are viewed from directly overhead, and (c) that perspective distortions are small. In such situations the objects may in principle be