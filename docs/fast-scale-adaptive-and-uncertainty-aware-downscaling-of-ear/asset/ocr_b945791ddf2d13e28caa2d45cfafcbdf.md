# nature machine intelligence

Article

https://doi.org/10.1038/s42256-025-00980-5

# Fast, scale-adaptive and uncertainty-aware downscaling of Earth system model fields with generative machine learning

+   - Received: 1 March 2024
- Accepted: 20 December 2024
- Published online: 13 March 2025
- Check for updates

Philipp Hess $^{1, 2} \odot$, Michael Aich $^{1, 2}$, Baoxiang Pan $^{3, 5} \&$ Niklas Boers $^{1, 2, 4} \odot$

Accurate and high-resolution Earth system model (ESM) simulations are essential to assess the ecological and socioeconomic impacts of anthropogenic climate change, but are computationally too expensive to be run at sufficiently high spatial resolution. Recent machine learning approaches have shown promising results in downscaling ESM simulations, outperforming state-of-the-art statistical approaches. However, existing methods require computationally costly retraining for each ESM and extrapolate poorly to climates unseen during training. We address these shortcomings by learning a consistency model that efficiently and accurately downscales arbitrary ESM simulations without retraining in a zero-shot manner. Our approach yields probabilistic downscaled fields at a resolution only limited by the observational reference data. We show that the consistency model outperforms state-of-the-art diffusion models at a fraction of the computational cost and maintains high controllability on the downscaling task. Further, our method generalizes to climate states unseen during training without explicitly formulated physical constraints.

Accurate and high-resolution climate simulations are of crucial importance in projecting the climatic, hydrological, ecological and socioeconomic impacts of anthropogenic climate change. Precipitation is one of the most important climate variables, with particularly large impacts, for example, on vegetation and crop yields, infrastructure or the economy $^{1}$. However, it is also the variable that is arguably the most difficult to model and predict, especially extreme precipitation events, resulting from a complex interaction of processes over a large range of spatial and temporal scales that cannot be fully resolved.

Numerical Earth system models (ESMs) are our main tool to project the future evolution of precipitation and its extremes. However, they exhibit biases and have much coarser spatial resolution, on the order of 10–100 km, than that needed for the reliable assessments of impacts of climate change $^{2}$. Therefore, ESM projections have to be downscaled to higher resolution, for which several machine-learning-based

approaches have recently been proposed. Due to the chaotic nature of geophysical fluid dynamics, the trajectory of climate simulations will not match historical observations, requiring approaches suitable for unpaired samples to learn such tasks. Recently, methods from generative deep learning have shown promising results in downsampling or correcting spatial patterns of ESM simulations. Normalizing flows (NFs) $^{6}$ and generative adversarial networks (GANs) $^{3,4,7-9}$ can perform these tasks efficiently in a single step $^{5,10}$. However, NFs often exhibit lower quality, for example, less sharp and less detailed generated images, whereas GANs can suffer from training instabilities and problems such as mode collapse $^{11}$. Moreover, these approaches require computationally expensive retraining of the neural networks for each specific ESM simulation to be processed. This makes downscaling large ESM ensembles, as needed in impact assessments, prohibitively costly and time-consuming.

+   1. $^{1}$Earth System Modelling, School of Engineering and Design, Technical University Munich, Munich, Germany. $^{2}$PotSDam Institute for Climate Impact Research, Potsdam, Germany. $^{3}$Institute of Atmospheric Physics, Chinese Academy of Sciences, Beijing, China. $^{4}$Global Systems Institute and Department of Mathematics, University of Exeter, Exeter, UK. $^{5}$Present address: Institute of Atmospheric Physics, Chinese Academy of Sciences, Beijing, China.

✉ e-mail: philipp.hess@tum.de