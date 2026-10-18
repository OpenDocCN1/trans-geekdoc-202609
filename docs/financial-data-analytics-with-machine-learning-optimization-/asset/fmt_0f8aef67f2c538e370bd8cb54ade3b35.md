
Based on the analysis above, many suggestions can be formulated for the banking industry. For example, as high‐net worth individuals tend to cherish the value of time more than others, they would rather save time by contacting the bank online directly, rather than queue up in the branch or make lengthy phone calls. It is then suggested that banks should promote and improve their online credit card services to attract more prestigious credit card users.

## Image Segmentation

A typical example of image processing is `image segmentation`, which means partitioning an image into `K` different segments to make subsequent data processing easier, like using photo‐editing software such as `Photoshop`. To implement `K`‐means in this context, we usually adopt the `CIE 1976 Lab color space` (a.k.a. `L*a*b*` channel) instead of the usual RGB channel. This color space also expresses a pixel in a 3‐tuple, namely the lightness `L*`, the green‐red component `a*` and the blue‐yellow component `b*`. Compared with RGB setting, a numerical change in these three coordinates can better reflect the magnitude of color change perceived by a human.

To perform the segmentation according to colors, we can neglect the lightness component `L*`, while the remaining ones `a*` and `b*` are extracted from each pixel, forming a sample of two‐dimensional points, with a size equal to the total number of pixels in the picture. This sample is then clustered using the `K`‐means algorithm or its variants as mentioned before, and pixels ending up in the same cluster are assigned the same values of `a*` and `b*` of the corresponding centroid. [Figure 14.7](#c14.xhtml#c14-fig-0007) shows an illustration of image segmentation using `K`‐means clustering with `K = 5`. ![FIGURE 14.7 Image segmentation using upper K‐means clustering.](images/c14f007.png)

[**FIGURE 14.7**](#c14.xhtml#R_c14-fig-0007) Image segmentation using `K`‐means clustering.

## Photo Denoising and Dictionary Learning

Another example that we may already benefit from is `photo denoising`, a mechanism that helps photos get rid of random noises on brightness or color caused by electrons, and so make the photo more aesthetically pleasant. It is so prevalent nowadays that we barely perceive its existence, thanks to the technique of `dictionary learning` that speeds up the procedure.

Dictionary learning is similar to PCA: given a dataset we wish to extract a number of basic elements called `atoms` such that almost all feature vectors can be represented in terms of these fundamental building blocks. The collection of such atoms is called a `dictionary`. It is at this stage that `K`‐means clustering or its extension, `K`‐SVD (`K`‐SVD) [\[2\]](#c14.xhtml#c14-bib-0002), is implemented.

Here, we briefly summarize `K`‐SVD: let `Y ∈ R^(p×n)` be the matrix of `n` observed image signals so that each has `p`‐dimensional features, and `D ∈ R^(p×K)` be the `dictionary` in which the `k`‐th column `d_k` is the `k`‐th atom to be learnt, for `k = 1, ..., K`.
