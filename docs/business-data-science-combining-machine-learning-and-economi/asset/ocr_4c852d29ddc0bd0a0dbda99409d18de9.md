but since I wrote the gamlr software, it has the advantage of providing for special features covered in this book (e.g., corrected AIC and distributed multinomial regression).

The glimnet package is also an excellent option for lasso estimation. Both gamlr and glimnet use similar syntax and use similar optimization routines (coordinate descent). The difference is in what they can do beyond the lasso: gamlr offers diminishing bias penalization, like the log penalty in Figure 3.4 (see also Figure 3.7), while glimnet provides for the elastic net of that same figure.

![](bbox=[0.31, 0.27, 0.77, 0.56])

FIGURE 3.7: As an aside, gamlr can execute a forward-stepwise subset-selection procedure. Figure 3.8 shows the corresponding path plot for the browser data; notice how the jagged solution paths in this figure contrast with the smooth lasso paths of Figure 3.6. This discontinuity in the solution paths is the source of instability in subset selection.

Running a lasso in gamlr is easy. The main difference from glm is that you need to create the numeric model-matrix yourself. But once you have this—say, xweb for the browser data—gamlr will by default run an entire path.

```
```python
> sp <- gamlr(xweb, log(yspend))
> sp
```
```

```
```python
gaussian gamlr with 1,000 inputs and 100 segments.
```
```