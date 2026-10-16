# 13.3.2 Finding a Different Best Line

It might seem obvious (or not!) but when we performed linear regression in Section 4.3, we dealt with differences between our line and the data in one direction: vertical. We assumed that all of the error was in our prediction of the target value. But what if there is error or randomness in the inputs? That means, instead of calculating our error up and down, we would need to account for both a vertical and a horizontal component in our distance from the best-fitting line. Let's take a look at some pictures.

```
In [56]:
fig, axes = plt.subplots(1,3,figsize=(9,3), sharex=True,sharey=True)
xs = np.linspace(0,6,30)
lines = [(1,0), (0,3), (-1,6)]
data = np.array([[1, 2, 4, 5],
                [2.5,.75,5.25,3.5]]).T
plot_lines_and_projections(axes, lines, data, xs)
```

![](bbox=[0.13, 0.52, 0.85, 0.65])

I've drawn three yellow lines (from left to right sloping up, horizontal, and down) and connected our small red data points to the yellow line. They connect with the yellow line at their respective blue dots. More technically, we say that we project the red dots to the blue dots. The solid blue lines represent the distances from a red dot to a blue dot. The dashed blue lines represent the distances from a red point to the mean, which is the larger black dot. The distance between a blue dot and the mean is a portion of the yellow line. Unless a red dot happens to fall directly on the yellow line, it will be closer to the mean when we project it onto its blue companion. Don't believe me? Look at it as a right triangle (using Y for yellow and B for blue): Y² + B²_solid = B²_dashed. The yellow piece has to be smaller—unless red happens to be on the yellow line.

There are lots of yellow lines I could have drawn. To cut down on the possibilities, I drew them all through the mean. The yellow lines I've drawn show off a fundamental tradeoff of any yellow line we could draw. Consider two aspects of these graphs: (1) how spread-out are the blue dots on the yellow line and (2) what is the total distance of the red points from the yellow line. We won't prove it—we could, if we wanted—but the yellow line that has the most spread-out blue dots is also the one that has the shortest total distance from the red points. In more technical terms, we might say that the line that leads to the maximum variance in the blue points is also the line with the lowest error from the red points.