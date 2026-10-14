# Table 13.8 Synthesis Results for Secure HEVC Modules

| Modules | Area (um²) | Power (mW) |
|---|---|---|
| Integer 2D DCT | 30115.00 | 255.19 |
| Watermark embedding unit | 1043.00 | 6.691 |
| Total | 31158.00 | 261.88 |

# 13.8.4 ASIC Implementation

The performance of secure HEVC is measured for custom hardware with cost, power dissipation and utilization of resources.

# 13.8.4.1 Hardware Cost

Both, Integer DCT and watermark embedding unit are synthesized with Design Complier of synopsys with Farday 0.18 µm technology. The resultant area are reported in Table 13.8. The watermark embedding unit occupies 3.35% area. The custom IC of the watermark embedding chip is capable of providing the security of HEVC encoder with the expanse of a relatively small area. The device such as HEVC video encoder is huge enough and would have room for a watermarking unit in order to have the facility of ownership verification. The obtained values of area justify the simplicity of our watermarking algorithm.

# 13.8.4.2 Power Consumption

The power consumption for HEVC modules is also calculated by Design Complier (0.18 µm) and is noted in Table 13.8. The total power consumption of HEVC encoder including watermarking unit is around 261.88 mW using recursive DCT method. Whereas, the watermarking unit consumes power of only 6.691 mW which is (2.5%) for the overall encoding system. This guarantees that the inclusion of the watermark embedding unit does not have much overhead of power consumption for the overall system. The power consumption will not be affected even for high resolution video. The watermarking system operated on 8 × 8 blocks of a frame at a time irrespective of any resolution of frame of a video. The overall performance is not dependent on resolution of frame but depends only on the number of frames which are to be watermarked.

# 13.8.5 Comparison with Related Work

Previous works were mainly based on uncompressed or older compression standards. Petitjean et al. [9] realized MPEG-2 standard-based watermarking that uses general