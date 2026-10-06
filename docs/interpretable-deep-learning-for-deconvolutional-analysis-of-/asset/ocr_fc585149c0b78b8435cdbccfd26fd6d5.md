# Neuron
NeuroSource

leveraging the interpretability of learned kernels in pre-defined bases. However, without a kernel-framework, such interpretable kernels are unknown *a priori*. In this context, DUNL replaces approaches like GP-GLM, where temporal kernels are learned rather than predefined.⁷²

Finally, compared DUNL with LFADS using the same windowed dopamine spike correlation. Spearman's rank correlation analysis between LF factors and DUNL's decoded codes for reward responses (Figure 5B) further reveals that LF factors represent better value information, liking-like characterization. This may result from LFADS's more expressive architecture, which overfits at the cost of consistency and interpretability.

To evaluate our choice of kernel selection in Figure 3, we examine the interactions between the chosen kernels in the decomposition of the raw data. We observed that many kernels lack an absence-like response (i.e., an early transient increase in activity that is invariant to reward), likely because the sensor-related signal had not yet decayed to baseline, potentially masking the salience response. Due to the sensor's offset onset dynamics, we observed salience-coupled positive responses for high-reward trials and low negative responses for reward trials. Given the temporal dynamics of positive and negative signals, we decoded reward responses into two types: salience and value-like both kernels mixing of salience and value information. Consequently, both kernels became correlated with reward.

# Dopamine calcium experiment

# Model details

SeqNMF is designed to learn population structure by deconvolve the local kernels spanning the neurons appearing at different times. In experiments, the decomposition of two temporal local kernels, SeqNMF identified only one and aligned kernels with event on, producing a less sparse representation despite regularization (Figure 1A).

# Decomposition property

We compared DUNL with PCA and MNF. The trial-specific coefficients and Spearman's rank correlation between neural coefficients across trials do not align with DUNL's decoded codes (Figures 5C and B). For PCA, this arises from the dissimilarity of learned kernels to known salience and reward responses. For NMF, learned kernels are similar to those in DUNL, the non-negative constraints prevent NMF from capturing spiking in neural responses, leading to lower Spearman's rank correlation to reward. Poisson-functional⁶³ is interpretable for saliency data, but lacks temporal dynamics. It also lacks flexibility for event-related features absent in PCA, NMF, and Poisson-functional PCA. ⁶⁴ Additionally, we compared DUNL with LFADS using the same dopamine spike data. LFADS successfully estimated reward rates in each trial, the learned factors lacked salience-like interpretability.

# Model training details

# Dopamine spiking experiment

The dataset consists of $N = 40$ recorded dopamine neurons, the number of trials from $J = 121$. For surprise trials, we use data from 1 second before the reward to 2 seconds after the reward. For expected trials, we use data from 1 second before the kernel to cover 0.8 seconds after the reward. For more details on data acquisition, see ⁶⁵.

We used the Binomial distribution with a time-bin of 25ms for ms decoding. We set $K = 3$ to learn the neural response to the reward, and the other two to represent salience and the reward prediction error responses. The baseline rate, $r_i$, is estimated for each trial. For stability, with rates lower than 0.001 are set to 0.001. We learned the three kernels, we for each kernel through the log function. In addition to the projection $p$, we apply ReLU($$) projection after backpropagation to enforce non-negativity. To enforce sparsity for each kernel indicator, the kernel value $c_i$ is set to 1 at the event onset and trial, with the event indicators set to zero at all time. The data, model, and training parameters are summarized in Table S2. For the attempted scenario, 685 out of the 780 trials were used for training; in this case, the kernel sparsity is set to 0.005.

# Dopamine calcium experiment

The data is captured from three sessions, with $N = 62$, and 30 trials. Data, model, and training are summarized in Table S3. Below, we provide a detailed explanation of the methodology. Given the continuous nature of calcium activity, we modeled the data using a Gaussian distribution. We use $K = 5$ kernels: one kernel to characterize neural activity in response to the odor with a reward (referred to as reward), another for the odor in expected trials prior to reward, and three kernels to model reward prediction error responses (RPEs). For RPEs, we use one with a non-negative kernel to model salience and two kernels to model value (one with a non-negative