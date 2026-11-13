# # 1.4 The Arithmetic of Images

An Image is a visual, rectangular piece of data, for example, a photo or a geometric figure and its frame. You can insert images in DrRacket wherever you can write down an expression because images are values, just like numbers and strings.

> Remember to require the 2htdp/image library in a new tab.

Your programs can also manipulate images with primitive operations. These primitive operations come in three flavors. The first kind concerns the creation of basic images:

+   * circle produces a circle image from a radius, a mode string, and a color string;
+   * ellipse produces an ellipse from two radii, a mode string, and a color string;
+   * line produces a line from two points and a color string;
+   * rectangle produces a rectangle from a width, a height, a mode string, and a color string;
+   * text produces a text image from a string, a font size, and a color string; and
+   * triangle produces an upward-pointing equilateral triangle from a size, a mode string, and a color string.

The names of these operations mostly explain what kind of image they create. All you must know is that mode strings means "solid" or "outline", and color strings are strings such as "orange", "black", and so on.

Play with these operations in the interactions window: