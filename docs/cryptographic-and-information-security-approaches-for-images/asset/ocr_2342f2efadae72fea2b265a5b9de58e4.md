| 0 | 0 | -1 |
| 0 | 1 | 0 |
| 0 | 0 | 0 |

| -1 | 0 | 0 |
| 0 | 1 | 0 |
| 0 | 0 | 0 |

Figure 21.10 Masks for Roberts edge detector. (a) Convolution mask K_x (b) Convolution mask K_y.

# 21.3.3 Roberts Edge Detector

The Roberts operator is one of the oldest operators, and is very easy to compute, as it only uses the 3 × 3 neighborhood of the current pixel. Its convolution masks are shown in Figure 21.10.

Thus, the magnitude of the edge is computed as Equations 21.8 and 21.9 respectively.

$G_x = (-1)w_3 + 1w_5$  (21.8)

$G_y = (-1)w_1 + 1w_5$  (21.9)

# 21.3.4 Laplacian Edge Detector

The Laplacian operator is very popular and approximates the second derivative, which only gives the gradient magnitude. This is approximated in digital images by a convolution sum, and a 3 × 3 mask is often used (Figure 21.11).

| -1 | -1 | -1 |
| -1 | 8 | -1 |
| -1 | -1 | -1 |

Figure 21.11 Mask for Laplacian edge detector.