# Chapter 17: Generating Images with PHP

![](bbox=[0.335, 0.091, 0.74, 0.333])

# # Image Types

Computers typically work with two types of images: raster and vector. *Raster images (also known as bitmap images)* are made up of pixel data; in a 20-pixel-wide by 20-pixel-high color image there are 400 individual pixels making up the image, and each of these pixels has its own RGB color value. In contrast, a vector image uses mathematical equations to describe the shapes that make up the image. The SVG (Scalable Vector Graphics) format is a good example of a vector image. Vector images are great for diagrams that include lines, curves, and blocks of color, but are not suitable for photographs or images with lots of detail.

In this chapter you concentrate on working with raster images, which tend to be more common on the Web. PHP's GD functions work with four main raster image formats — JPEG, PNG, and GIF for desktop Web browsers, and WBMP images for mobile browsers. (You concentrate on Web images in this chapter.)

These four image formats are *compressed* formats, which means they use mathematical algorithms to reduce the amount of storage to describe the image. They play a key role in keeping your files small and download times short!

It's important to know how to use each of these formats. Although they are all raster, they use different compression techniques, and in certain situations one works better than another.

The JPEG format uses *lossy* compression, in which some of the data in the original image is lost during compression. The format is designed to work with images like photographs, where there's a lot of subtle shading and large blocks of a single color. The format to use when a slight loss in quality won't be apparent to the viewer.

Images in the PNG and GIF formats, on the other hand, are compressed in a *lossless* fashion, meaning that no image data is lost during the compression process. Sharp edges and straight lines (which suffer under JPEG compression) are reproduced faithfully. This technique works with images that contain lines and large blocks of color — cartoons and diagrams, for example.

509