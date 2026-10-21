![](bbox=[0.21, 0.12, 0.78, 0.27])

FIGURE 1.30 Use of autocorrelation function for texture analysis. This diagram shows the possible 1-D profile of the autocorrelation function for a piece of material in which the weave is subject to significant spatial variation: notice that the periodicity of the autocorrelation function is damped down over quite a short distance.

condensed to relatively few numbers before it can be used to classify the texture. The early paper by Haralick et al. (1973) gave fourteen such measures, and these were used successfully for classification of many types of material (including, for example, wood, corn, grass and water).

Unfortunately, the amount of data in the co-occurrence matrices is liable to be many times more than in the original image—a situation which is exacerbated in more complex cases by the number of values of d and θ that are required to accurately represent the texture. In addition, the number of grey levels is typically ~256, and the amount of matrix data varies as the square of this number. Finally, co-occurrence matrices merely provide a new representation: they do not themselves solve the recognition problem. As a result of these factors, the 1980s saw a highly significant diversification of methods for the analysis of textures. Of these, Laws’ approach (1979; 1980a; 1980b) is important in that it has led to other developments which provide a systematic, adaptive means of tackling texture analysis. This approach is covered in the following section.

# 1.6.3 Laws’ texture energy approach

In 1979 and 1980 Laws presented his novel texture energy approach to texture analysis (Laws, 1979, 1980a,b). This involved the application of simple filters to digital images. The basic filters he used were common Gaussian, edge detector and Laplacian-type filters, and were designed to highlight points of high ‘texture energy’ in the image. By identifying these high energy points, smoothing the various filtered images, and pooling the information from them, he was able to characterize textures highly efficiently. As remarked earlier, Laws’ approach has strongly influenced much subsequent work and it is therefore worth considering it here in some detail.

The Laws’ masks are constructed by convolving together just three basic 1 × 3 masks:

```
L3 = [1  2  1]    (1.104)
E3 = [-1  0  1]   (1.105)
S3 = [-1  2  -1]  (1.106)
```