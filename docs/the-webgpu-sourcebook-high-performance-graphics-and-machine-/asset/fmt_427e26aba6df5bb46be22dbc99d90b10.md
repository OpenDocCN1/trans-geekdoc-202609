
The fundamental operation is the two-dimensional dot product, which accepts two matrices and returns the sum of the products of their corresponding elements. For example, suppose `A` and `B` are two matrices given as follows:

$$A = \\left| \\begin{matrix} a\_{00} & a\_{01} & a\_{02} \\\\ a\_{10} & a\_{11} & a\_{12} \\\\ a\_{20} & a\_{21} & a\_{22} \\\\ \\end{matrix} \\right|\\;\\;\\;\\;\\;\\;B = \\left| \\begin{matrix} b\_{00} & b\_{01} & b\_{02} \\\\ b\_{10} & b\_{11} & b\_{12} \\\\ b\_{20} & b\_{21} & b\_{22} \\\\ \\end{matrix} \\right|\\;$$  

The two-dimensional dot product of `A` and `B` can be computed with the following equation:

$$\\begin{matrix} {A \\cdot B = a\_{00}b\_{00} + a\_{01}b\_{01} + a\_{02}b\_{02} + a\_{10}b\_{10} + a\_{11}b\_{11} +} \\\\ \\begin{matrix} \\hspace{0pt} & \\hspace{0pt} & \\hspace{0pt} & {a\_{12}b\_{12} + a\_{20}b\_{20} + a\_{21}b\_{21} + a\_{22}b\_{22}} \\\\ \\end{matrix} \\\\ \\end{matrix}$$  

Image filtering treats an image as a matrix of values, and computes a two-dimensional dot product for each of its pixels. In essence, the goal is to intensify or diminish the differences between adjacent pixels.

The second matrix is called the filter's *kernel*, and its elements determine what effect the filter will have. To demonstrate this, I'll show how image filtering can reduce the noise in the image illustrated in [Figure 10.1](#chapter10.xhtml#fig10_1).

![Figure 10.1 Image before filtering. (Photo by 663highland, Provided under Creative Commons License 2.5.)](images/fig10_1.jpg)

[Figure 10.1](#chapter10.xhtml#b10fig10_1) Image before filtering. (Photo by 663highland, Provided under Creative Commons License 2.5.)

You can think of noise as unwanted variation between nearby pixels. One way to reduce this variation is to replace each pixel with the average of it and its surrounding pixels. To express this mathematically, we'll denote the image as a matrix called `M`. Then `Mij` is the pixel at Row `I` and Column `J`. The color of the filtered pixel can be computed in the following way:

$$M\_{ij,filtered} = \\frac{1}{9}\\begin{pmatrix} {M\_{i - 1,j - 1} + M\_{i,j - 1} + M\_{i + 1,j - 1} + M\_{i - 1,j} + M\_{i,j}} \\\\ {+ M\_{i + 1,j} + M\_{i - 1,j + 1} + M\_{i,j + 1} + M\_{i + 1,j + 1}} \\\\ \\end{pmatrix}$$  

This operation can also be performed by taking the dot product of these nine image pixels with a kernel matrix, `K_box`, whose elements are given as follows:

$$K\_{box} = \\frac{\\left| \\begin{matrix} 1 & 1 & 1 \\\\ 1 & 1 & 1 \\\\ 1 & 1 & 1 \\\\ \\end{matrix} \\right|}{9}\\;\\;\\;M\_{ij,filtered} = K\_{box} \\cdot M\_{ij}$$  

To fully filter an image, this dot product must be performed for each pixel. Once this is done, the filtered image will have the same size as the original. Because the elements of the kernel add to 1, the filtered result will also have the same average brightness. [Figure 10.2](#chapter10.xhtml#fig10_2) shows what the filtered image looks like.

![Figure 10.2 Image filtered with box filter.](images/fig10_2.jpg)

[Figure 10.2](#chapter10.xhtml#b10fig10_2) Image filtered with box filter.

This filter, called a *box filter* or *mean filter*, has removed much of the noise in the original image by averaging neighboring pixels. But it has also removed a significant amount of detail. The following discussion introduces the Gaussian blur, which does a better job.

## Gaussian Blur

When it comes to removing noise, the Gaussian blur generally gives better results than the box filter. The term *Gaussian* refers to a special function that produces the commonly encountered bell curve. [Figure 10.3](#chapter10.xhtml#fig10_3) shows what the Gaussian function looks like in two dimensions.

![Figure 10.3 Two-dimensional Gaussian function.](images/fig10_3.jpg)

[Figure 10.3](#chapter10.xhtml#b10fig10_3) Two-dimensional Gaussian function.

To implement Gaussian filtering in code, we need to approximate its values in a 3-by-3 matrix. One possible kernel is given as follows:

$$K\_{gaussian} = \\frac{\\left| \\begin{matrix} 1 & 2 & 1 \\\\ 2 & 4 & 2 \\\\ 1 & 2 & 1 \\\\ \\end{matrix} \\right|}{16}$$  

Filtering with this kernel produces a blurring effect like that of the box filter, but it gives priority to the central pixel and the immediately adjacent pixels. This means that the filtered image keeps more of the differences between one pixel and the next. [Figure 10.4](#chapter10.xhtml#fig10_4) shows what the result looks like.

![Figure 10.4 Effect of Gaussian blur.](images/fig10_4.jpg)

[Figure 10.4](#chapter10.xhtml#b10fig10_4) Effect of Gaussian blur.

The Gaussian blur serves as a compromise between the noisy image and the deep blurring produced by the box filter. The kernel used in this filter is only one possible implementation of the Gaussian blur.

## Image Sharpening

Just as the box filter and Gaussian blur reduce differences between pixels, a sharpening filter emphasizes differences. It accomplishes this by subtracting nearby pixels from the central pixel. An example kernel is shown here:

$$K\_{sharpen} = \\left| \\begin{matrix} {- 1} & {- 1} & {- 1} \\\\ {- 1} & 9 & {- 1} \\\\ {- 1} & {- 1} & {- 1} \\\\ \\end{matrix} \\right|$$  

If the central pixel has the same value as those around it, the filtered pixel will be equal to that of the original. But if the central pixel is much greater than its neighbors, the filtered value will be large. This is shown in [Figure 10.5](#chapter10.xhtml#fig10_5), which displays an image before and after sharpening.

![Figure 10.5 Effect of image sharpening.](images/fig10_5.jpg)

[Figure 10.5](#chapter10.xhtml#b10fig10_5) Effect of image sharpening.

A sharpening filter magnifies noise along with other details. The following discussion explains how this filter can be implemented using WebGPU.

## Example Application—Image Sharpening

The `Ch10_SharpenImage` application demonstrates how compute shaders can use storage textures for image filtering. It filters an input image using a sharpening kernel and then displays the result in the page. Its operation can be split into three main steps:

1. The application creates a texture from an image file and an empty storage texture.
2. The compute shader reads texels from the texture and writes grayscale values to the storage texture.
3. The vertex and fragment shaders display the content of the storage texture as though it was a regular texture.

The last point is important to understand. At a low level, storage textures are identical to regular textures. The only difference is that storage textures are specially configured so that shaders can modify their content.

### Creating Textures

The code in `ch10_sharpenimage.js` starts by creating the fundamental objects needed for WebGPU operation (`adapter`, `device`, `encoder`, and so on). Then it creates two textures. The first texture serves as the input for the compute shader and holds the content of the `smiley.png` image. The following code shows how it's created.

```
// Create ImageBitmap from image file
const response = await fetch("tower.png");
const imageBitmap = await createImageBitmap(await response.blob());

// Create texture to hold input image
const imageTexture = device.createTexture({
    size: [imageBitmap.width, imageBitmap.height, 1],
    format: "rgba8unorm",
    usage:
        GPUTextureUsage.TEXTURE_BINDING |
        GPUTextureUsage.COPY_DST |
        GPUTextureUsage.RENDER_ATTACHMENT
});

// Write data to input texture
device.queue.copyExternalImageToTexture(
    { source: imageBitmap },
    { texture: imageTexture },
    [imageBitmap.width, imageBitmap.height]
);
```
