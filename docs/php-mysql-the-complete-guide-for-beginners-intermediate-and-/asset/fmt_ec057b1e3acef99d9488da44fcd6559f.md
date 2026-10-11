
# Chapter 74: GD Library

## Section 74.1: Stream Wrapper

![](Image01459.jpg)A fully implemented stream wrapper class should look like [this](http://php.net/manual/en/stream.streamwrapper.example-1.php), but according to tests with the `__call` magic method, only `stream_open`, `stream_write` and `stream_close` are called from internal functions.

No flags are required in the `fopen` call, but you should at least pass an empty string. This is because the `fopen` function expects such parameter, and even if you don't use it in your `stream_open` implementation, a dummy one is still required.

![](Image01460.jpg)According to tests, `stream_write` is called multiple times. Remember to use `.=` (concatenation assignment), not `=` (direct variable assignment).

### Example usage

| <img | |

| --- | |

![](Image01461.jpg) In the `>` HTML tag, an image can be directly provided rather than using an external link: `echo '<img src="data:image/png;base64,' . base64_encode($binary) . '">';`

## Section 74.2: Creating an image

To create a blank image, use the `imagecreatetruecolor` function:

![](Image01462.jpg)

`$img` is now a resource variable for an image resource with `$width x $height` pixels. Note that width counts from left to right, and height counts from top to bottom.

Image resources can also be created from [image creation functions](http://php.net/manual/en/ref.image.php), such as:

![](Image01463.jpg)`imagecreatefrompng`, `imagecreatefromjpeg`

| imagecreatefrom | |

| --- | |

![](Image01464.jpg)other `*` functions.

| imagedestroy | |

| --- | |

Image resources may be freed later when there are no more references to them. However, to free the memory immediately (this may be important if you are processing many large images), using `imagedestroy()` on an image when it is no longer used might be a good practice. ![](Image01465.jpg)`imagedestroy($image);`

### Converting an image

Images created by image conversion does not modify the image until you output it. Therefore, an image converter can be as simple as three lines of code:

![](Image01466.jpg)

## Section 74.3: Image Cropping and Resizing

If you have an image and want to create a new image, with new dimensions, you can use `imagecopyresampled` function: first create a new image with desired dimensions:

![](Image01467.jpg)

| createimagefrom | |

| --- | |

and store the original image into a variable. To do so, you may use one of the `*` functions where `*` stands for:

![](Image01468.jpg)
- jpeg
- gif
- png
- string

For example:

![](Image01469.jpg)

Now, copy all (or part of) original image (`src_img`) into the new image (`dst_img`) by `imagecopyresampled`:

![](Image01470.jpg)

| src_ | | * and | | dst_ |

| --- | --- | --- | --- | --- |

To set `*` dimensions, use the below image:

![](Image01471.jpg)

Now, if you want to copy entire of source (initial) image, into entire of destination area (no cropping):

```
$src_x = $src_y = $dst_x = $dst_y = 0;
$dst_width = $width; // width of new image
$dst_height = $height; //height of new image
$src_width = imagesx($src_img); //width of initial image
```
![](Image01472.jpg) `$src_height = imagesy($src_img); //height of initial image`

# Chapter 75: Imagick

## Section 75.1: First Steps

### Installation

#### Using apt on Debian based systems

![](Image01473.jpg)

#### Using Homebrew on OSX/macOs

![](Image01474.jpg)

To see the dependencies installed using the brew method, visit [brewformulas.org/Imagemagick](http://brewformulas.org/Imagemagick).

#### Using binary releases

Instructions on [imagemagick website](https://www.imagemagick.org/script/binary-releases.php#macosx).

### Usage

![](Image01475.jpg)

## Section 75.2: Convert Image into base64 String

This example is how to turn an image into a Base64 string (i.e. a string you can use directly in a `src` attribute of an `img` tag). This example specifically uses the [Imagick](http://php.net/manual/en/intro.imagick.php) library (there are others available, such as [GD](http://php.net/manual/en/intro.image.php) as well).

![](Image01476.jpg)

![](Image01477.jpg)

# Chapter 76: SOAP Server

## Section 76.1: Basic SOAP Server

![](Image01478.jpg)

# Chapter 77: Machine learning

## Section 77.1: Classification using PHP-ML

Classification in Machine Learning is the problem that identifies to which set of categories does a new observation belong. Classification falls under the category of Supervised Machine Learning.

![](Image01479.jpg)Any algorithm that implements classification is known as classifier.

The classifiers supported in PHP-ML are:

![](Image01480.jpg)
- SVC (Support Vector Classification)
- k-Nearest Neighbors
- Naive Bayes

The `train` and `predict` method are same for all classifiers. The only difference would be in the underlying algorithm used.

### SVC (Support Vector Classification)

Before we can start with predicting a new observation, we need to train our classifier. Consider the following code:

![](Image01481.jpg)

The code is pretty straight forward. `$cost` used above is a measure of how much we want to avoid misclassifying each training example. For a smaller value of `$cost` you might get misclassified examples. By default it is set to `1.0`.

Now that we have the classifier trained we can start making some actual predictions. Consider the following codes that we have for predictions:

![](Image01482.jpg)

The classifier in the case above can take unclassified samples and predicts their labels. `predict` method can take a single sample as well as an array of samples.

### k-Nearest Neighbors

The classifier for this algorithm takes in two parameters and can be initialized like:

`$classifier = new KNearestNeighbors($neighbor_num = 4);`

![](Image01483.jpg) `$classifier = new KNearestNeighbors($neighbor_num = 3, new Minkowski($lambda = 4));`

`$neighbor_num` is the number of nearest neighbours to scan in [knn](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm) algorithm while the second parameter is distance metric which by default in first case would be `Euclidean`. More on Minkowski can be found [here](https://en.wikipedia.org/wiki/Minkowski_distance). Following is a short example on how to use this classifier:

![](Image01484.jpg)

### NaiveBayes Classifier

| Bayes' theorem | |

| --- | |

NaiveBayes Classifier is based on Bayes' theorem and does not need any parameters in constructor.

The following code demonstrates a simple prediction implementation:

![](Image01485.jpg)

### Practical case

Till now we only used arrays of integer in all our case but that is not the case in real life. Therefore let me try to describe a practical situation on how to use classifiers.

| mm | | , | | 10 mm |

| --- | --- | --- | --- | --- |

| 10 mm | | , | | 20 mm |

| --- | --- | --- | --- | --- |

![](Image01486.jpg) ![](Image01487.jpg)Suppose you have an application that stores characteristics of flowers in nature. For the sake of simplicity we can consider the color and length of petals. So there two characteristics would be used to train our data. color is the simpler one where you can assign an int value to each of them and for length, you can have a range like `(0)=1`, `()=2`. With the initial data train your classifier. Now one of your user needs identify the kind of flower that grows in his backyard. What he does is select the color of the flower and adds the length of the petals. You classifier running can detect the type of flower ("Labels in example above").

## Section 77.2: Regression

| PHP | | - | | ML |

| --- | --- | --- | --- | --- |

In classification using PHP-ML we assigned labels to new observation. Regression is almost the same with difference being that the output value is not a class label but a continuous value. It is widely used for predictions and forecasting. PHP-ML supports the following regression algorithms:

![](Image01488.jpg)
- Support Vector Regression
- LeastSquares Linear Regression

Regression has the same `train` and `predict` methods as used in classification.

### Support Vector Regression

This is the regression version for SVM (Support Vector Machine). The first step like in classification is to train our model:

![](Image01489.jpg)
