![](bbox=[0.19, 0.106, 0.81, 0.376])

**Fig. 11.15.** Well B gas sensitivity.

**Table 11.13.** Gas lift results for Well A and B (Optimum Production Rates).

**Table 11.13.** Gas lift results for Well A and B (Optimum Production Rates).

# ### 3.5 ANN Results

# #### 3.5.1 ANN Architecture

Table 11.14 shows the statistics of the historical production data input and output for both wells used for the ANN models to predict THP. However, production data of three wells were used to build the database for training the model while one well data was used for testing the model.

**Table 11.14.** Input and output data statistics.

| Parameters | Minimum | Maximum | Average | Standard Deviation | Data Type |
|---|---:|---:|---:|---:|---|
| Days | 0 | 2455 | 1009.04 | 660.53 | Input |
| Daily Oil Production (MMSTB/D) | 0 | 27645 | 11308.43 | 5023.96 | Input |
| Cumulative Oil Production (MMSTB) | 0 | 26.06 | 10.44 | 6.68 | Input |
| Cumulative Gas Production (MMSCF) | 0 | 32.73 | 8.04 | 9.41 | Input |
| Gas Rate (MMSCF/D) | 0 | 23.66 | 5.94 | 6.51 | Input |
| Flowing Bottomhole Pressure (PSIA) | 2489.96 | 6212.41 | 4423.02 | 508.60 | Input |
| Tubing Head Pressure (PSIG) | 1095.03 | 4185.29 | 2564.75 | 430.48 | Output |