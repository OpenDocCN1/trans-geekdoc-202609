# Figure 7.3 ETL and ELT

![](bbox=[0.127, 0.146, 0.651, 0.337])

The fundamental difference in the processes is where the transformation (data preparation) takes place. If we take a data lake, it is likely that ELT will be used. The raw data from the source will be placed in the data lake. For a data warehouse and data mart, it is likely that ETL will be used, as the data will be transformed to ensure the quality of the data loaded in the warehouse or mart. Many data scientists favour ELT, as they gain access to the raw data, which potentially presents more analytical possibilities.

# DATA GOVERNANCE

Data governance covers both the strategic decisions around how an organisation should use and manage data and the operationalisation of that strategy. For mature organisations, this will be set out in clear policies with an effective governance