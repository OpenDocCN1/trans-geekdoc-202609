# 4.5 EXPERIMENT

![](bbox=[0.13953, 0.14286000000000001, 0.8604700000000001, 0.28714999999999996])

FIGURE 4.4. (a) Comparison of EVIL and RigL which leverages the label information to explore the variant parameters. (b) Comparison of different mask initialization strategies.

than full finetuning, our method achieves the best OOD performance on all three datasets. Specifically, there are 1.2%, 2.4%, and 2.0% performance gains on ImageNet, iWildCam, and FMoW datasets, respectively. Therefore, the effectiveness and superiority of the EVIL can be successfully extended to large-scale architectures and datasets.

# 4.5.9 Analytical Studies

In this section, we conduct extensive empirical analyses to exploit why EVIL can achieve effective results. First, we conduct ablation studies to show the effect of leveraging distribution knowledge and the influence of choosing different mask initialization strategies. Then, we conduct parameter sensitivity analysis on the hyperparameter $\alpha$ and $\Delta T$. Furthermore, we show a comparison of EVIL-SAM and SAM by visualizing their sharpness during training. Finally, we show the Hessian spectrum to explain why EVIL achieves effective generalization.

Abl Study. To validate the effectiveness of exploring variant parameters using distribution knowledge, we change the optimization target $L_{var}(g(f_{\theta_{var}}(\mathbfx)), d)$ in Equation (4.4) to $L_{var}(h(f_{\theta_{var}}(\mathbfx)), y)$ which leverages the label information instead. As a result, the changed variant is Rig the Lottery (RigL) [200], which is an effective sparse training method. By comparing EVIL and RigL on DomainBed as shown in Figure 4.4 (a), we can see that EVIL surpasses RigL in all scenarios. Therefore, we can conclude that exploring variant parameters by using the distribution information is essential for OOD generalization.