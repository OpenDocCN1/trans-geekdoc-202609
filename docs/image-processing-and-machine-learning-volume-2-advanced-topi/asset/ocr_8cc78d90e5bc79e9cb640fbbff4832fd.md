# 3.1 Coordinate Transformation

The transformation carried out by Equation 3.3 is fundamentally a function, which can be divided into two independent functions, such that:

```
x' = T_x(x, y) \text{ and } y' = T_y(x, y) (3.4)
```

# 3.1.1 Simple Transformations

Simple transformations include displacement, scaling, skewing, and rotation [3].

# 3.1.1.1 Displacement

Also known as a translation, it allows to shift an image by defining a displacement vector (dx, dy), such that:

```
Tx: x' = x + dx
Ty: y' = y + dy (3.5)

[ x' ]   [ x ]   [ dx ]
[    ] = [   ] + [    ]
[ y' ]   [ y ]   [ dy ]
```

# 3.1.1.2 Scaling

Either in the direction x (sx) or y (sy) it allows to increase or contract the space occupied by the rectangular array of the image, such that:

```
Tx: x' = x * sx
Ty: y' = y * sy (3.6)

[ x' ]   [ sx 0 ] [ x ]
[    ] = [      ] [   ]
[ y' ]   [ 0 sy ] [ y ]
```

# 3.1.1.3 Inclination

Either in the x (bx) or y (by) direction, it allows tilting the space occupied by the rectangular array of the image (in tilting, only one direction should be considered while the other remains zero), such that: