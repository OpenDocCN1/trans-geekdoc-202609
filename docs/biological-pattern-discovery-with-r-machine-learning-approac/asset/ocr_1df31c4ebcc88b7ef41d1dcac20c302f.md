236

Biological Pattern Discovery with R

associated with the cow milk concentration percentage. For this investigation, each spectrum was converted to a set of variables using the short-term Fourier transform. The R package wavelets was used for the short-term Fourier transform of the spectra of this data set.

![](bbox=[0.248, 0.203, 0.751, 0.363])

Fig. 5.20. The estimated baseline for one of 45 replicates of the milk data using BWH. The thin lines stand for the raw data and the thick line stands for the estimated baseline.

After the transformation, a matrix was generated. The data was further logarithm transformed. A visualisation map was produced using the self-organising map algorithm [Kohonen, 1982] based on the logarithm-transformed short-term Fourier transform data. To do so is because the self-organising map algorithm can normally produce a map to well-reserve and envisage the structure of a multi-dimensional data. The visualisation was carried out through a process in which the 45 replicates were mapped to different neurons, which were arranged as a two-dimensional array of cells. Cell is one neuron on this array. If two spectra profile were mapped to the same neuron (cell), it is believed that these two spectra profile shared a great degree of similarity compared with others. In addition, similar spectra were supposed to be mapped to neighbouring neurons (cells). The R package kohonen was used for this data visualisation.

The self-organising map for this data set was composed of 36 neurons on which each of 45 spectra data was mapped with a cow milk concentration percentage printed on the cells of the map. Some neurons attracted no spectrum, some attracted one spectrum and attracted more than one spectrum. If two spectra were mapped to the same neuron, it was expected that their spectra profiles were very similar. It is expected that their cow milk concentration percentage values were similar. Figure 5.21 show such a map. The self-organising map shows a good separation