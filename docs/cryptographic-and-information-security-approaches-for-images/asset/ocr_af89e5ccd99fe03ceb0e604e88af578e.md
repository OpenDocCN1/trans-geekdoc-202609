![](bbox=[0.12, 0.12, 0.88, 0.78])

# Figure 21.5 Flowchart of interpolation and edge detection based data hiding methods.

When edge detection techniques are used, how many bits can be embedded? It came from basic idea that it is difficult to discriminate the distortion in edge areas even though the embedding bits are larger than smooth areas.

The cover image is easily calculated from the original image and used as the source for the data hiding method. An edge detection algorithm is then applied to divide the cover image into edge and non-edge areas, as more secret data can be embedded in edge areas, plus a different data hiding method is used when embedding the secret data in edge and non-edge areas.

In this chapter, reversible data hiding methods using image interpolation techniques and edge detection techniques are described.