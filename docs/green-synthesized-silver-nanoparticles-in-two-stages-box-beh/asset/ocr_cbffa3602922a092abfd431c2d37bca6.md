generalization. To the best of the authors’ knowledge, this kind of two-step green NPS using BBD and ML, which is the novelty of this study has never been presented in the literature. The size of nanoparticles is important for effective surface interaction in various biotechnological studies. Therefore, it is important to estimate the size with a low error rate according to the conditions used in the processes. This allows an economical approach with fewer experiments. In this respect, this work represents an innovative approach and a guide for the commercial production of biogenic nanoparticles using ML. The details of this two-phase approach are described in the following sections.

In this study, the biosynthesis of silver nanoparticles (AgNPs) was carried out using the extract of yellow starwort plant as a bioreduction agent. The stock solution containing the plant extract was added dropwise to the medium containing AgNO₃ at a rate of 1 drop/s to initiate the nanoparticle production process.

This process has been optimized by maintaining the temperature, the ratio of metal solution to extract volume (v:v), and mixing speed constant at 25 °C, 1:1 and 200 rpm, respectively. The pH has been set between a minimum of 4 and a maximum of 8. Initial pH of batch cultivations was adjusted and was not monitored during the process. Incubation time according to the recipe of experimental design has been adjusted to 30–240 min. Metal solutions have been prepared in different concentrations as 1–8 mM and added to the Erlenmeyer system with the help of a buret at a 1 drop per second. In this design, the experiments have been set up with 17 runs, as shown in the first four columns of Table 1. The response of the design is the harmonic mean diameter (HMD) of the nanoparticles supplied using Malvern ZetaSizer Analyzer. The results were determined by the average of three cycles of many scans (auto calculated by device) and the average size has been

# Materials and methods

The proposed method consists of two stages: BBD for experimental design, statistical formulation, and data generation; and ML for learning the input/output relationship and generalization. NPS was chosen as the application domain: the aim was to predict nanoparticle size using the proposed model for the specified inputs. Once this model is trained, it can be used for various purposes, such as in the optimization problems where the input values for the optimal nanoparticle size can be determined. In addition, different environmental conditions could be confirmed to achieve a higher desirability. The details are given in the following subsections.

# Experimental design with BBD and data generation

Experiments of NPS have been performed to evaluate the effects of selected variables, namely metal concentration, incubation time and pH on a small scale with 25 mL working volume in the Erlenmeyer system. Relevant experimental designs for optimization processes have been carried out using the Design-Expert® software (version 7.0.0, Stat-Ease Inc., Minneapolis, MN). The process has been followed by statistical analysis using BBD that uses minimum-maximum levels and one point at the center of the experimental region to fit quadratic polynomials as in Figure 1.[20]

**Table 1.** BBD’s predicted values and percent errors for the Control Set.

| Run | pH | Incubation Time (min) | Metal Concentration (mM) | HMD (nm) Actual | HMD (nm) Prediction | Prediction Error (%) |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 4 | 30 | 4.50 | 48.00 | 46.68 | 2.76 |
| 2 | 4 | 135 | 1.00 | 149.40 | 148.20 | 0.80 |
| 3 | 8 | 135 | 8.00 | 172.00 | 173.20 | 0.70 |
| 4 | 6 | 240 | 8.00 | 137.00 | 134.48 | 1.84 |
| 5 | 8 | 30 | 4.50 | 90.50 | 89.88 | 0.69 |
| 6 | 6 | 135 | 4.50 | 135.3 | 125.84 | 6.99 |
| 7 | 6 | 135 | 4.50 | 134.00 | 125.84 | 6.09 |
| 8 | 6 | 135 | 4.50 | 124.6 | 125.84 | 1.00 |
| 9 | 4 | 135 | 8.00 | 109.00 | 110.90 | 1.74 |
| 10 | 6 | 30 | 1.00 | 81.00 | 83.53 | 3.18 |
| 11 | 8 | 135 | 1.00 | 106.00 | 104.10 | 1.79 |
| 12 | 8 | 240 | 4.50 | 89.50 | 90.83 | 1.48 |
| 13 | 4 | 240 | 4.50 | 115.20 | 115.83 | 0.54 |
| 14 | 6 | 135 | 4.50 | 116.3 | 125.84 | 8.20 |
| 15 | 6 | 240 | 1.00 | 98.50 | 99.08 | 0.59 |
| 16 | 6 | 30 | 8.00 | 80.50 | 79.93 | 0.71 |
| 17 | 6 | 135 | 4.50 | 119.00 | 125.84 | 5.75 |
| **Average prediction error (%)** |  |  |  |  |  | **2.64** |

![](bbox=[0.22, 0.724, 0.633, 0.929])

**Figure 1.** Box Behnken Design (BBD).