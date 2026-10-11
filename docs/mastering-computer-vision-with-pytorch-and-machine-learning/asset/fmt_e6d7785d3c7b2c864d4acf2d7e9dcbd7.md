
The 3×3 sub-matrix on the top-left corner of the `pose` matrix is equal to the new rotation matrix `R`. From the top 3×1 sub-matrix in the last column of the `pose`, we get a ray origin, or the camera's world coordinates after the camera is rotated, where `r` is the distance between the two coordinate systems. We use the `pose` matrix to convert `X⃗[c]` to `X⃗[w]` for query points. During model training, all query points and ray origins are position-encoded by a function defined in the last function of Cell 04. A hyperparameter `L` is the number of encoding functions. The value of `L` for query points and ray origins is set to be 6 and 4, respectively. In the following equation, `q` is a batch of query points with a batch size `B`, where `L` = 6 is the number of encoding functions. After the coordinates of `q` are multiplied by 2π2⁰, a sin function acts on them element-wisely, and a cos function also acts on them element-wisely. The operations of the two triangular functions are appended to `q` to construct a list with nine elements: [`q`, sin(2π2⁰`q`), cos(2π2⁰`q`)] at frequency 2⁰.

```
sin(2π2ⁱq) = sin(2π2ⁱ [ q_x1 q_y1 q_z1; q_x2 q_y2 q_z2; ...; q_xB q_yB q_zB ]) i ∈ [0, (L - 1)]
```

The list of position encoding results of `q` are concatenated to get a tensor with shape `B`×(3+3×2×`L`) as one of two inputs of an MLP model defined in Cell 05. With the above background information, it should be easy to understand the codes of the tiny NeRF project listed in appendix [K](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-K). My codes are inspired by [Bmild](https://github.com/bmild/nerf/blob/master/tiny_nerf.ipynb). Model training time is about 125 min for 128 query points on each ray, and PSNR value is around 28.5. The trained MLP model is then saved by codes in Cell 13. The size of the saved model file is 301 kB. Running code in Cell 14, we can load the saved model to synthesize a Lego image at any `θ` and `φ` angles for a distance `r` around 4. The right image shown in figure [12.7](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig7) is the output of the following codes. You can change the values of theta, phi and `r` on the first line of following function to see different synthesized images. To improve the quality of the synthesized images, we need to increase the sample points on each ray, but we will have issues about the limit of GPU memory and model training time. Now we have many new NeRF algorithms enabling us to reconstruct photorealistic videos in real time. The development of computer vision is very fast. Some techniques in the book are obsolete when you are reading the book.

![](images/bk978-0-7503-6244-3ch12uf7_pr.gif)

| Point | | Red color | | Green color | | Blue color | | Density |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 01 | | `α[1]r[1]` | | `α[1]g[1]` | | `α[1]b[1]` | | `σ[1]` |
| 02 | | `α[2]r[2]β[1]` | | `α[2]g[2]β[1]` | | `α[2]b[2]β[1]` | | `σ[2]` |
| 03 | | `α[3]r[3]β[1]β[2]` | | `α[3]g[3]β[1]β[2]` | | `α[3]b[3]β[1]β[2]` | | `σ[3]` |
| … | | … | | … | | … | | … |
| 32 | | `α₃₂r₁₂₈∏ᵢ₌₁³¹βᵢ` | | `α₃₂g₃₂∏ᵢ₌₁³¹βᵢ` | | `α₃₂b₃₂∏ᵢ₌₁³¹βᵢ` | | `σ[32]` |

![Figure 12.7. Using a trained tiny NeRF model to synthesize a tiny Lego image at any θ and φ angles with a distance r around 4. (left) Image of the ground truth; (right) a synthesized tiny Lego image with theta, phi, r = 135°, -45°, 4.The tiny Lego image is reproduced with MIT license from Mildenhall et al (2020) (the authors of the original NeRF paper) and Yen-Chen Lin, the owner of ‘NeRF-pytorch’ GitHub repository.](images/bk978-0-7503-6244-3ch12f7_online.jpg)

**Figure 12.7.** Using a trained tiny NeRF model to synthesize a tiny Lego image at any `θ` and `φ` angles with a distance `r` around 4. (left) Image of the ground truth; (right) a synthesized tiny Lego image with theta, phi, `r` = 135°, -45°, 4. The tiny Lego image is reproduced with MIT license from Mildenhall *et al* ([2020](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib7)) (the authors of the original NeRF paper) and Yen-Chen Lin, the owner of ‘NeRF-pytorch’ GitHub [repository](https://github.com/yenchenlin/nerf-pytorch/tree/master/configs).

### 12.3 Introduce 3D Gaussian splatting by 2D Gaussian splatting
