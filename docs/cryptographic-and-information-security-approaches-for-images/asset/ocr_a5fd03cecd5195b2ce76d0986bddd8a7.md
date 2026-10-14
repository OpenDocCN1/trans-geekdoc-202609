# 7.1.2 Scalability

An SVC bitstream consists of a low-quality video sub-bitstream as well as one or more supplement sub-bitstreams. Due to the flexible arrangement of NALUs, SVC provides three kinds of scalabilities, as depicted in Figure 7.2. These scalability properties enable an SVC-aware router to reduce the bit-rate directly without decoding the bitstream so as to meet the requirements of network bandwidth and/ or end user devices’ capabilities.

There are four temporal layers, two spatial layers, and three quality layers.

**Temporal scalability:** Temporal enhancement layer defines the various numbers of pictures per second, which is hierarchical P- or B-pictures, and logically organizes the bitstream into a hierarchy of images. The temporal base layer should be coded with highest fidelity since they are used as references for motion-compensated prediction of pictures for all temporal layers; the enhancement layers use a larger quantization parameter because the quality of these pictures influences fewer pictures. Thus, when an SVC-aware router discards some picture (e.g., B-pictures) data directly without decoding the bitstream, it produces a lower bit-rate SVC bitstream.

**Spatial scalability:** SVC spatial scalability means that its base layer represents a video of low spatial resolution, and the enhancement layers increase the spatial resolution of the video. As there are inter-layer prediction mechanisms for the sake of coding efficiency, a lower layer must be present if a higher layer exists, but the lower layer does not need the higher layers at the decoder side. Therefore, when the highest layer is discarded, the rest of layers are still able to be decoded. This discarding process can be repeated until only one layer remains. In other words, the spatial resolution of an SVC bitstream can be decreased directly without decoding the bitstream.

![](bbox=[0.22, 0.66, 0.75, 0.9])

Figure 7.2 An example architecture of H.264/SVC three dimensions.