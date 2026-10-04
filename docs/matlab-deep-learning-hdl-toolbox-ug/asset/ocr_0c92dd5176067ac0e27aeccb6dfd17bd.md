# # Classify Images on an FPGA Using a Quantized DAG Network

Select the training options. For transfer learning, keep the features from the early layers of the pretrained network (the transferred weights). To slow down learning in the transferred layers, set the initial learning rate to a small value. Specify the mini-batch size and validation data. The software validates the network every Frequency during training.

```
options = trainingOptions('sgdm',
  'MiniBatchSize',10,
  'MaxEpochs',6,
  'InitialLearnRate',1e-4,
  'Shuffle','every-epoch',
  'ValidationData',augmentsValidation,
  'ValidationFrequency',3,
  'Verbose',false,
  'Plots','training-progress')
```

Train the network that connects the transferred and new layers. By default, trainNetwork uses a GPU if one is available (Parallel Computing Toolbox) and a supported GPU device. For more information, see “GPU Support by Release” (Parallel Computing Toolbox). Otherwise, the network can also specify the execution environment by using the 'ExecutionEnvironment' name-value argument of trainOptions.

```
netTransfer = trainNetwork(augmentsTrain,Lgraph,options)
```

![](bbox=[0.05, 0.463, 0.95, 0.828])

# # Quantize the Network

Create a quantizer object and specify the network to quantize.

```
dlquantObj = dlquantizer(netTransfer, 'ExecutionEnvironment', 'FPGA');
```

10-149