# 10 Featured Examples

Deep Learning Processor Profiler Performance Results

| Network | LastLatency(cycles) | LastLatency(seconds) | FramesNum |
|---|---|---|---||
| conv 1 | 1754614 | 0.00798 | | 1 |
| maxpool 1 | 271184 | 0.00123 | | |
| crossnorm | 87557 | 0.00040 | | |
| conv 2 | 125768 | 0.00057 | | |
| maxpool 2 | 149819 | 0.00008 | | |
| fc 1 | 199602 | 0.00009 | | |
| fc 2 | 1085664 | 0.00493 | | |
| * The clock frequency of the DL processor is: 220MHz | 14930 | 0.00007 | | |

```
### Finished writing input activations.
### Running single input activations.
```

Deep Learning Processor Profiler Performance Results

| Network | LastLatency(cycles) | LastLatency(seconds) | FramesNum |
|---|---|---|---||
| conv 1 | 1754486 | 0.00797 | | 1 |
| maxpool 1 | 271014 | 0.00123 | | |
| crossnorm | 87662 | 0.00040 | | |
| conv 2 | 125835 | 0.00057 | | |
| maxpool 2 | 149789 | 0.00068 | | |
| fc 1 | 199661 | 0.00009 | | |
| fc 2 | 1085505 | 0.00493 | | |
| * The clock frequency of the DL processor is: 220MHz | 14930 | 0.00007 | | |

```
Iori = reshape(Iori, [1, we*ch]);
bbox = reshape(bbox, [1, 16]);
scores = reshape(scores, [1, 8]);
```

```
% Insert an annotation for postprocessing
out = myDNNet_Postprocess(Iori, num, bbox, scores, wi, he, ch);
```

```
sz = [he wi ch];
out = cv2mat(out,sz);
imshow(out)
```

10-40