# 7.2.2 On Security of Content-Based Video Stream Authentication

This section surveys and classifies existing transform-domain CBA (Content-based authentication) schemes for videos into two categories and points out that, in contrary to CBA for images, there exists a common design flaw in these schemes. We present the principles (based on video coding concept) on how the flaw can be exploited to mount semantic-changing attacks in the transform domain that cannot be detected by existing CBA schemes. We show the attack examples including content removal, modification and insertion attacks. Noting that these CBA schemes are designed at the macro block level, we discuss, from the attacker's point of view, the conditions in attacking content based authenticated macroblocks.

# 7.2.2.1 The H.264 Video Coding Standard

Most video coding standards including MPEG-2, MPEG-4, and H.264 achieve compression by identifying similarities in the spatial (within frame) and the temporal (between frames) dimensions. In the H.264 standard, a prediction model takes as input a raw video frame and outputs a residual frame. The raw frame is first partitioned into units (each of size 16 × 16 pixels) called macroblocks, which may be further partitioned into 16 (4 × 4) blocks. Given a raw macroblock Ori, the prediction model searches for the most perceptually similar macroblock within a searchable region, i.e., neighbouring macroblocks in the same frame (intra prediction) or in adjacent frames (inter-prediction), and uses the most similar macroblock as reference to generate a prediction macroblock Pred. The prediction macroblock is (pixel-wise) subtracted from the raw macroblock to obtain the residual macroblock Res as in (1). The residual macroblock is then transformed, quantized and entropy encoded to the bitstream domain.

Figure 7.6 shows the syntax of an H.264 macroblock. In this figure, parameter type indicates whether the macroblock is intra- or inter-predicted. Each (intra/inter) macroblock can be partitioned into sub-blocks of different sizes, which is conveyed by the parameter partition size. For an intra macroblock, prediction mode conveys the Directional Prediction Mode (DPM) indicating the location of reference macroblock(s)

![](bbox=[0.12, 0.78, 0.88, 0.92])

Figure 7.6 The syntax elements of a H.264 macroblock.