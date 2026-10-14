# Table 15.3 (Continued) BER Results Against Different Attacks (in case of Lena, Boat, and Airplane images)

| Attack Id | Attacks | Approach 1 |  |  | Approach 2 |  |  |
|---|---|---|---|---|---|---|---|
|  |  | Lena | Boat | Airplane | Lena | Boat | Airplane |
| a11. | crop (25%) left up corner (white) | 3.44 | 3.6 | 3.4 | 0.006 | 0 | 0.006 |
| a12. | crop (50%) bottom(white) | 3.6 | 3.6 | 3.4 | 0.19 | 0.15 | 1.09 |
| a13. | affine transformation (2) | 3.8 | 3.7 | 3.6 | 0 | 0 | 0.09 |
| a14. | remove lines (RML) (10) | 3.5 | 3.4 | 3.6 | 0.024 | 0 | 0 |
| a15. | translation vertically (10) | 3.9 | 3.7 | 3.6 | 0.12 | 0 | 0.19 |
| a16. | rotation (counterclockwise 5°) + crop (25%) left up corner | 3.4 | 3.8 | 3.4 | 0.58 | 0 | 1.7 |
| a17. | histogram equalization + resize (256 × 256) | 3.5 | 3.8 | 3.8 | 0 | 0.73 | 1.7 |
| a18. | Rotation (counterclockwise 5°) + crop (25%) left up corner + histogram equalization | 3.4 | 4.0 | 3.4 | 0.62 | 0 | 1.09 |
| a19. | Gaussian noise (variance = 0.01, mean = 0) + rotation (counterclockwise 5°) + sharpen | 3.9 | 3.7 | 3.5 | 0 | 0 | 1.08 |