| Device | Slice Reg | Slice LUTs | DSPs | Block RAM |
|---|---|---|---|---|
| Zynq-7045 | 16947 (3.9%) | 20873 (9.5%) | 48 (5.3%) | 161 (29.5%) |

![](bbox=[0.235, 0.185, 0.795, 0.41])

Figure 8.7 Experimental results on our FPGA prototype of the tracking VLSI system. (a) A sample video result. (b) The tracking precisions on five OTB videos. The particular precision metrics under the commonly used threshold of 20 pixels are stated in the legend.

which is equivalent to 600 frames/s for 320 × 240 images. Its peak power consumption is 768 mW (estimated by the Xilinx Vivado tool).

Fig. 8.7(a) gives a qualitative tracking result of the prototype on a sample video from the OTB dataset. The tracked object positions basically keep up with the ground truth. Fig. 8.7(b) demonstrates quantitative results on five more OTB videos. The precision means the percentage of correctly tracked frames in the whole video. If the distance (in terms of pixels) between the object position predicted by our prototype and the ground truth is above a certain threshold in one frame, then this frame is regarded as incorrectly tracked [8]. Table 8.2 further compares the tracking precisions of our system and those of the hardware implementation in [8] on the five videos. These results indicate that our system performs poorly on the Tiger1 and David videos. The two videos undergo fast scale changes or large occlusions, respectively, but our simple unified compressive features are not scale-invariant or scale-adaptive, and our fast template updating scheme cannot distinguish occlusions and freeze the target template before occlusion. Fig. 8.8 visualizes more tracking results comparing our system and state-of-the-art algorithms [14] on more OTB video clips. Although