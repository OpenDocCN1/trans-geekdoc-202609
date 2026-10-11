
## 9.2.5 Uplink Power Prediction with Machine Learning

This section summarizes the work on ML-based uplink power prediction according to [\[207\]](#backmatter-001.xhtml#b_9783110785944-010_ref_207). Energy-aware system design is an important optimization task for static and mobile IoT-based sensor nodes, especially for highly resource-constrained vehicles such as mobile robotic systems. For 4G/5G-based cellular communication systems, the effective transmission power of uplink data transmissions is of crucial importance for the overall system power consumption. Unfortunately, this information is usually hidden within off-the-shelf modems and mobile handsets and can therefore not be exploited for green communications. Moreover, the dynamic transmission power control behavior of the mobile device is not explicitly modeled in most of the established simulation frameworks.

In order to close this gap, we present a novel machine learning-based approach for forecasting the uplink transmission power used for data transmissions based on available passive network quality indicators and application-level information. A schematic illustration of the proposed solution approach is shown in [Figure 9.15](#9783110785937_093138.xhtml#b_9783110785944-009_fig_015). The key idea is to leverage an `SDR` (Software-Defined Radio)-based measurement setup—capable of simultaneously determining the uplink transmission power `P_TX` and different network context indicators—in order to derive a machine learning-based prediction model that infers `P_TX` from the context measurements. This model can then be deployed to other platforms that are not capable of determining `P_TX` on their own.

The required machine learning model is derived from comprehensive field measurements of drive tests performed in a public cellular network and can be parameterized for integrating all measurements that a given target platform is able to provide for the prediction process. [Figure 9.16](#9783110785937_093138.xhtml#b_9783110785944-009_fig_016) shows a road map of the measurement points along a vehicular trajectory that covers urban, suburban, and rural environments. In total, 6172 have been acquired during the real world measurements. In focusing on the platform’s sensing capabilities, we considered four different variants of feature sets. A summary of the feature sets and the implied impact factors of the contained features is given in [Table 9.3](#9783110785937_093138.xhtml#b_9783110785944-009_tab_003).

![Fig. 9.16 Road map with locations of all data samples of the measurement campaign between two larger cities in Germany. Each blue point represents an intermediate status logging of all measured variables (cf. Table 9.3) during ongoing uplink transmissions. (Map: ©OpenStreetMap contributors, CC BY-SA). ©\[2018\] IEEE. Reprinted, with permission, from \[207\].](graphic/b_9783110785944-009_fig_016.png)

**Fig. 9.16** Road map with locations of all data samples of the measurement campaign between two larger cities in Germany. Each blue point represents an intermediate status logging of all measured variables (cf. Table 9.3) during ongoing uplink transmissions. (Map: ©OpenStreetMap contributors, CC BY-SA). ©\[2018\] IEEE. Reprinted, with permission, from [\[207\]](#backmatter-001.xhtml#b_9783110785944-010_ref_207).

For performing the actual prediction task, different regression models are considered:

*   **Random Forest** with 64 trees and a maximum depth of 32.
*   **Deep Learning** with three fully connected hidden layers, 64 neurons per layer, and Rectified Linear Unit (`ReLU`) activation function.
*   **Ridge Regression** with 12 model parameters (one per feature plus one bias term).

The results of the 10-fold cross validation are summarized in [Figure 9.17](#9783110785937_093138.xhtml#b_9783110785944-009_fig_017). While the differences between the feature set variants are comparably small, larger differences between the machine learning models can be observed. The Random-Forest models thoroughly performed best with a mean average error of 3.166 dB. It can also be seen that the standard deviation between the different cross validation runs is small, which indicates a good model fit to unknown and independent data.

**Tab. 9.3** Captured features and association with application-specific prediction models based on full-feature set `F`, practical sets `P1`/`P2`, and simulation set `S`. ©\[2018\] IEEE. Reprinted, with permission, from [\[207\]](#backmatter-001.xhtml#b_9783110785944-010_ref_207).

| Parameter | Model | Indicated Influences(s) |
| --- | --- | --- |
| Velocity | `F`, `P1`, `P2`, `S` | Distortions by fast fading |
| Upload size | `F`, `P1`, `P2`, `S` | Influence of TCP slow start |
| RSRP | `F`, `P1`, `P2`, `S` | Signal strength, distance |
| RSRQ, SINR | `F`, `P1`, `P2` | Signal clarity, interference |
| Datarate | `F`, `P1` | Signal strength, allocated RBs `M` |
| RSSI | `F` | Signal strength, distance |
| Frequency band | `F` | Environment [\[349\]](#backmatter-001.xhtml#b_9783110785944-010_ref_349) |
| Number of neighbor cells (intra/inter freq.) | `F` | Environment, cell density, interference |
| Cell bandwidth | `F` | Exhaustion of TX-power headroom |

![Fig. 9.17 Cross-validated error of trained prediction models for each feature subset (F, P1, P2, S) and each machine learning method (Random Forest, Deep Learning, Ridge Regression) in terms of Root Mean Squared Error (RMSE) (left) and Mean Absolute Error (MAE) (right). Lower is better. ©\[2018\] IEEE. Reprinted, with permission, from \[207\].](graphic/b_9783110785944-009_fig_017.png)

**Fig. 9.17** Cross-validated error of trained prediction models for each feature subset (`F`, `P1`, `P2`, `S`) and each machine learning method (Random Forest, Deep Learning, Ridge Regression) in terms of Root Mean Squared Error (`RMSE`) (left) and Mean Absolute Error (`MAE`) (right). Lower is better. ©\[2018\] IEEE. Reprinted, with permission, from [\[207\]](#backmatter-001.xhtml#b_9783110785944-010_ref_207).

## Notes

# Bibliography

[1] D. J. Abadi et al. “Aurora: A New Model and Architecture for Data Stream Management”. In: *The VLDB Journal – The Int. Journal on Very Large Data Bases* 12.2 (Aug. 2003), pp. 120–139 (cit. on p. 21). [→](#9783110785937_002446.xhtml#xref_d1990e2155)

[2] M. R. Ackermann, J. Blömer, and C. Sohler. “Clustering for Metric and Nonmetric Distance Measures”. In: *ACM Transactions on Algorithms* 6.4 (2010). Previously appeared in the Procs. of the Symposium on Discrete Algorithms 2008, 59:1–59:26 (cit. on pp. 201, 203, 204). [a](#9783110785937_041148.xhtml#xref_d1990e49651), [b](#9783110785937_041148.xhtml#xref_d1990e49734), [c](#9783110785937_041148.xhtml#xref_d1990e50684), [d](#9783110785937_041148.xhtml#xref_d1990e50691)

[3] C. Adam-Bourdarios, G. Cowan, C. Germain, I. Guyon, B. Kégl, and D. Rousseau. “The Higgs boson machine learning challenge”. In: *Advances in Neural Information Processing Systems: Procs. of the Workshop on High-energy Physics and Machine Learning 2015*. 2015, pp. 19–55 (cit. on p. 250). [→](#9783110785937_066530.xhtml#xref_d1990e69623)
