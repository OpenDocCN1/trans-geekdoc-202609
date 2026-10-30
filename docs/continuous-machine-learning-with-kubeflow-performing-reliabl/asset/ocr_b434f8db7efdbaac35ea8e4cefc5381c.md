The preceding diagram is the example gen component, which will split the dataset in that manner. So, this is the architecture of the ExampleGen.

# Component: ExampleGen

![](bbox=[0.12, 0.28, 0.88, 0.43])

Figure 4.6: Example Gen Architecture

The ExampleGen TFX Pipeline component ingests the data into TFX pipelines.

```
def examplegen(_data_root):
example_gen = CsvExampleGen(input=external_input(_data_root))
return example_gen
```

Define the path where we downloaded the data:

```
example_gen= examplegen(_data_root)
context.run(example_gen)
```