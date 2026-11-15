```
c("data_batch_1.bin", "data_batch_2.bin", "data_batch_3.bin", "data_ba
tch_4.bin"))
```

+   3. Filter the dataset for aeroplane and automobile. This is an optional step and is done to reduce complexity later:

```
# Filter data for Aeroplane and Automobile with label 1 and 2,
respectively
Classes = c(1, 2)
images.rgb.train <- cifar_train$images.rgb
images.lab.train <- cifar_train$images.lab
ix <- images.lab.train %in% Classes
images.rgb.train <- images.rgb.train[ix]
images.lab.train <- images.lab.train[ix]
rm(cifar_train)
```

+   4. Transform to image. This step is required as the CIFAR-10 dataset is a 32 x 32 x 3
+   image, which is flattened to a 1024 x 3 format:

```
# Function to transform to image
transform.Image <- function(index, images.rgb) {
# Convert each color layer into a matrix,
# combine into an rgb object, and display as a plot
img <- images.rgb[index]
img.r.mat <- as.cimg(matrix(img$r, ncol=32, byrow = FALSE))
img.g.mat <- as.cimg(matrix(img$g, ncol=32, byrow = FALSE))
img.b.mat <- as.cimg(matrix(img$b, ncol=32, byrow = FALSE))
# Bind the three channels into one image
img.col.mat <- imappend(list(img.r.mat, img.g.mat, img.b.mat), "c")
return(img.col.mat)
}
```

+   5. The next step involve padding images with zeros:

```
# Function to pad image
image.padding <- function(x) {
img_width <- max(dim(x) [1:2])
img_height <- min(dim(x) [1:2])
pad.img <- pad (x, nPix = img_width - img_height,
axes = ifelse(dim(x) [1] < dim(x) [2], "x", "y"))
return(pad.img)
}
```