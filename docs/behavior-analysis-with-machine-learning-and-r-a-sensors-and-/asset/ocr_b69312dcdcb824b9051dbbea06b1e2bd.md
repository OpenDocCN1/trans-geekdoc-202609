![](bbox=[0.301, 0.091, 0.698, 0.325])

Each trajectory has a different number of video frames. We can get the frame count by inspecting the length of one of the coordinates.

```
# Count how many frames this trajectory has.
length(tr(bounding.box.x))
# [1] 37
```

The first trajectory has 37 frames but on average, they have 10 frames. For our analyses we are going to include only trajectories with a minimum of 10 frames since it may be difficult to extract patterns from shorter paths. Furthermore, we are not going to use the bounding boxes themselves the center point of the box.

At this point, it would be a good idea to plot how the data looks. To do so, I will use the antipaths package (Scharf, 2020) which has a function to animate trajectories! I will not cover the details on how to use the package but the complete code is in the script visualize_fish.R. The output result is in the form of 'index.html' file that contains the interactive animation. For simplicity, I selected 50 and 10 normal and abnormal trajectories (respectively) to be plotted. Figure 10.6 shows the resulting plot. The plot also includes some controls to play, pause, change the speed of the animation, etc.

The 'normal' and 'abnormal' labels were determined by visual inspection by experts. The abnormal cases include events such as predator avoidance and aggressive movements (due to another fish or because of being frightened).