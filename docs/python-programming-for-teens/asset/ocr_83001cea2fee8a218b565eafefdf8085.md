```
# Delay drawing if level is greater than 6.
if level > 6:
    tracer(False)
mondrian(-paintingWidth, paintingHeight,
    paintingWidth, -paintingHeight, level)
# Draw now if level is greater than 6.
if level > 6:
    update()
```

# The tracer and update Functions

Note that you call the tracer function before calling the mondrian function, if the level is greater than 6. When called with an argument of False, the tracer function delays any drawing until the update function is called. The update function is called in the matching if statement after the mondrian function finishes. In between, the turtle still does all the computations for the drawing in the mondrian function, but no output occurs until update is called. If you did not do this for large levels, it would take a long time to draw all the rectangles in the figure.

Generally, input and output operations are much slower than other computations, which occur at the speed of light within the CPU. But despite this move to speed up the output, even the internal computations are not fast enough to prevent considerable delays, as the size of the level grows quite large.

Just how large is this rate of growth in the mondrian function? Table 7.1 shows the number of calls of the mondrian function and the number of rectangles drawn for levels 1 through 5.

Table 7.1 Performance Statistics of the mondrian Function

| Level | Number of Rectangles | Number of Calls |
|---|---|---|
| 1 | 1 | 3 |
| 2 | 3 | 7 |
| 3 | 7 | 15 |
| 4 | 15 | 31 |
| 5 | 31 | 63 |
| N | 2^N-1 | 2^(N+1)-1 |