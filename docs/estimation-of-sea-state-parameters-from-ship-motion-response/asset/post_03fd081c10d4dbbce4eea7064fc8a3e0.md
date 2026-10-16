
![](img/4734fbdc67cafcec90fddf3b05be1d58_2_0.png)

Fig. 2. Ship motion responses in six degrees of freedom (6-DOF).

![](img/4734fbdc67cafcec90fddf3b05be1d58_2_1.png)

Fig. 3. Unidirectional one-dimensional Bretschneider wave spectrum with H_s = 3.0 m and T_z = 4.0 s.

Table 1
Main characteristics of the Bulk Carrier ship.
| Name | Value |
|---|---|
| Length L_pp | 160.4 m |
| Breadth B | 27.2 m |
| Draught T | 6.55 m |
| Metacentric height G_M | 3.97 m |
| Block coefficient C_B | 0.77 |
| Displacement | 22,193 t |

With respect to the heading to the waves, β. In this case wave elevation can be expressed as a sum of multiple sinusoidal (regular) wave components:

ζ(x,t) = Σ_{i=1}^{n} A_i cos(ω_i t - k_i x + ε_i)   (1)

where ω_i is a wave frequency of a particular wave component, k_i is a wave number, and ε_i is the random phase shift in the range [0,2π] to ensure random nature of the waves. The amplitude A_i can be found from the relation to the wave spectrum S(ω), given with Eq. (2):

½ A_i² = S(ω_i) Δω_i   (2)

where considered frequency interval Δω_i has randomly distributed boundaries.

Wave spectrum S(ω) is given in the frequency domain and describes how the total wave energy of all wave frequencies ω_i is distributed in stationary seaway (Faltinsen, 1990). It can be estimated by one of the well-known spectra suggested by the International Towing Tank Conference (ITTC, 1969). In the case of fully developed seas, the recommendation is to use the two-parameter Bretschneider spectrum, cf. Eq. (3).

S(ω) = 124 H_s² / T_z⁴ ω^{-5} exp(-496 / (T_z⁴ ω⁴))   (3)

Eq. (3) is given in a rewritten form as the characteristic statistical period of interest is zero up-crossing period T_z, with a relation to mean wave period T_1, T_1 = 1.087 T_z and peak period T_p, T_p = 1.405 T_z. H_s represents significant wave height, and ω is the wave frequency (DNV-GL, 2018).

The energy distribution, in an example of two-parameter Bretschneider spectrum, is given in Fig. 3 with values of H_s = 3.0 m and T_z = 4.0 s. The one-dimensional spectrum has a single peak value indicating that unimodal seas are being observed. The single peak value occurs at an angular frequency ω_p = 1.12 rad/s, corresponding to the above relations for the peak period T_p and zero up-crossing period T_z since ω_p = 2π / T_p. Also, the supplied spectrum includes information on the significant wave height H_s, which can be determined from the area under the spectrum. It should be noted that, for practicality and simplicity reasons, generated time-series do not contain information about wave directionality. In other words, we only observe long-crested or unidirectional waves with a narrow spreading.

While routing, the ship is observed as a complex object with the forward speed U, and it is encountered by waves at a specific encounter angle β. Encountered wave spectrum is not equal to wave spectrum given in wave frequency domain ω due to Doppler shift. Therefore, ship responses should be observed in the encounter frequency domain ω_e. The following expression applies to the transformation from wave to encounter frequency domain:

ω_e = ω - ω² U / g cos(β)   (4)

with g being the gravitational constant in the adopted right-handed coordinate system, where the encounter angle of 180 deg indicates head seas.

Given ship speed and heading angle, we can easily calculate the encounter period from the wave period. The encounter period is significant since it represents the period when the ship encounters waves. Consequently, substantial ship motions may occur if it coincides with the natural ship motion period. Since it depends on the ship's speed and course angle, in addition to the wave frequency, the captain can “control” it by adjusting the ship's speed or course angle.

With known encounter wave spectrum and appropriate complex-valued transfer functions Φ_R, one can calculate the time-series of ship motion responses R_i(t) following (Denis and Pierson, 1953):

R_i(t) = Σ_{i=1}^{n} A_i |Φ_R(ω_{e,i})| cos(ω_{e,i} t + ε_i)   (5)

where frequency discretization is non-equidistant, and amplitude A_i is given in wave frequency domain ω as stated in Eq. (2). Since the unidirectional spectrum is observed, each set of time-series R_i(t) is generated for a single encounter angle β, with other wave characteristics contained in the amplitude A_i.

Transfer functions are computed with a strip theory solver for pitch, roll and heave as a function of encounter frequency ω_e and encounter angle β. Forward speed was 16.19 knots, and relative wave directions were discretized into 36 headings for [0,360]deg, with other values obtained by linear interpolation. The range of wave frequencies ω are defined as [0,4.0] rad/s. The ship under study was a 20,000 DWT Bulk Carrier, with the primary characteristics shown in Table 1. The amplitudes of frequency response functions for heave, pitch, and roll motions are given in Fig. 4 with relative wave direction β = 150 deg and ship forward speed U = 16.19 knots.

By applying Eq. (5), we computed time-series of motion responses in 3-DOF, with a sampling frequency of 5 Hz and sample lengths of 300 s. An example of time-series responses is given in Fig. 5.

![](img/4734fbdc67cafcec90fddf3b05be1d58_3_0.png)

**Fig. 4.** Amplitudes of transfer functions for heave, pitch and roll responses with different relative wave directions (β = 90 deg., β = 150 deg. and β = 180 deg.) and ship forward speed $U = 16.19$ knots.

![](img/4734fbdc67cafcec90fddf3b05be1d58_3_1.png)

**Fig. 5.** Calculated time-series of ship motion responses at ship forward speed $U = 16.19$ knots and sea state parameters $H_s = 3.0$ m, $T_z = 4.0$ s and β = 150 deg.

We design Latin hypercube sampling (LHS) to discretize the three-dimensional search space of $H_s$, $T_z$ and β with a 20,000 number of sample points at a uniform distance. The range of validity for parameter $H_s$ is [0.5, 10.5] m and [3.5, 9.6] s for parameter $T_z$. The encounter angle β is defined in range [0, 360] deg. In addition, following (Mittendorf et al., 2022) work, constraints for irregular waves are applied to include wave breaking conditions in the sense of moderate wave steepness with a limited maximum value $S_s$ given as DNV-GL (2018):

$$S_s = \begin{cases} \frac{1}{10} & \text{for } T_z \leq 6\ s \\ \frac{1}{15} & \text{for } T_z \geq 12\ s \end{cases} \tag{6}$$

Finding the values between the limits given in the above equation is done with linear interpolation. The dataset contained about 13,000 samples after these constraints were applied. The final three-dimensional search space of $H_s$, $T_z$, and β was sampled by the LHS. Since the LHS method helps to ensure that the samples are spread out evenly and reduces the possibility that some of the samples are left out in the given range, it was a useful tool for our simulation and experimentation. LHS is also computationally less expensive than the standard Monte Carlo sampling. This may not be as significant with modern computers, but it was used since it may give marginally more accurate results in terms of true variability (given the amount of processing time).

Fig. 3 shows an example of a 2D representation of a wave spectrum using a selected distributed parameter pair ($H_s$ and $T_z$). If the third parameter from the three-dimensional search space (the direction of the wave β) is taken into account, it is possible to obtain a directional wave spectrum.

The following is a detailed description of the data augmentation process and the NN architectures which are used to create the DL models.

## 2.2. Data preprocessing

Input–output samples were prepared for models’ training in the form of JSON files, and subsequently processed and scaled. The output values of the sea state parameters were scaled so that $H_s$ and $T_z$ were divided by a value of 15, and the relative wave direction β values were divided by the value of 360. The extensive experimentation showed that the scaling of input data (3-DOF) is not influencing the convergence of the tested models. However, the convergence of models is greatly influenced by the output scale (set to be between 0 and 1). By choosing scaling values of 15 and 360 as maximum values in our dataset enlarged by 10%, we have ensured the fulfillment of these conditions.

Data augmentation strategies are employed in the data preprocessing step to increase the accuracy of our models. With data augmentation applied to proposed models, we increase the variety of our data and eliminate overfitting.

Next, we explain the utilized data augmentation methods. Fig. 6 shows one batch with $n = 32$ samples. Each sample in the batch consists of three time-series input data of ship motion responses, denoted as $M_1$, $M_2$ and $M_3$. Within each batch, sampling with size $s = 32$ was performed resulting in $k = 47$ sub-samples of each input data.

Fig. 7 compares transformations on how the sub-samples of each input data are shuffled. We distinguish two different approaches: batch-wise and row-wise types of augmentation. Comparison is given using one batch with $n = 3$ samples and $k = 3$ tokens. As depicted in the figure, batch-wise augmentation randomly shuffles the input data signals so that all rows shuffle simultaneously in the same manner. Row-wise augmentation, on the other hand, shuffles each data sample separately. To compare the results, all DL models were trained without any augmentation, as well as with batch-wise and row-wise data augmentation. The trained models always outperformed those not using the above data augmentations.

Besides the results confirming the benefits of utilizing the row-wise and batch-wise augmentation, it is necessary to elaborate more on what the utilized augmentation does to the model training. Similar to the “mosaic” and “bag of freebies” augmentation introduced in YoloV4 paper, the utilized augmentations also deal with variation in data (Bochkovskiy et al., 2020). The general idea is to permute the data chunks to force the model to learn different relations between the chunks and to make the whole problem more demanding. By introducing more variations in the data, the model is forced to learn more in-depth relations in the scattered patterns. Hence, the row-wise and batch-wise augmentation differ in the number of permutations (increased variance) they introduce into the data during the models’ training. The batch-wise augmentation introduces less variation in the training because all samples in the batch are rearranged with the same random seed. On the contrary, row-wise augmentation is more costly for numeric operations but introduces more variation to the dataset due to the per-sample random seed. Based on our evaluation, we cannot single out the best approach for all methods — some methods benefit more from batch-wise augmentation, while others perform better with
