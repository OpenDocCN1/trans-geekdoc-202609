
cannot provide a robust background for foreground detection because the panoramas contain moving objects which cause false detection [2].

The timely replacement algorithm based on the central region of the background and the control strategy of camera rotation could achieve target detection and tracking under a dynamic background. The target which has to be tracked was in the field of view which was set before. Currently, this method can only achieve the detection and tracking of a single target, which is the main disadvantage of this paper. The multi-layered correspondence propagation method registers observed frames in the panoramic background and obtains the correspondence background, even when the zoom value (scale) of the PTZ camera changes a lot. Using the correspondence background, foreground objects are detected. Background registration methods are based on phase correlation, block matching, background motion compensation, and so on. Although these algorithms are able to achieve the target detection and tracking of dynamic surroundings, the background matching algorithm is more complex due to the tracking of larger amounts of calculation and lower speeds in real-time processing [3].

Existing feature-based methods often filter the sequence images to extract feature points and try to find matches between a set of points. Subsequently, the mosaic of the images will be obtained. The mosaic’s performance depends on the corresponding correction very deeply [4]. In order to increase the corresponding correction rate, the feature points are tracked frame-to-frame. On the other hand, video frames are typically 30 frames per second and long sequences contain significant redundancy. Therefore, to meet the real time constraint for the whole system, as a first step, some measures to identify key frames, which includes enough effective information for later mosaicking, is needed. In order to overcome the problems existing in traditional methods, a Background Mosaicing Model for wide area surveillance using SURF features is proposed. The objective of this paper is to propose an effective background model for a PTZ camera-based surveillance system which constructs mosaic and is able to properly detect and represent foreground objects even though areas with large zoom. The proposed method works well in workplaces such as Healthcare and monitoring in public places.

## 5.3 Methodology

The main aim of this paper is to propose an effective background model for a PTZ camera-based surveillance system that performs feature extraction followed by mosaic construction and foreground segmentation. Figure 5.1 shows an overview of the methodology.

![](img/146f9a713528a3fbc62fcad0f0d5a352_87_0.png)

Figure 5.1 Proposed methodology.

Input video is converted into a sequence of frames. Subsequently, the features are extracted using SURF (Speeded Up Robust Features). The first frame is taken as a reference frame and the feature points are compared to the points in the immediate next frame. If the feature points of both frames match, it will be compared to the next successive frame. Tracking these N feature points frame-to-frame is continued up until a mismatch occurs [5]. Then, the current frame will be taken as the key frame. Frames taken from reference frame to key frame will be mosaiced to a single frame (updated reference frame) which contains all the essential information about all the in-between frames optional key frames. Consequently, the key frame is updated as the new reference image and N feature points are selected on it [6]. Finally, the Background Mosaic Construction Model is fed for foreground segmentation. The details on methodology are given below.

### 5.3.1 Feature Extraction

Deep Learning has a vast repository of algorithms and techniques that can help us for feature extraction. PTZ camera-based video is taken for motion segmentation. Video formats, like .avi files, are converted as frames [7]. These frames are provided to the Deep Learning algorithm as an input, then all the converted frames as input data are used for feature extraction. All the converted frames are given for SURF feature Extraction. SURF (Speeded-Up Robust Features) features are based on a detector-descriptor scheme. The detector is based on the Hessian Matrix and uses a very basic approximation just as DoG, which is a Laplacian-based detector. A 'Fast-Hessian' detector relies on integral images to reduce computation time. The descriptor also describes a distribution of Haar-wavelet responses within the interest point neighborhood [8]. Again, exploit integral images for speed. Moreover, only 64 dimensions are used, reducing the time for feature computation and increasing the robustness simultaneously. A new indexing step, based on the sign of the Laplacian, increases the strength of the descriptor. The concept of integral images allows faster implementation of box type convolution filters [9]. The entry of an integral frame (I\(_\Sigma\) (x)) at a specific location (x = (x, y)) represents the sum of all pixels in the input image (I) of a rectangular region created by the point (x) and the origin shown in Equation (5.1),

```
I\(_\Sigma\)(X) = \(\sum_{i=0}^{i \le x} \sum_{j=0}^{j=y} I(i, j)\) (5.1)
```

With I\(_\Sigma\) calculated, it only takes four additions to determine the sum of the intensities over any upright, rectangular area, independent of its size. The extracted features are used to construct a Mosaiced Background Model [10].

### 5.3.2 Background Deep Learning Model Based on Mosaic

Mosaicing consists of four steps:

- 1. First, detect N feature points on the initial frame of the video and set this frame as the reference frame
- 2. Then, track these N feature points using SURF algorithm frame-to-frame until condition 1 is broken and set the current frame as a key frame for mosaicing
- 3. Next, the reference image, the key image, and their corresponding feature points will be sent to the quality feature points management module to obtain the most accurate mosaic according to the condition 2 [11]
- 4. Lastly, update the key frame as the new reference frame and reselect N feature points on it

The objective of this paper is to propose a Mosaic Based Background Model for quantity management for robust feature points. Here, the speed and performance of the surveillance system will be increased [12].

- 1. Extract N feature points on the initial frame (F1) of the video.
- 2. Track these N feature points frame-to-frame until M feature points have been matched and the current frame is F2. M is the threshold for re-selecting new feature points.
- 3. Once F2 is reached, decide on F1 and F2 as the key frames which have enough information including the sequence F1~F2.
- 4. Using these two key frames, F1 and F2, and their matched feature points (M), the transform matrix is obtained for mosaicing construction [13].

In this paper, feature points are according to the gradient value. Meanwhile, in order to ensure accuracy of the construction, inputs F1, F2, and their feature points (M) will be subject to the quality management which will be described later. Furthermore, considering that if some strong feature points occur in a video and they are almost matched very well during many frames, step 2 is very difficult to reach and, thus, the interval between F2 and F1 is very large. In order to ensure that the key frames retain enough information, give an upper limitation (H) for the frame interval. If the frame interval between the two key frames is larger than the H, select these two frames as the key frames. Here, a general idea is proposed to identify the upper limitation (H) in different situations [14]. If video frames are typically 30 frames a second, then this long sequence contains significant redundancy. The background model for mosaicing, constructed as shown in Figure 5.2, was implemented on MICC datasets of video frames consisting of 50 frames a second. A mosaiced view of the MICC dataset is shown in Figure 5.2.

![](img/146f9a713528a3fbc62fcad0f0d5a352_89_0.png)

Figure 5.2 MICC dataset background mosaic model.

The sequence of frames has feature points for each frame generated from SURF and when the sequence gets changed, it should be automatically
