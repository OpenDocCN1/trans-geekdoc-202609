+   2. Track these N feature points frame-to-frame until M feature points have been matched and the current frame is F2. M is the threshold for re-selecting new feature points.
+   3. Once F2 is reached, decide on F1 and F2 as the key frames which have enough information including the sequence F1~F2.
+   4. Using these two key frames, F1 and F2, and their matched feature points (M), the transform matrix is obtained for mosaicing construction [13].

In this paper, feature points are according to the gradient value. Meanwhile, in order to ensure accuracy of the construction, inputs F1, F2, and their feature points (M) will be subject to the quality management which will be described later. Furthermore, considering that if some strong feature points occur in a video and they are almost matched very well during many frames, step 2 is very difficult to reach and, thus, the interval between F2 and F1 is very large. In order to ensure that the key frames retain enough information, give an upper limitation (H) for the frame interval. If the frame interval between the two key frames is larger than the H, select these two frames as the key frames. Here, a general idea is proposed to identify the upper limitation (H) in different situations [14]. If video frames are typically 30 frames a second, then this long sequence contains significant redundancy. The background model for mosaicing, constructed as shown in Figure 5.2, was implemented on MICC datasets of video frames consisting of 50 frames a second. A mosaiced view of the MICC dataset is shown in Figure 5.2.

The sequence of frames has feature points for each frame generated from SURF and when the sequence gets changed, it should be automatically

![](bbox=[0.12, 0.68, 0.88, 0.89])

Figure 5.2 MICC dataset background mosaic model.