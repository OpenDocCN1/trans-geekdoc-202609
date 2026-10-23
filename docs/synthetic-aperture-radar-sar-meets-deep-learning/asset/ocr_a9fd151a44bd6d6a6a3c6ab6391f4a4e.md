This paper quotes the latest SAR target detection methods, FBR-Net [50], Center-Net++ [51], NNAM [52], DCMSNM [53], and DAPN [54]. Since the relevant papers do not have specific data divisions, this paper has no way to fully reproduce the results from other relevant papers. Therefore, this paper can only quote them. The results are compared horizontally, as shown in Table 7.

**Table 7.** Comparison with the latest SAR target detection method.

| Method | P | R | F1 | mAP |
|---|---:|---:|---:|---:|
| FBR-Net [50] | 0.928 | 0.940 | 0.934 | 0.941 |
| CenterNet++ [51] | 0.833 | 0.952 | 0.889 | 0.951 |
| NNAM [52] | 0.843 | 0.851 | 0.849 | 0.798 |
| DCMSNM [53] | 0.836 | 0.834 | 0.835 | 0.896 |
| DAPN [54] | 0.711 | 0.909 | 0.798 | 0.898 |
| CRTransSar (Ours) | 0.925 | 0.983 | 0.953 | 0.970 |

To demonstrate the robustness of our proposed algorithm, we conducted comparative experiments with low SNR on salt and pepper noise, random noise, and Gaussian noise. In the salt and pepper noise experiments, our method led to mAP of 94.8. The map of our method was 5.5% higher than Yolo v3 and 9.7% higher than Faster R-CNN. In the random noise experiments, our method led to mAP of 96.7. The map of our method was 3% higher than Yolo v3 and 11.1% higher than Faster R-CNN. In the Gaussian noise experiments, our method led to mAP of 95.8. The map of our method was 1% higher than Yolo v3 and 10.7% higher than Faster R-CNN. The experimental results, presented in Table 8, show that we produced a reliable performance for SAR target detection tasks in low SNR.

**Table 8.** Comparison with low SNR of other advanced methods.

| Method | Salt and Pepper Noise: P | Salt and Pepper Noise: R | Salt and Pepper Noise: mAP | Salt and Pepper Noise: F1 | Gaussian Noise: P | Gaussian Noise: R | Gaussian Noise: mAP | Gaussian Noise: F1 | Random Noise: P | Random Noise: R | Random Noise: mAP | Random Noise: F1 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Faster R-CNN | 80.0 | 92.7 | 85.1 | 85.9 | 79.2 | 92.4 | 85.1 | 85.3 | 79.8 | 92.5 | 85.6 | 85.7 |
| YOLO | 84.3 | 93.4 | 89.3 | 88.6 | 89.4 | 97.2 | 94.8 | 93.1 | 88.7 | 97.2 | 93.7 | 92.7 |
| CRTransSar (Ours) | 90.2 | 96.7 | 94.8 | 93.3 | 90.0 | 97.8 | 95.8 | 93.7 | 91.3 | 98.2 | 96.7 | 94.6 |

In order for our proposed method to effectively solve the SAR target detection task, we also made corresponding experimental comparisons for the computational cost of the Swin Transformer. The FPS and parameter statistics of several representative target detection algorithms are shown in Table 9. Compared with the single-stage target detection algorithm, our parameter was 34M higher than YOLO v3, and the FPS was 28.5M lower, but the mAP was 1.9% higher than YOLO v3. Compared with two-stage target detection, the parameter amount was 52M higher than Faster R-CNN, and the FPS was 11.5M lower. Compared with Cascade R-CNN, the parameter amount was 8M higher and the FPS was 4.5M lower. Compared with Cascade Mask R-CNN, the number of parameters was 19M higher and the FPS was 7.5M lower; moreover, our mAP was 8.5% higher than that of Faster R-CNN, 7.7% higher than that of Cascade R-CNN, and 6.8% higher than that of Cascade Mask R-CNN. Because the overall architecture of the Swin Transformer is still relatively large, the large volume of Transformer is a general problem in this field, and we plan to make further improvements in model lightweighting and compression in the future.