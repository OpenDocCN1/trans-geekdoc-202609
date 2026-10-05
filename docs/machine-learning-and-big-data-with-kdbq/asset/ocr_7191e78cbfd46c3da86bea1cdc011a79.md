# 450 MACHINE LEARNING

monitorConvergence; and,, specification of the problem, func (choose from three options `classifier`, `multiClassifier`, and `nonlinearReg`, (respectively).

There are two terminal conditions supported: `count`, for a case where provided number of iterations is performed, and `relativeError`, being the required minimum error to be achieved during the convergence process. The function is implemented as follows:

```
quantq0.modelNN:[input,output,nNeurons;typeTerminal;argTerminal];
// input -- array of inputs
// output -- array of outputs
// nNeurons -- number of neurons in hiddn layer
// typeTerminal -- type of terminal condition: `count``relativeError
// argTerminal -- parameter for terminal condition
// learningRate -- learning rate for update
// monitorConvergence -- binary variable to monitor convergence
// func -- purpose of the NN: `classifier`multiClassifier`nonlinearReg
// adding bias/intercept to the input data
input:1,'input';
// counting dimension of the input including intercept
input: count flip output;
// counting of the output
output: count first output;
// initialization of layer: Input -> Hidden
layer:quantq0.weightNN[ninput;nNeurons];
// initialization of layer: Hidden (with bias[ninput+nNeurons];nOutput) -> Output
layerH20:weightH20;if:0];
// decide between two terminal conditions
[$Terminal=`count;terminus:[{argTerminal}];];
[$typeTerminal=`relativeError;terminus:[{argTerminal};param[`Error]`]argTerminal];argTerminal];];
```

```
// training the network and return output (depends on monitoring the convergence)
[$monitorConvergence=1;
[:.quantq0.forwardBackwardNNError[input;output;learningRate;func
]][:terminus;out parshid2out`parsin2Hid`Error`Counter(@,);
layerH20;layerH20;if:0];
[:.quantq0.forwardBackwardNNError[input;output;learningRate;func
]][:terminus;out parshid2out`parsin2Hid`Error`Counter(@,);
layerH20;layerH20;if:0];
```

The function proceeds as follows: First, the instances are instantiated with weightNNIt. Then, the terminal is decided and the appropriate rule for the iteration procedure is defined. This function can be potentially outsourced into another function, depending on the choice whether we want to see every iteration step or not, based on the value of monitorConvergence, the iteration is performed.
When we aim for monitoring convergence, we record the dictionary parameters in every step. From this record, we can understand the evolution of errors as well as variance in the parameters. This is a useful option when we want to gain intuition about the problem itself.