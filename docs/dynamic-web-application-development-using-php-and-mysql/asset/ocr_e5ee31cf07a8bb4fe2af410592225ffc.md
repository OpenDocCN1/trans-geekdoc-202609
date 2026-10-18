The output from the above script is illustrated in Figure 17.10.

We have now reached the stage where we have an inheritance structure consisting of four different shapes. It is now time to add a new method, one which is able to calculate the area of the shape in question. We cannot simply include a single method in the shape class as the formula to calculate a shape’s area differs from shape to shape. We are going to have to include a method for each of our shapes. Table 17.1 lists the formulae for calculating the area of our shapes.

# FIGURE 17.10 — Triangles, ellipses and more

![](bbox=[0.084, 0.261, 0.782, 0.731])

# TABLE 17.1 — Shape area calculations

| Shape | Formula | Code |
|---|---|---|
| Rectangle | Width * Height | `$intArea = $intWidth * $intHeight;` |
| Square | As for rectangle | Can inherit from rectangle |
| Triangle | Width * Height/2 | `$intArea = $intWidth * $intHeight/2;` |
| Ellipse | π * Width/2 * Height/2 | `round(Pi() * ($intWidth/2) * ($intHeight/2));` |