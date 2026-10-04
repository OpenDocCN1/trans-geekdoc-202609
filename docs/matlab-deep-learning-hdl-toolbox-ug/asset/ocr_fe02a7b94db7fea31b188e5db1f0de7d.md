# Vehicle Detection Using DAG Network Based YOLO v2 Deployed to FPGA

| res4a branch1 485804 0.00221 |
| res4a branch2a 485923 0.00221 |
| res4a branch2b 880309 0.00400 |
| res4a 52446 0.00024 |
| res4b branch2a 880071 0.00400 |
| res4b branch2b 880065 0.00400 |
| res4b 52456 0.00024 |
| yolov2Conv1 880210 0.00400 |
| yolov2Conv2 880375 0.00400 |
| yolov2ClassConv 179300 0.00081 |

* The clock frequency of the DL processor is: 220MHz

Display the prediction results.

```
[bboxes, scoresn, labelsn] = yolo_post_proc(prediction,I_pre,anchorBoxes,{'Vehicle'});
I_new3 = insert0bjectAnnotation(I,rectangle,bboxes,scoresn);
figure
imshow(I_new3)
```

![](bbox=[0.257, 0.412, 0.523, 0.603])