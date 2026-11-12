![](bbox=[0.24, 0.115, 0.84, 0.52])

**FIGURE 1.28**
Object labeling results when considering different neighborhood criteria. (a) Result when it is considered a 4-connected neighborhood and (b) result when it is considered the 8-connected neighborhood.

objects found when the 4-connected neighborhood is used, while Figure 1.28b shows the result when the criterion used is 8-connected. As can be seen from both figures, it is clear that when the 4-connected criterion is used, there will be more objects since the connection criterion between objects will be more restrictive. On the other hand, in the case of 8-connected, the neighborhood criterion presents more flexibility, being able to absorb pixels and consider two objects as one.

MATLAB's image processing toolbox has the bwlabel function, which labels the detected elements with certain connectivity in an image. The syntax of this function is:

```
[L, num]=bwlabel(I, con);
```

where I is a binary image that contains the identified objects to be labeled. con specifies the type of neighborhood criterion considered (4 or 8). L is an array that contains the labeled elements, while num (this parameter is optional) specifies the number of objects contained in the image. If the value