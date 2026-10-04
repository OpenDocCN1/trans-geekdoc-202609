# 10 Featured Examples

| conv_4 | 504820 | 0.00229 |
| maxpool_4 | 8965 | 0.00004 |
| fc_1 | 687629 | 0.00313 |
| fc_2 | 439923 | 0.00200 |
| fc_3 | 58721 | 0.00027 |

* The clock frequency of the DL processor is: 220MHz

```
prediction_FPGA = struct with fields:
    NumSamples: 1
    MetricResults: [1x1 struct]
QuantizedNetworkFPS: 17.2915
```

# View Performance of Quantized Neural Network

Examine the MetricResults.Result field of the validation output to see the performance of the quantized network.

prediction_simulation.MetricResults.Result

```
ans=2x2 table
NetworkImplementation      MetricOutput
```

| {'Floating-Point'} | 1 |
| {'Quantized'} | 1 |

prediction_FPGA.MetricResults.Result

```
ans=2x2 table
NetworkImplementation      MetricOutput
```

| {'Floating-Point'} | 1 |
| {'Quantized'} | 1 |

Examine the QuantizedNetworkFPS field of the validation output to see the frames per second performance of the quantized network.

prediction_FPGA.QuantizedNetworkFPS

```
ans = 17.2915
```

# See Also

+   * dlquantizer
* calibrate
* validate
* dlquantizationOptions
* "Quantization of Deep Neural Networks" on page 11-2

# 10-114