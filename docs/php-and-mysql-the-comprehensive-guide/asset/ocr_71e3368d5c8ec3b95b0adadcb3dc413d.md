![](bbox=[0.143, 0.102, 0.856, 0.468])

Figure 31.2 A Text Box with Background Color

# 31.2.3 Lines and Points

PDF as a format also has the ability to create vector graphics and draw shapes and lines using points and styles. We will create a simple example with a self-drawn house. It consists of a rectangle, which we create using the Rect() method, and a triangle that we draw using the Polygon() method.

> > **Note**
> > TCPDF supports a range of other shapes, such as circles with Circle(), lines with Line(), and even Bezier curves with Curve(). It is definitely worth experimenting a little here.

In the following example, we first create the central points for the roof—that is, for the triangle. The third coordinate also forms the top-left-hand corner of the rectangle:

```
$a1 = [105, 60];
$a2 = [200, 140];
$a3 = [10, 140];
```

This is followed by a central variable with an array. This array in turn contains index-value combinations for the line style. These include the thickness of the line (width), the