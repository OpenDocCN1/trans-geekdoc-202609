![](bbox=[0.15, 0.09, 0.78, 0.42])

Figure 14. Distribution of Δh(q) in five fault modes.

# Table 3. Fault diagnosis results of three methods.

|   | WP–ICA | EEMD–LSSVM | EEMD–Improved-MFDFA |
|---|---|---|---|
| Average detection rate /% | 95.7 | 96.67 | 97.87 |

In this paper, Δ𝑓 and Δh̅(𝑞) were input to the support vector machine as feature vectors for classification. The classification results are shown in Table 3. In the same circuit environment, the recognition rate of the proposed method in this paper can reach 97.87%, while the recognition rates of the other two methods are 95.7% and 96.67%. This shows that the method proposed in this paper has more advantages in circuit soft fault identification.

In order to better verify the effectiveness of the method in this paper, the method in this paper is used in the fault feature extraction of three different circuits, namely, Sallen–Key lowpass filter, state-variable filter, and active dual second-order bandpass filter, and compared with the CBAM–CNN analog circuit fault diagnosis method from the literature [17], the FFT–CNN–GRU analog circuit fault diagnosis method from the literature [18], and the MLLE–CHMM analog circuit fault diagnosis method from the literature [19]. The diagnosis results are shown in the following table.

From Table 4, it can be seen that the method in this paper is still very effective in circuit fault feature extraction even under different circuit models, while the diagnosis rate shows that the method in this paper is more advantageous than other methods with higher recognition rate.

# Table 4. Diagnostic results of the corresponding methods under the three circuit models.

| Circuit Models | Method | Diagnosis Rate (%) |
|---|---|---|
| Sallen-Key lowpass filter | EEMD-Improved MF-DFA | 96.31 |
|  | CBAM-CNN | 95.48 |
| State-variable filters | EEMD-Improved MF-DFA | 97.785 |
|  | FFT-CNN-GRU | 97.778 |
| Active dual second-order bandpass filter | EEMD-Improved MF-DFA | 96.32 |
|  | MLLE-CHMM | 95.04 |