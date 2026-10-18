```
$objRectangle->resize(50,100);
$objRectangle->display();

$objSquare = new square(100, "square.gif");
$objSquare->display();

$objTriangle = new triangle(50,100, "triangle.gif");
$objTriangle->display();

$objEllipse = new ellipse(50,100, "ellipse.gif");
$objEllipse->display();
$objEllipse->resize(100,50);
$objEllipse->display();
?>
```

In addition to creating our square and rectangle and displaying those as before the script creates and displays a triangle:

```
$objTriangle = new triangle(50,100, "triangle.gif");
$objTriangle->display();
```

It then creates an ellipse, displays it, resizes it and displays it again:

```
$objEllipse = new ellipse(50,100, "ellipse.gif");
$objEllipse->display();
$objEllipse->resize(100,50);
$objEllipse->display();
```

# FIGURE 17.9 Triangle and ellipse classes

![](bbox=[0.2, 0.62, 0.95, 0.92])