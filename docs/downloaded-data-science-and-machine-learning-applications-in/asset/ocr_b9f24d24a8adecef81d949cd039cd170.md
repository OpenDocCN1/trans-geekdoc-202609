# 3.5 Numerical Simulator and Machine Learning Computational Time

Figure 7.9 shows the simulation time for the CMG commercial numerical simulator and the machine learning algorithms using Intel core i5 – 11400H, 4.5 GHz 6Core, and 16 GB of RAM. It can be seen that the numerical simulation took a long runtime to execute. Also, this significant reduction in simulation time indicates the robustness of the machine-learning proxy models (MARS and GMDH). Furthermore, the proxy models can serve as substitutes for direct simulation of CO₂-LSWAG for design parameters within the ranges considered. In summary, using a GPU (graphics processing unit) could further improve the computational time of this machine-learning algorithm. In comparison to using a GPU, this method may offer even greater benefits in terms of speed and efficiency when running multiple simulations at the same time.

![](bbox=[0.18, 0.42, 0.78, 0.73])

Fig. 7.9. Simulation time for machine learning and numerical models.

# 4. Conclusion

The problem addressed in this study is the lack of attention and research on using machine learning techniques to use CO₂-LSWAG for EOR in carbonate reservoirs. The quality and composition of the water used in most EOR processes are not adequately considered, and there is a need for fast computational methods for predicting future recovery factors. We used multiphase multicomponent flow equations, geochemical modelling, and compositional simulation datasets to build proxy models for predicting oil recovery factors in carbonate reservoirs for CO₂-LSWAG EOR. Two supervised machine learning models (MARS and GMDH) were used to