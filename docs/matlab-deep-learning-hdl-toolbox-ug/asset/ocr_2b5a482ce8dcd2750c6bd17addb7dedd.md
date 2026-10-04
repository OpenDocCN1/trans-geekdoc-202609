# Visualize Activations of a Deep Learning Network by Using LogoNet

```
"InputDataOffset" "0x00000000" "24.0 MB"
""OutputResultOffset" "0x01000000" "136.0 MB"
""SystemBufferOffset" "0x0a000000" "64.0 MB"
""InstructionDataOffset" "0x0e000000" "8.0 MB"
""ConvWeightDataOffset" "0x0e000000" "4.0 MB"
""EndOffset" "0x0e000000" "Total: 236.0 MB"

### Programming FPGA Bitstream by JTAG...
### Programming the FPGA bitstream has been completed successfully.

### Finished writing input activations.
### Running single input activations.
```

Deep Learning Processor Profiler Results

| | LastLatency(cycles) | LastLatency(seconds) | FramesNum |
|---|---|---||
| Network | 10182024 | 0.06788 | 1 |
| conv_module | 10182024 | 0.06788 | |
| conv_1 | 7088885 | 0.04726 | |
| maxpool_1 | 3093166 | 0.02062 | |

* The clock frequency of the DL processor is: 150MHz

The activations are returned as a d-3-array, with the third dimension indexing the channel on the maxpool_1 layer. To show these activations using the itmile function, reshape array to 4-D. The third dimension in the input itmile represents the image color. The third dimension to have size 1 because the activations do not have color. The fourth dimension indexes the channel.

```
sz = size(act1)
act1 = reshape(act1,sz(1) sz(2) 1 sz(3));
```

Display the activations. Each activation can take any value, normalize the output using the mat2gray. All activations are scaled so that the minimum activation is 0 and the maximum activation is 1. Display the 96 images on an 12-by-8 grid, for each channel in the layer.

```
I = itmile(mat2gray(act1), 'GridSize',[12 8]);
imshow(I)
```