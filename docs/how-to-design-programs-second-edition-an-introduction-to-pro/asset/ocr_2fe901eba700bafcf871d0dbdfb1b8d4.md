+   overlay places all the images to which it is applied on top of each other, using the center as anchor point;

+   overlay/xy is like overlay but accepts two numbers—x and y—between two image arguments. It shifts the second image by x pixels to the right and y pixels down—all with respect to the first image's top-left corner; unsurprisingly, a negative x shifts the image to the left and a negative y up; and

+   overlay/align is like overlay but accepts two strings that shift the anchor point(s) to other parts of the rectangles. There are nine different positions overall; experiment with all possibilities!

The 2htdp/image library comes with many other primitive functions for combining images. As you get familiar with image processing, you will want to read up on those. For now, we introduce three more because they are important for creating animated scenes and images for games:

+   empty-scene creates a rectangle of some given width and height;

+   place-image places an image into a scene at a specified position. If the image doesn't fit into the given scene, it is appropriately cropped;

+   scene+line consumes a scene, four numbers, and a color to draw a line into the given image. Experiment with it to see how it works.

The laws of arithmetic for images are analogous to those for numbers; see figure 10 for some examples and a comparison with numeric arithmetic. Again, no image gets destroyed or changed. Like +, these primitives just make up new images that combine the given ones in some manner.