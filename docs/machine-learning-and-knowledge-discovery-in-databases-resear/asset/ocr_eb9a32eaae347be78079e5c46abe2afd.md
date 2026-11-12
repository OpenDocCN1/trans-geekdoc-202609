Table 1. Feature Reconstruction RMSE ($\times 10^{-4}$) comparison on three datasets. Lower is better. Best result highlighted in bold.

| Model | Cylinder Flow | Pipe Turbulence | Thermochemical Reaction |
| :--- | :--- | :--- | :--- |
| PointMLP | 52.50 | 60.52 | 109.45 |
| AMGNET | 15.76 | 17.63 | 22.17 |
| BSMS-GNN | 3.23 | 3.32 | 3.96 |
| MPG (ours) | **2.72** | **1.74** | **3.94** |

![](bbox=[0.09, 0.24, 0.86, 0.45])

Fig. 4. Rollout Error Snapshots of MeshGraphNets, AMGNET, BSMS, and Our Proposed Model (MPG) on the NSM2d Dataset.

Rollout Prediction and Error Accumulation. For the rollout prediction task (Table 2), conducted on Cylinder Flow, Lid2d, and NSM2d datasets, our MPG model exhibits notably lower error accumulation over the trajectory compared to baselines, particularly on complex mesh structures. Even though single-step prediction errors for Cylinder Flow and NSM2d are similar to BSMS-GNN, MPG achieves these results with approximately only 15% of its parameter count. Figure 4 illustrates the error accumulation over the trajectory for different models, emphasizing the superior performance of MPG in maintaining lower error rates over time.

Computational Efficiency. Notably, the statistics for training and inference time exclude the multi-scale construction, which acts as an independent preprocessing module. As summarized in Table 2, MPG achieves significant improvements in computational efficiency. Specifically, our method reduces training time per epoch by 63.1–86.1% compared to BSMS-GNN, 17.7%–65.3% compared to MeshGraphNets, and 45.0%–73.8% compared to AMGNET across different datasets. Additionally, MPG exhibits a substantial reduction in inference time in the Cylinder Flow and Lid2d datasets. Regarding memory usage, MPG requires less memory than MeshGraphNets and BSMS-GNN. MPG also maintains a lightweight model size, reducing the parameter count by 87.3% com-