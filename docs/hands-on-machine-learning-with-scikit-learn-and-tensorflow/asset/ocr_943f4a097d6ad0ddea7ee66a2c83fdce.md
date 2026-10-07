![](bbox=[0.14438, 0.09135, 0.85562, 0.46345])

Figure 14-24. Detecting Multiple Objects by Sliding CNN Across the Image

This technique is fairly straightforward, as you can see it will detect the same object multiple times, at slightly different positions. Post-processing will then be needed to get rid of all the unnecessary bounding boxes. A common approach for this is called **non-max suppression**:

+   - You need to add an *extra oddness* output to your CNN, to estimate the probability that a flower is indeed present in the image (alternatively, you could add a "no-flower" class, but this usually does not work well). It must use the sigmoid activation function and you train it using the *binary_crossentropy* loss. Then get rid of all the bounding boxes for which the oddness score is below some threshold: this will drop all all the bounding boxes that don't actually contain a flower.

+   - Second, find the bounding box with the highest confidence score, and get rid of all the other bounding boxes that overlap a lot with it (e.g., with an IoU greater than 60%). For example, in **Figure 14-24**, the bounding box with the max score is the thick bounding box over the top-most rose (the oddness score is represented by the thickness of the bounding boxes). The other bounding box over that rose overlaps a lot with the max bounding box, so we will get rid of it.

**WOW! eBook
www.wowebook.org**