# An Enhanced Image Dehazing Procedure Using CLAHE and a Guided Filter 39

The higher value of the contrast of the enhanced image, the better is the result for the dehazing algorithm.

# 12.7 EXPERIMENTAL RESULTS AND DISCUSSION

Similarly, in Figure 12.3, haze level 100 is considered. In Figure 12.3(c), the output of the white balanced image is given. After applying CLAHE to it, the result seems to be not very appealing, as shown in Figure 12.3(d). To improve the result, GF has been used and the result is shown in Figure 12.3(e). It is observed that the result is quite successful in removing the haze from the background as well.

The experiment has been performed and tested on hazy images collected from the data set HazeRD. For Figure 12.2, haze level 50 has been considered. Figure 12.2(b) shows that the image is quite hazy. White balancing is performed to adjust the color of the image and the output of the white balanced image is shown by applying CLAHE, in Figure 12.2(e), it is observed that, not visual improvement is observed in the image. So the image is tested by applying GF to it in Figure 12.2(f), where it is observed that, although the visibility of the hazy image has increased, the haze has not been removed totally from the background. Considering haze level 200 for Figure 12.4, it is observed that the result obtained after applying CLAHE, shown in Figure 12.4(d), is not improved much as compared to the resultant image of white balance in Figure 12.4(c). So to improve the result, GF is applied and the final result image is shown in Figure 12.4(e), where haze is seen to be removed and the result obtained is also very appealing. The contrast of the image is also improved as compared to the earlier results.

![](bbox=[0.128, 0.574, 0.871, 0.833])

(a) (b) (c)

(d) (e)

FIGURE 12.2 Experimental results on hazy Image 50: (a) Ground truth image, (b) Input image, (c) Image after white balancing, (d) Image after applying CLAHE, (e) Image after applying CLAHE+Guided.