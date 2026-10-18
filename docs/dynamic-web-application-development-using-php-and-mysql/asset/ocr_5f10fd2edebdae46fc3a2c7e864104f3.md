# FIGURE 17.4 Expanded shape and rectangle classes

![](bbox=[0.42, 0.09, 0.71, 0.38])

Let’s begin by building these two classes. The shape class is going to contain the data members, $intHeight, $intWidth and $strGraphic to store the width, height and graphical image used to represent the shape. The shape class is also going to contain three methods: a constructor, a display() method, which will display the shape, and a resize() method which will allow the shape to be resized. This is illustrated in Figure 17.4.

> **NOTE** Note that we have included the __construct() function in the list because of what we will be doing later. However, to keep things simple we have removed the constructor’s arguments.

In PHP then, our shape class looks like this and should be saved as ‘shape.php’:

```
<?php
// File: shape.php

class shape {
    private $intHeight;
    private $intWidth;
    private $strGraphic;

    function __construct($intHeight, $intWidth, $strGraphic){
        $this->intHeight = $intHeight;
        $this->intWidth = $intWidth;
        $this->strGraphic = $strGraphic;
    }
}
```