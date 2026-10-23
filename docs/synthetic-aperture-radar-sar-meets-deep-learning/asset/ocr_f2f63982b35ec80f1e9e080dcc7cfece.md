# 5. Discussion

The four graphs in Figure 16 show some errors in the visualized results. It can be seen that (a) there are obvious detection frames to identify a ship, picture (b) has obvious undetected ships detected, and picture (c) has obvious detection frames to identify multiple ships, while one ship is detected by multiple ships. In (d), there are multiple ships that have not been recognized. We can solve the problem of the difficult identification of neighboring ships by segmentation, and introduce nonlocal mean models to highlight edge information.

![](bbox=[0.09, 0.28, 0.42, 0.51])

![](bbox=[0.48, 0.28, 0.84, 0.51])

![](bbox=[0.09, 0.52, 0.42, 0.75])

![](bbox=[0.48, 0.52, 0.84, 0.75])

Figure 16. Visualization results of misdetected samples. (a–d) are the inshore visualization results of the CRTransSar method under the SSDD dataset. (a,c,d) are the visualization results of false-alarms. (b,d) are the visualization results of missed-detection.

# 6. Conclusions

SAR target detection has important application value in military and civilian fields. Aiming to overcome the difficulties of SAR targets, such as strong scattering, sparseness, multiscale, unclear contour information, and complex interference, we propose a visual transformer SAR target detection framework based on contextual joint representation learning, called CRTransSar. In this paper, CNN and the transformer are innovatively combined to improve the feature representation and the detectability of SAR targets in a balanced manner. This study was based on the use of a Swin Transformer and integrates CNN architecture ideas. We also redesigned a new backbone, named CRbackbone, which