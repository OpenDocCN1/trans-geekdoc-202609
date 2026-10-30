# 4.4.2 StatisticsGen

The StatisticsGen component computes the statistics over your dataset for the data analysis, as well as for use in the downstream components. It uses the TensorFlow Data Validation library.

# Component: StatisticsGen

![](bbox=[0.12, 0.4, 0.86, 0.53])

Figure 4.8: Statistics Gen Architecture

StatisticsGen takes as input, the dataset that we just ingested using ExampleGen:

```
def statisticsgen(example_gen):
statistics_gen =
StatisticsGen(examples=example_gen.outputs['examples'])
return statistics_gen
```

```
statistics_gen=statisticsgen(example_gen)
context.run(statistics_gen)
```