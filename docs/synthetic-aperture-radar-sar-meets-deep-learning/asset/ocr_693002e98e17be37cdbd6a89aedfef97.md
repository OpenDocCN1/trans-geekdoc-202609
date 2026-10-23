![](bbox=[0.25, 0.14, 0.7, 0.35])

Figure 15. The comparison results of GASN with Siamese-RPN and Siamese-FC on FPS.

# Table 3. Average tracking performance of simulated Video-SAR data.

| Method | Accuracy | CLE | FPS |
|---|---|---|---|
| MOSSE | 31.21% | 19.76 | 105 |
| KCF | 41.80% | 11.30 | 58 |
| Siamese-FC | 43.67% | 8.46 | 19 |
| Siamese-RPN | 55.61% | 7.94 | 31 |
| GASN (ours) | 60.16% | 6.68 | 32 |

# 4.1.2. Tracking Results with Distractors

To verify that the proposed method only tracks the TOI, we selected two adjacent targets with similar shapes for tracking. Figure 16a,b show the tracking results in the same frame. TOI-2 can be considered a distractor when we want to track TOI-1 in Figure 16a. Similarly, TOI-1 can be considered a distractor when we want to track TOI-2 in Figure 16b. The green box represents the ground truth of the TOI, and the red box represents the tracking results using the proposed method. The overlap between the red and green boxes in both figures is greater than 50%, so the proposed method can accurately track the TOI without errors. The main reasons are as follows: GASN uses the Siamese subnetwork to extract multi-level and more expressive features compared to the traditional methods. In addition, compared to the existing deep learning methods, GASN uses GA-SubNet to provide the general location and shape of the TOI based on the template, which can effectively suppress the distractors. Through the above analysis, we think that the proposed method can accurately track the TOI without errors, although there are distractors in the scene.

![](bbox=[0.25, 0.75, 0.43, 0.88])

(a)

![](bbox=[0.55, 0.75, 0.73, 0.88])

(b)

Figure 16. Tracking results with distractors: (a) TOI-1 in the 51st frame of Video 6; (b) TOI-2 in the 51st frame of Video 6.