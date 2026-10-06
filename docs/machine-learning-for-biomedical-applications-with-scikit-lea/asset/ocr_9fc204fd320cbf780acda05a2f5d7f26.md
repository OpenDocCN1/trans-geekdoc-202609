# Machine Learning for Biomedical Applications

![](bbox=[0.193, 0.091, 0.768, 0.258])

Figure 5.13 ICA decomposition expressed in terms of fMRI signal components.

ICA makes the exact opposite assumption. Thus, PCA is suitable for dimensionality-reduction tasks where the assumptions are that the directions of maximal variance are interpretable and of key importance. On the other hand, ICA is most often used for problems where it can be assumed that the recorded data represent a mixture of source signals.

# 5.5.7 Biomedical applications of ICA

A very common use of ICA is to isolate source signals from electrophysiological or functional recordings of the brain. Here, X<sub>M</sub> might represent neuronal recordings measured from electroencephalogram (EEG) records, or indirect measures of brain activity recorded from various locations in the brain, as done in functional MRI (fMRI). In the case of fMRI, most often spatial ICA is implemented, which means that the underlying assumption is that the source signals nonoverlapping regions of the brain that share a common pattern of brain activity (Fig. 5.13). Then, the loading coefficients A may be interpreted as the time series of patterns of activity. In this way, ICA can also be used to remove nuisance signals, e.g., generated through physiological processes (breathing, cardiac pulsation) or motion [41].

# 5.5.8 ICA exercises

+   1. Given the table in Fig. 5.9, calculate:
   a. the conditional probability that an individual aged 60–80 has heart disease;
   b. the joint probability of sampling someone who is under 20 and suffers from diabetes;
   c. the marginal probability of brain having cancer.

+   2. Given the two mixed audio files "mix1.wave" and "mix2.wave";<sup>19</sup>

19</sup> Datasets and solution is available from github.com/MachineLearningBiomedicalApplications/note-books.