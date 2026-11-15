# Table 8.3 Comparisons of object tracking hardware implementations.

| | Feature | Frame rate (frames/s) | Image reso. | Clock Freq. (MHz) | Power effi. (nJ/pixel) |
|---|---|---|---|---|---|
| StratiX-III [8] | Directional Edge | 150 | 640 × 480 | 60 | N/A |
| Arria-V[9] | Gray-Level LBP | 2800 | 128 × 128 | 100 | N/A |
| 28nm ASIC [15] | Opticalflow+Depth | 30 | 1920 × 1080 | 180 | 12.22 |
| Virtex-4 [7] | LBP+HOG | 60 | 640 × 480 | 25 | N/A |
| Virtex-5 [11] | Oriented energy | 30 | 640 × 480 | 24 | N/A |
| Zynq-7045 | | 630 | 320 × 240 | | |
| (ours) | UTDCF | 253 | 640 × 480 | 100 | 15.87 |