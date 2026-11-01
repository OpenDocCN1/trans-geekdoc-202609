
# Edges

Edges are straight lines or curves in the image plane across which there is a “significant” change in image brightness. The goal of edge detection is to abstract away from the messy, multi-megabyte image and towards a more compact, abstract representation, as in [Figure 27.6](#Chapter27-03.xhtml#fig27-6). Effects in the scene very often result in large changes in image intensity, and so produce edges in the image. Depth discontinuities (labeled 1 in the figure) can cause edges because when you cross the discontinuity, the color typically changes. When the surface normal changes (labeled 2 in the figure), the image intensity often changes. When the surface reflectance changes (labeled 3), the image intensity often changes. Finally, a shadow (labeled 4) is a discontinuity in illumination that causes an edge in the image, even though there is not an edge in the object. Edge detectors can’t disentangle the cause of the discontinuity, which is left to later processing.

![](images/Fig-405.jpg)

Figure 27.6 Different kinds of edges: (1) depth discontinuities; (2) surface orientation discontinuities; (3) reflectance discontinuities; (4) illumination discontinuities (shadows).

## Finding edges requires care

Finding edges requires care. [Figure 27.7](#Chapter27-03.xhtml#fig27-7) (top) shows a one-dimensional crosssection of an image perpendicular to an edge, with an edge at `x = 50`.

![](images/Fig-406.jpg)

Figure 27.7 Top: Intensity profile `I(x)` along a one-dimensional section across a step edge. Middle: The derivative of intensity, `I'(x)`. Large values of this function correspond to edges, but the function is noisy. Bottom: The derivative of a smoothed version of the intensity. The noisy candidate edge at `x = 75` has disappeared.

You might differentiate the image and look for places where the magnitude of the derivative `I'(x)` is large. This almost works, but in [Figure 27.7](#Chapter27-03.xhtml#fig27-7) (middle), we see that although there is a peak at `x = 50`, there are also subsidiary peaks at other locations (e.g., `x = 75`) that could be mistaken for true edges. These arise because of the presence of “noise” in the image. Noise here means changes to the value of a pixel that don’t have to do with an edge. For example, there could be thermal noise in the camera; there could be scratches on the object surface that change the surface normal at the finest scale; there could be minor variations in the surface albedo; and so on. Each of these effects make the gradient look big, but don't mean that an edge is present. If we “smooth” the image first, the spurious peaks are diminished, as we see in [Figure 27.7](#Chapter27-03.xhtml#fig27-7) (bottom).

### Noise

Smoothing involves using surrounding pixels to suppress noise. We will predict the “true” value of our pixel as a weighted sum of nearby pixels, with more weight for the closest pixels. A natural choice of weights is a Gaussian filter. Recall that the zero-mean Gaussian function with standard deviation `σ` is

$\\begin{array}{l} {G\_{\\sigma}(x) = \\frac{1}{\\sqrt{2\\pi\\sigma}}e^{- x^{2}/2\\sigma^{2}}} \\\\ {G\_{\\sigma}(x,y) = \\frac{1}{\\sqrt{2\\pi\\sigma^{2}}}e^{- (x^{2} + y^{2})/2\\sigma^{2}}} \\\\ \\end{array}\\,\\,\\,\\begin{array}{l} \\text{in~one~dimension,~or} \\\\ {\\text{in~two~dimensions}\\text{.}} \\\\ \\end{array}$

### Gaussian filter

Applying a Gaussian filter means replacing the intensity `I(x0, y0)` with the sum, over all (`x`, `y`) pixels, of `I(x, y) Gσ(d)`, where `d` is the distance from (`x0`, `y0`) to (`x`, `y`). This kind of weighted sum is so common that there is a special name and notation for it. We say that the function `h` is the convolution of two functions `f` and `g` (denoted as `h = f * g`) if we have

### Convolution

$\\begin{array}{l} {h\\text{(}x\\text{)} = {\\sum\\limits\_{u = - \\infty}^{+ \\infty}{f(u)g(x - u)\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{in~one~dimension,~or}}}} \\\\ {h\\text{(}x,y\\text{)} = {\\sum\\limits\_{u = - \\infty}^{+ \\infty}{\\sum\\limits\_{v = - \\infty}^{+ \\infty}{f(u,v)g(x - u,y - v)\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{in~two~dimensions}\\text{.}}}}} \\\\ \\end{array}$

So the smoothing function is achieved by convolving the image with the Gaussian, `I * Gσ`. A `σ` of 1 pixel is enough to smooth over a small amount of noise, whereas 2 pixels will smooth a larger amount, but at the loss of some detail. Because the Gaussian’s influence fades rapidly with distance, in practice we can replace the ±∞ in the sums with something like ±3`σ`.

We have a chance to make an optimization here: we can combine the smoothing and the edge finding into a single operation. It is a theorem that for any functions `f` and `g`, the derivative of the convolution, `(f * g)'`, is equal to the convolution with the derivative, `f * (g')`. So rather than smoothing the image and then differentiating, we can just convolve the image with the derivative of the Gaussian smoothing function, `G'σ`. We then mark as edges those peaks in the response that are above some threshold, chosen to eliminate spurious peaks due to noise.

There is a natural generalization of this algorithm from one-dimensional crosssections to general 2D images. In two dimensions edges may be at any angle `θ`. Considering the image brightness as a scalar function of the variables `x`, `y`, its gradient is a vector

$\\nabla I = \\begin{pmatrix} \\frac{\\partial I}{\\partial x} \\\\ \\frac{\\partial t}{\\partial y} \\\\ \\end{pmatrix}$

Edges correspond to locations in images where the brightness undergoes a sharp change, and thus the magnitude of the gradient, `|| ∇I ||` should be large at an edge point. When the image gets brighter or darker, the gradient vector at each point gets longer or shorter, but the direction of the gradient

$\\frac{\\nabla I}{\\left| \\middle| \\nabla I \\middle| \\right|} = \\begin{pmatrix} {\\cos\\,\\theta} \\\\ {\\sin\\,\\theta} \\\\ \\end{pmatrix}$

does not change. This gives us a `θ = θ(x, y)` at every pixel, which defines the edge orientation at that pixel. This feature is often useful, because it does not depend on image intensity.

### Orientation

As you might expect from the discussion on detecting edges in one-dimensional signals, to form the gradient, we don’t actually compute `∇I`, but rather `∇(I * Gσ)`, after smoothing the image by convolving it with a Gaussian. A property of convolutions is that this is equivalent to convolving the image with the partial derivatives of the Gaussian. Once we have computed the gradient, we can obtain edges by finding edge points and linking them together. To tell whether a point is an edge point, we must look at other points a small distance forward and back along the direction of the gradient. If the gradient magnitude at one of these points is larger, then we could get a better edge point by shifting the edge curve very slightly. Furthermore, if the gradient magnitude is too small, the point cannot be an edge point. So at an edge point, the gradient magnitude is a local maximum along the direction of the gradient, and the gradient magnitude is above a suitable threshold.

Once we have marked edge pixels by this algorithm, the next stage is to link those pixels that belong to the same edge curves. This can be done by assuming that any two neighboring pixels that are both edge pixels with consistent orientations belong to the same edge curve.

Edge detection isn’t perfect. [Figure 27.8(a)](#Chapter27-03.xhtml#fig27-8) shows an image of a scene containing a stapler resting on a desk, and [Figure 27.8(b)](#Chapter27-03.xhtml#fig27-8) shows the output of an edge detection algorithm on this image. As you can see, the output is not perfect: there are gaps where no edge appears, and there are “noise” edges that do not correspond to anything of significance in the scene. Later stages of processing will have to correct for these errors.

![](images/Fig-407.jpg)
