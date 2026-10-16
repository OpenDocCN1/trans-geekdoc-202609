```
```python
# compute PCA
pca = decomposition.PCA()
P = pca.fit_transform(centered_data)

# extract useful bits for drawing
directions = pca.components_
lengths = pca.explained_variance_
print("Lengths:", lengths)
var_wgt_prindirs = -np.diag(1engths).dot(directions)
  # negate to point up/right

# draw principal axes
sane_quiver(var_wgt_prindirs, ax, origin=np.mean(data,axis=0), colors='r')
ax.set_xlim(0,10)
ax.set_ylim(0,10)
ax.set_aspect('equal')
```
```

Lengths: [5.6067 1.2683]

![](bbox=[0.25, 0.48, 0.7, 0.82])

That wasn’t too bad. If we tilt our heads—or our pages or screens—so that the axes are pointing left-right and up-down, all of a sudden, we’ve translated our data from an arbitrary orientation to a standard grid relative to the red arrows. We’ll get to performing that last step—without tilting our heads—shortly. I’d like to take a moment and talk about the covariance of the results. In the process, I’ll explain why I choose to draw the data axes with the lengths of explained_variance. As a warm-up, remember that the