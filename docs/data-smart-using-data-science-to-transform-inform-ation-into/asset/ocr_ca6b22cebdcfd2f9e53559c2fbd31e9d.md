In the second drop-down to the left, select “not between.” In the two field boxes to the right, select the upper and lower bounds of the inner fence (D5 and D6, respectively). Because this is the lesser of the bounds, I chose a lighter-shaded red (officially, Excel calls it Red, Accent 2, Lighter 80%). Go ahead and do the same thing for the outer fence. For this, I chose a darker red.

![](bbox=[0.142, 0.23, 0.642, 0.5])

# Figure 10.2: Adding conditional formatting for outliers

As shown in Figure 10.3, Mrs. Hadlum turns red, meaning her pregnancy was radically extreme. Scrolling down, you’ll find no other dark red pregnancies, but there are nine light reds. This matches up closely with the roughly 1 out of 100 points you’d expect to be flagged in normal data by the rule.

| A | B | C | D | E |
|---|---|---|---|---|
| Birth Duration | | Median | 267 | |
| 349 | | 1st Quartile | 260 | |
| 278 | | 3rd Quartile | 272 | |
| 266 | | Interquartile Range | 12 | |
| 265 | | Lower Inner Fence | 242 | |
| 269 | | Upper Inner Fence | 290 | |
| 263 | | Lower Outer Fence | 224 | |
| 278 | | Upper Outer Fence | 308 | |
| 257 | | | | |
| 268 | | | | |
| 260 | | | | |
| 272 | | | | |
| 265 | | | | |

# Figure 10.3: Birth duration with conditional formatting color codes