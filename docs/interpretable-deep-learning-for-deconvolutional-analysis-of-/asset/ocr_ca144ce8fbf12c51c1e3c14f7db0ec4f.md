# Neuron NeuroResource

# CellPress

(50) mice pulses at random times, sampled from a Gamma distribution, across trials, mimicking the statistics of natural oral pulses.¹ We recorded and 770 neurons from the anterior cortex of mice (Figures 4A and 5B).

cefully detected the two components, when the events overlapped and in a limited data range of 25 training trials (Figures 6A and 6B).

the somiform cortex shows neuronal sequences of responses to oral pulses are largely uncorrelated, and we used DUNL to characterize these resonances.

In the second scenario, a single neuron responded to a single event type to evaluate how effectively DUNL identifies kernels and codes based on general firing patterns (simulation study, STAR Methods). This characterization helps users assess DUNL's performance for specific statistics.

To model neuronal responses, we aligned the elements of the responses with the timing of the pulses and modeled them using a Poisson process (Figure 5C). Each neuron was characterized by a single kernel and code amplitudes.

DUNL-performance as a function of binding rate (2, 5, 11, 14, and 17 Hz) and trial number (5, 25, 50, and 500; Figure 5A) for kernel learning (10, 25, 500, and 1000 trials; Figure 6B).

We learned the kernels and code amplitudes for all recordings, capturing the temporal dynamics of response across the prior cortex. K-means clustering on measured kernels revealed three main components (Figure 5D).

Results (Figures 6C–6E) show DUNL's ability to learn kernels and infer overlap events with more trials, higher precision and larger sizes (STAR Methods simulation details).

Three clusters represent with activity following following pulses, with distinct dynamics, while the fourth corresponds to neurons inhibited by pulses.

In the third scenario, we tested DUNL's ability to recover kernels from 5 different events across trials, in a large-scale setting with 1000 neurons and 1000 trials. We used this dataset to guide how to choose the appropriate number of kernels when this information is unknown.

This application demonstrates how DUNL can learn any shape of kernels without relying on assumptions about their structure. As result, DUNL can capture a diversity of responses without requiring hand-crafted functions, utilizing the variable nonlinear temporal structure of neural responses.

We used a set of olfactory kernels to generate this data for testing (Figure 7), which is not required by DUNL to learn. We used this to enable a one-component model with sparse component (CA) to the same dataset.

Second, while multi-photon photometry recordings from mice and objects showed expected experience where events were not predicted (Figure 5G). These recordings captured calcium concentration changes in axons across trials, monitored by a separate optical fiber. DUNL was used to identify a single kernel for each event over the entire 90 ms period.

Events occurred in each trial, with local events not seen across trials. As a result, the population dynamics exhibited only a low-rank structure, making it difficult to recover overlapping kernels. DUNL effectively recovers low-rank structures, though less successfully.

We observed that the kernels learned by DUNL were larger in ventral regions and smaller in dorsal regions, with findings consistent from previous experiments⁷.

This highlights DUNL's ability to detect events overlapping across trials and to capture highly unstructured behavioral features. For features with no dendritic structure

DUNL effectively learns kernels, even with overlapping kernels (Figures 7g and 7j). When the number of kernels is unknown, training and validation allow us to optimize kernels until the kernel count exceeds the true number of events.

# Model characterization

To evaluate the robustness of our results and guide DUNL's use, we characterized its performance across three scenarios based on spiking data. In the first scenario, a single neuron responds to two distinct, unstructured events (simulation i, STAR Methods: Simulation details). DUNL,

DUNL's performance on this dataset is also used to show its ability to share kernels across the neuron population, where group sparsity outperforms even with group

⁸ Histogram of metrics for DUNL: one code amplitude per event on a single trial across recorded neurons with group sparsity.

⁹ Minkowski snapshots detected by DUNL on a single trial across all records with group sparsity (i.e., difference once for each event). Detection is more robust with group sparsity.

See also Figures S4–S4.

Neuron 7/3, 1151–1168, April 16, 2023