We get the preprocessed red channel on the right:

![](bbox=[0.155, 0.152, 0.843, 0.423])

Similarly, we can process the other two channels. Based on these three channels, how can we construct the feature space? Discarding any channel might result in loss of information. Simply stacking them up could lead to redundancy. So, combining three channels into one would be a better solution. In the color world, Y'UV is an encoding system that encrypts brightness information separately from color information. It is typically used as part of a color image pipeline and computer graphics hardware. Y'UV represents human perception of color in terms of three components: Y' as the luminance (brightness), and U and V as the chrominance (color). Y'UV can be converted from RGB using:

+   * Y' = 0.299R + 0.587G + 0.114B
+   * U = 0.492(B - Y')
+   * V = 0.877(R - Y')

For our feature space, we can only take the brightness channel Y'.

Now that we have the last piece of the whole preprocessing ready, let's put them together, load, and process (ROI + resize + conversion to Y') the entire labeled dataset:

```
> load_labeled_data <- function(training_path, classes) {
+ # Initialize the pixel features X and target y
+ # X <- matrix(, nrow = 0, ncol = 32*32)
+ y <- vector()
+ # Load images from each of the 43 classes
+ for(i in classes) {
+ print(paste('Loading images from class', i))
+ }
```