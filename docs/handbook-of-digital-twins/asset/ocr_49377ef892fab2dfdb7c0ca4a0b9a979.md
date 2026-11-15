crack gradually grows across the thickness and then transforms into a through-thickness crack.

The comparison of the crack growth simulation and the round-robin test data is shown in Figure 43.3b, from which we can see that fairly good agreements are obtained. In the first 150hours, the predicted growth is slightly faster than that in the test, while after that, the predicted crack growth is slightly slower.

# 43.5 Digital Twin–Driven Damage Diagnosis and Prognosis

In traditional aircraft structural management, the influence of various uncertainties on fatigue crack growth is not considered, which affects the damage state of each aircraft significantly. In order to effectively track the damage evolution to support the arrangement of the inspection and maintenance, it is necessary to comprehensively consider the influence of various uncertainties on the damage evolution. In this section, a digital twin in the forms of DBN is constructed, which can integrate various epistemic and aleatory uncertainties. (Epistemic uncertainty is produced by lack of knowledge and is reducible, whereas aleatory uncertainty is a naturally occurring variable that is irreducible [10].) Based on the digital twin model, the diagnosis and prognosis of the damaged structures are conducted, where the measured crack lengths are used as observations to update the digital twin to improve the accuracy of damage prognosis and remaining useful life prediction.

# 43.5.1 Constructing the Digital Twin by the Dynamic Bayesian Network

For the crack growth problem, the state of interest is the crack length vector $\mathbf{a}$. The fatigue crack growth law is as follows:

$$\frac{da}{dN} = f(\mathbf{a}, \Delta \mathbf{K}; \boldsymbol{\mu})$$ (43.17)

where $\frac{da}{dN}$ are the increments of crack lengths per cycle, $\mathbf{a}$ are the crack lengths, $\Delta \mathbf{K}$ are the ranges of SIFs, and $\boldsymbol{\mu}$ are the material parameters, which are considered as uncertain parameters.

Appending unknown material parameters $\boldsymbol{\mu}$ to crack lengths $\mathbf{a}$ at time step $t$, the augmented state vector is defined as $\mathbf{X}_t = [\mathbf{a}_t, \boldsymbol{\mu}_t]^T$. The functional relationship of crack lengths between two adjacent time steps can be obtained as follows:

$$\mathbf{a}_t = \mathbf{a}_{t-1} + \frac{d\mathbf{a}_{t-1}}{dN} \Delta N$$ (43.18)