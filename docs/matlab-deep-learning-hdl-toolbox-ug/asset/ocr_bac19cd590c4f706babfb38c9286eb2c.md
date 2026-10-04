# Load Pretrained Network

Load the pretrained network.

```
snet=detector.Network;
I_pre=yolo_pre_proc(I);
```

Use analyzeNetwork to obtain information about the network layers:

```
analyzeNetwork(snet)
```

![](bbox=[0.257, 0.146, 0.526, 0.359])