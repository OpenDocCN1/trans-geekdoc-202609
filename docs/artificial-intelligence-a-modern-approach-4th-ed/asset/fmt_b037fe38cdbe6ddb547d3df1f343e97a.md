
Figure 27.8(a) Photograph of a stapler. (b) Edges computed from (a).

## 27.3.2 Texture

In everyday language, the texture of surfaces hints at what they feel like when you run a finger over them (the words “texture,” “textile,” and “text” have the same Latin root, a word for weaving). In computational vision, texture refers to a pattern on a surface that can be sensed visually. Usually, these patterns are roughly regular. Examples include the pattern of windows on a building, the stitches on a sweater, the spots on a leopard's skin, blades of grass on a lawn, pebbles on a beach, and a crowd of people in a stadium.

Texture

Sometimes the arrangement is quite periodic, as in the stitches on a sweater; in other instances, such as pebbles on a beach, the regularity is only in a statistical sense: the density of pebbles is roughly the same on different parts of the beach. A usual rough model of texture is a repetitive pattern of elements, sometimes called texels. This model is quite useful because it is surprisingly hard to make or find real textures that never repeat.

Texels

Texture is a property of an image patch, rather than a pixel in isolation. A good description of a patch's texture should summarize what the patch looks like. The description should not change when the lighting changes. This rules out using edge points; if a texture is brightly lit, many locations within the patch will have high contrast and will generate edge points; but if the same texture is viewed under less bright light, many of these edges will not be above the threshold. The description should change in a sensible way when the patch rotates. It is important to preserve the difference between vertical stripes and horizontal stripes but not if the vertical stripes are rotated to the horizontal.

Texture representations with these properties have been shown to be useful for two key tasks. The first is identifying objects—a zebra and horse have similar shape, but different textures. The second is matching patches in one image to patches in another image, a key step in recovering 3D information from multiple images ([Section 27.6.1](#Chapter27-06.xhtml#sec27-6-1)).

Here is a basic construction for a texture representation. Given an image patch, compute the gradient orientation at each pixel in the patch, and then characterize the patch by a histogram of orientations. Gradient orientations are largely invariant to changes in illumination (the gradient will get longer, but it will not change direction). The histogram of orientations seems to capture important aspects of the texture. For example, vertical stripes will have two peaks in the histogram (one for the left side of each stripe and one for the right); leopard spots will have more uniformly distributed orientations.

But we do not know how big a patch to describe. There are two strategies. In specialized applications, image information reveals how big the patch should be (for example, one might grow a patch full of stripes until it covers the zebra). An alternative is to describe a patch centered at each pixel for a range of scales. This range usually runs from a few pixels to the extent of the image. Now divide the patch into bins, and in each bin construct an orientation histogram, then summarize the pattern of histograms across bins. It is no longer usual to construct these descriptions by hand. Instead, convolutional neural networks are used to produce texture representations. But the representations constructed by the networks seem to mirror this construction very roughly.

## 27.3.3 Optical flow

Next, let us consider what happens when we have a video sequence, instead of just a single static image. Whenever there is relative movement between the camera and one or more objects in the scene, the resulting apparent motion in the image is called optical flow. This describes the direction and speed of motion of features in the image as a result of relative motion between the viewer and the scene. For example, distant objects viewed from a moving car have much slower apparent motion than nearby objects, so the rate of apparent motion can tell us something about distance.

Optical flow

In [Figure 27.9](#Chapter27-03.xhtml#fig27-9) we show two frames from a video of a tennis player. On the right we display the optical flow vectors computed from these images. The optical flow encodes useful information about scene structure—the tennis player is moving and the background (largely) isn’t. Furthermore, the flow vectors reveal something about what the player is doing—one arm and one leg are moving fast, and the other body parts aren’t.

×![](images/Fig-408.jpg)

Figure 27.9 Two frames of a video sequence and the optical flow field corresponding to the displacement from one frame to the other. Note how the movement of the tennis racket and the front leg is captured by the directions of the arrows. (Images courtesy of Thomas Brox.)

The optical flow vector field can be represented by its components `vx(x, y)` in the x direction and `vy(x, y)` in the y direction. To measure optical flow, we need to find corresponding points between one time frame and the next. A very simple-minded technique is based on the fact that image patches around corresponding points have similar intensity patterns. Consider a block of pixels centered at pixel `p`, (`x0`, `y0`), at time `t`. This block of pixels is to be compared with pixel blocks centered at various candidate pixels `qi` at (`x0 + Dx`, `y0 + Dy`) at time `t + Dt`. One possible measure of similarity is the sum of squared differences (`SSD`):

Sum of squared differences (SSD)

$\\text{SSD(}D\_{x},D\_{y}\\text{)} = {\\sum\\limits\_{(x,y)}{{(I(x,y,t) - I(x + D\_{x},y\\, + \\, D\_{y},t + D\_{t}))}^{2.}}$

Here, (`x`, `y`) ranges over pixels in the block centered at (`x0`, `y0`). We find the (`Dx`, `Dy`) that minimizes the `SSD`. The optical flow at (`x0`, `y0`) is then (`vx`, `vy`) = (`Dx` / `Dt`, `Dy` / `Dt`). Note that for this to work, there should be some texture in the scene, resulting in windows containing a significant variation in brightness among the pixels. If one is looking at a uniform white wall, then the `SSD` is going to be nearly the same for the different candidate matches `q`, and the algorithm is reduced to making a blind guess. The best-performing algorithms for measuring optical flow rely on a variety of additional constraints to deal with situations in which the scene is only partially textured.

## 27.3.4 Segmentation of natural images

Segmentation is the process of breaking an image into groups of similar pixels. The basic idea is that each image pixel can be associated with certain visual properties, such as brightness, color, and texture. Within an object, or a single part of an object, these attributes vary relatively little, whereas across an inter-object boundary there is typically a large change in one or more of these attributes. We need to find a partition of the image into sets of pixels such that these constraints are satisfied as well as possible. Notice that it isn't enough just to find edges, because many edges are not object boundaries. So, for example, a tiger in grass may generate an edge on each side of each stripe and each blade of grass. In all the confusing edge data, we may miss the tiger for the stripes.

Segmentation

There are two ways of studying the problem, one focusing on detecting the boundaries of these groups, and the other on detecting the groups themselves, called regions. We illustrate this in [Figure 27.10](#Chapter27-03.xhtml#fig27-10), showing boundary detection in (b) and region extraction in (c) and (d).

×![](images/Fig-409.jpg)
