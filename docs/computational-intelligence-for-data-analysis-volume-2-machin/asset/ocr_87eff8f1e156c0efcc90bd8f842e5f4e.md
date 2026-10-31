| References | Classifier Algorithm Used | Accuracy |
|---|---|---|
| [19] | SVM with Gaussian kernel | 66.9%. |
| [26] | KNN | 86.1% |
| [26] | LS-SVM | 95.6% |
| [26] | Multilayer Perceptron Neural Network (MLPNN) | 92.5% |
| [26] | Naïve Bayes (NB) | 84.4% |
| [26] | Random Forest (RF) | 97.3% |
| [27] | tunable-Q wavelet transform (TQWT) + ensemble empirical mode decomposition (EEMD) + RF | 96.2% |

# APPLICATIONS OF BCI

In this section, we detail the state-of-the-art applications of BCI. Several studies are underway to enhance current BCI systems by combining multimodal signal acquisition methods. Several studies have demonstrated that fMRI with simultaneous EEG can yield complementary features through the use of the EEG's effective spatial resolution and the EEG's effective temporal resolution, according to Debener et al. [28]. MEG, as mentioned by Kauhanen et al. [29], can also work in conjunction with EEG, since it provides information regarding radially/tangentially polarized sources in cortical-subcortical networks, and can complement the EEG by adding complementary information. Few studies, such as Min et al. [30], and Piastra et al. [31], contend that EEG and MEG can detect subcortical activities; however, skepticism remains regarding their capability to detect brain activities that originate from subcortical areas. It has become increasingly common to combine different signal acquisition methods for improving BCI efficiency in recent years.

In order to translate any brain signal into a command that can be used by a computer or other external device, signal processing combined with ML techniques plays a crucial role. Time-domain representations of the brain signals include the Fourier transform (FT) and autoregressive models, whereas time-frequency representations include short-time FTs and wavelet transforms, as described by Bashashati et al. [32]. When spatial filtering is considered, as described by Saha et al. [33], many inverse models enable the differentiation and projection of actual sources on three-dimensional cortical-subcortical networks. A variety of linear and nonlinear classification algorithms, such as kernel-based support vector machines and linear discriminant analysis can be used to translate the extracted features, as described by Lotte et al. [34]. A deeper understanding of BCI based on deep learning paradigms is receiving increasing attention from researchers thanks to the remarkable advancements in computational