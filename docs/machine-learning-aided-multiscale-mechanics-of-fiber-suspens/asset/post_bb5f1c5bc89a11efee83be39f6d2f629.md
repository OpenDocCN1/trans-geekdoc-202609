
we generate 32 sample viscosities with the procedure described in section 5.3.3, and compute the corresponding effective viscosities. To compute a single effective viscosity, five FFT-based computations are necessary (Bertóti et al., 2021), leading to a total of 4960 computations, and 992 computed effective viscosities. In the previous sections 5.2.3 and 5.3.2, we studied the linear homogenization functions of CLMs, and presented the FDMN architecture to treat infinite material contrast and incompressible materials. In the following, we discuss the material sampling for the offline training, the offline training procedure, and the online evaluation of FDMNs for suspensions of rigid particles.

### 5.4.2 Offline training

With the linear training data at hand, we wish to train FDMNs for the prediction of the non-Newtonian viscous behavior of shear-thinning fiber polymer suspensions. We follow previous work (Gajek et al., 2020; 2021) and choose the depth of the FDMN as \( K = 8 \) to achieve sufficient prediction quality for non-linear computations. An FDMN of depth \( K = 8 \) with CLMs of rank \( R = 3 \) has 512 weights and 638 angles as free parameters, as per equations (5.53) and (5.73). For each microstructure, we define the training data \(\mathcal{S}^D\) as

\[
\mathcal{S}^D = \{(\mathbb{V}_1^s, \mathbb{V}_F, \bar{\mathbb{V}}^s) \mid s \in (1, ..., 32)\}, \quad (5.93)
\]

where \(\mathbb{V}_1^s\) denotes the sample viscosities generated with equation (5.54), \(\mathbb{V}_F\) denotes the infinite viscosity of the rigid fibers, and \(\bar{\mathbb{V}}^s\) stands for the effective viscosity of the sample \( s \). For each microstructure, we split the training data \(\mathcal{S}^D\) into the training set \(\mathcal{S}^t \subset \mathcal{S}^D\) and the validation set \(\mathcal{S}^v \subset \mathcal{S}^D\), which consist of 90% and 10% of the total training data, respectively. The training set \(\mathcal{S}^t\) and the validation set \(\mathcal{S}^v\) share no samples, i.e., \(\mathcal{S}^t \cap \mathcal{S}^v = \varnothing\).

As an initial guess for the FDMN parameters, we uniformly sample all angles $\underline{\alpha}$ and weights $\underline{w}$ from their respective intervals, and rescale the weights $\underline{w}$ such that they sum to unity. Because we use a relatively small set of 32 samples as training data, we dedicate a large portion of it to the training set $\mathcal{S}^t$, and choose to train 20 FDMNs per fiber orientation state $\underline{\lambda}$. Furthermore, we train the FDMNs on mini batches with size $N_{\mathrm{b}} = 8$, for which we draw randomly from the training set $\mathcal{S}^t$. In case the last batch is smaller than eight samples, we drop the batch. Because the initialization of the parameter vectors $\underline{\alpha}$ and $\underline{w}$, as well as the offline training process are random, the FDMNs differ in their parameters and quality of fit. By training 20 FDMNs per fiber orientation state, we leverage this randomness with the goal of obtaining FDMNs with a high quality of fit. This strategy aims to reduce the total computational effort required to obtain sufficiently accurate FDMNs, because repeatedly training FDMNs on 32 samples requires less computational resources than conducting full field simulations for larger sample sizes. For the minimization of the loss function $\mathcal{L}$, we choose the RAdam algorithm (Liu et al., 2019a) and use a learning rate sweep (Smith and Topin, 2019) to determine the learning rates $\kappa_{0, \alpha}$ and $\kappa_{0, w}$. With the learning rate sweep we obtain highly similar learning rates for both parameter groups $\underline{\alpha}$ and $\underline{w}$, such that $\kappa_{0, \alpha} = \kappa_{0, w} = 1 \cdot 10^{-2}$. As the learning process advances, we use PyTorch's StepLR learning rate scheduler to improve convergence towards minima (Darken and Moody, 1990; Darken et al., 1992). To do so, we multiply the learning rates $\kappa_{0, \alpha}$ and $\kappa_{0, w}$ with a constant factor $f_{LR} = 0.75$ every 150 epochs. Other than the learning rates, we used standard hyperparameters for the two momentum coefficients $\beta_1 = 0.9$ and $\beta_2 = 0.999$, as well as the stabilization constant $\varepsilon = 10^{-8}$. Overall, we train every FDMN for a total of 2000 epochs each.

![](img/283dee3537da34c9897f9777475c5d3d_154_0.png)

![](img/283dee3537da34c9897f9777475c5d3d_154_1.png)

(a) Training set $\mathcal{S}^{\text{t}}$

(b) Validation set $\mathcal{S}^{\text{v}}$

Figure 5.6: Minimum, maximum, and average mean error \( e^{\text{mean}} \) of all trained FDMNs for the training set \( \mathcal{S}^{\text{t}} \) (a) and the validation set \( \mathcal{S}^{\text{v}} \) (b). Figure adapted from Sterr et al. (2024a, Figure 6).

To measure the quality of fit, we define the mean error \( e^{\text{mean}} \) over a subset \( \mathcal{S} \) of the training data \( \mathcal{S}^{\text{D}} \) as

\[
e^{\text{mean}} = \frac{1}{|\mathcal{S}|} \sum_{(\mathbb{V}_1^s, \mathbb{V}_F, \bar{\mathbb{V}}^s) \in \mathcal{S}} \frac{\|\mathcal{DMN}_{\text{L}}(\mathbb{V}_1^s, \mathbb{V}_F, \underline{\alpha}, \underline{w}) - \bar{\mathbb{V}}^s\|_1}{\|\bar{\mathbb{V}}^s\|_1}, \quad (5.94)
\]

where \( |\mathcal{S}| \) is the cardinality of the set \( \mathcal{S} \). Depending on the fiber orientation state \( \underline{\lambda} \) and the initial guesses of the angles \( \underline{\alpha} \) and the weights \( \underline{w} \), the quality of fit varies per DMN. Therefore, for the whole training process of all 620 FDMNs, we visualize the smallest mean error \( \min(e^{\text{mean}}) \), the largest mean error \( \max(e^{\text{mean}}) \), and the average mean error \( \text{avg}(e^{\text{mean}}) \) for the training and validation sets \( \mathcal{S}^{\text{t}} \) and \( \mathcal{S}^{\text{v}} \) per epoch in Figure 5.6. For the training and the validation set, we observe that the three considered error measures drop rapidly at the beginning of the training, and continue to improve as the training continues. As the learning rates are small for epochs larger than 1500, the errors do not change significantly at the end of the training process, while the smallest mean error \(\min(e_{\text{t}}^{\text{mean}})\) falls below 0.3%. This indicates a high quality of fit on the training set \(\mathcal{S}^\text{t}\) for all FDMNs. Compared to the training set \(\mathcal{S}^\text{t}\), the spread between the largest mean error \(\max(e_{\text{v}}^{\text{mean}})\) and the smallest mean error \(\min(e_{\text{v}}^{\text{mean}})\) for the validation set \(\mathcal{S}^\text{v}\) is larger. However, the largest mean error \(\max(e_{\text{v}}^{\text{mean}})\) stays below 2% for all considered FDMNs and does not fluctuate by a large margin. Additionally, the average mean error \(\text{avg}(e_{\text{v}}^{\text{mean}})\) decreases continuously during training. Consequently, the prediction quality on both the training and validation set improve on average as the training progresses, although the largest mean validation error \(\max(e_{\text{v}}^{\text{mean}})\) does not improve significantly after 1250 training epochs. Overall, this indicates that no pronounced overfitting to the training data set \(\mathcal{S}^\text{t}\) occurs.

### 5.4.3 Online evaluation

To measure the online performance of an FDMN, we define the online error function \(e_{\text{on}} : \text{Sym}_0(3) \rightarrow \mathbb{R}\) as

\[
e_{\text{on}}(\bar{D}) = \frac{\|\sigma^{DMN}(\bar{D}) - \sigma^{FFT}(\bar{D})\|_2}{\|\sigma^{FFT}(\bar{D})\|_2}, \tag{5.95}
\]

where \(\|\cdot\|_2\) denotes the \(\ell^2\)-norm of the components in Mandel notation, \(\bar{D}\) stands for the prescribed effective strain rate tensor, and \(\sigma^{DMN} : \text{Sym}_0(3) \rightarrow \text{Sym}_0(3)\) and \(\sigma^{FFT} : \text{Sym}_0(3) \rightarrow \text{Sym}_0(3)\) are the stress functions of the FDMN and the FFT-based homogenization, respectively. We then choose the largest error over all load cases \(e_{\text{on}}^{\max}\) and the mean error over all load cases \(e_{\text{on}}^{\text{mean}}\)

\[
e_{\text{on}}^{\max} = \max_{\bar{D} \in \bar{D}_\gamma} e_{\text{on}}, \quad e_{\text{on}}^{\text{mean}} = \frac{1}{|\bar{D}_\gamma|} \sum_{\bar{D} \in \bar{D}_\gamma} e_{\text{on}}(\bar{D}), \tag{5.96}
\]

to study the performance of the different FDMNs. For each investigated orientation state \(\underline{\lambda}\), we identify the FDMN with the smallest maximum
