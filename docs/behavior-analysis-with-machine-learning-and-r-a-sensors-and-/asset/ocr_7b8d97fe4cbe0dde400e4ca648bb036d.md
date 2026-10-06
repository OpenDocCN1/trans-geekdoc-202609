![](bbox=[0.118, 0.098, 0.881, 0.211])

Figure 9.2: Skeleton of basketball shoot action. 6 frames sampled from the entire sequence.

```
# Path to one of the files.
filepath <- "/skeleton_actions/a7_s1_t1_skeleton.mat"

# Read skeleton file.
df <- readMat(filepath)$d.skel

# Print dimensions.
dim(df)
#> [1] 20 3 66
```

From the file name, we can see that this corresponds to action 7 (basketball shoot), from subject 1 and trial 1. The readMat() function is used to read the file contents and store them as a 3D array in df. If we print the dimensions we see that the first corresponds to the number of joints, the second are the positions (x, y, z), and the last dimension is the number of frames, in this case 66 frames.

We can extract the first time-frame as follows:

```
# Select the first frame.
frame <- data.frame(df[, , 1])

# Print dimensions.
dim(frame)
#> [1] 20 3
```

Each frame can then be plotted. The plotting code is included in the script. The Figure below shows how the skeleton looks like for 6 of the time frames. The script also has code to play the action as an animation.