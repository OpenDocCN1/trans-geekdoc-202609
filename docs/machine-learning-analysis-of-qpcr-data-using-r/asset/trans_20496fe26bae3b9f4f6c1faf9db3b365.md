

```r
cat("Accuracy  = ", round(accuracy,2), " ± ", round(accuracy_SD, 2),
"\nSensitivity = ", round(sensitivity,2), " ± ", round(sensitivity_SD, 2),
"\nSpecificity = ", round(specificity,2), " ± ", round(specificity_SD, 2))
```

```
Accuracy  = 1    ± 0.01
Sensitivity = 0.99  ± 0.04
Specificity = 1    ± 0
```

图3.7A展示了这一分析的结果。为了更好地理解超平面的含义，将使用清单中定义的一次迭代中的xyz_dat数据框的数据进行绘图：

```r
xyplot(MR ~ FCN, group = ygrid, data = xyz_dat, col=c("gray90", "gray40"), key = list(space="top", columns=2, col = "black", points=list(pch=16, col=c("gray40", "gray90")), text=list(c("positives", "negatives"))))
```

图3.7B清晰地显示，聚集在MR/FCN空间中心的反应被归类为阳性（有反应）。

![](img/7ea01e6937e09d043e45c73fff9eaed3_113_0.png)

![](img/7ea01e6937e09d043e45c73fff9eaed3_114_0.png)

图3.7. SVM分析提供的超平面。SVM对maxRatio生成的qPCR数据进行分析的结果。A. 线条表示SVM模型识别出的超平面；叠加了五次独立分析。使用的核函数是Bessel函数，成本为1。B. SVM生成模型的示例。MR/FCN平面上的每个点都被赋予一个标签（'positives'或'negatives'）；因此，反应根据其在数学空间中的位置进行分类。反应按上面板中的方式分层；注意，下面板是上面板的放大图。

## 扩展SVM分类

本例中达到的总体准确率并不突出；相比之下，在上述研究（Marongiu, 2020）中准确率为1 ± 0。然而，必须考虑到：

- 数据集很小（仅占2020年分析数据的0.76%）。
- 在归类为阳性和阴性的反应之间存在相当多的重叠。

无论初始数据的质量如何，该分析的价值在于其根据反应性对样本进行聚类的能力。这一特性将在下面的清单中加以测试。

## 清单3.11

```r
pred_prob = predict(mod, validation, type = "probabilities")
prediction = predict(mod, validation)
serial = validation$Index
rating = validation$Outcome
classified = data.frame(Serial = serial, Class = prediction, MR = validation$MR,
    FCN = validation$FCN, stringsAsFactors = FALSE)
split.screen(c(2, 1))
split.screen(c(1, 4), screen = 2)
screen(1)
plot(classified$MR[classified$Class == "positive"] ~ classified$FCN[classified$Class == "positive"],
    cex=1.5, pch=16, xlim=c(0, 0.50), ylim=c(0,0.45), xlab=expression(bold("FCN")),
    ylab=expression(bold("MR")))
points(classified$MR[classified$Class == "negative"] ~ classified$FCN[classified$Class == "negative"],
    cex=1.5, pch=1)
points(classified$MR[classified$Serial == 171] ~ classified$FCN[classified$Serial == 171], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 71] ~ classified$FCN[classified$Serial == 71], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 148] ~ classified$FCN[classified$Serial == 148], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 80] ~ classified$FCN[classified$Serial == 80], cex=2.5,
    pch=0, lwd=2)
text(classified$FCN[classified$Serial == 171]-1, 0.02, 171)
text(classified$FCN[classified$Serial == 71]+0.3, 0.02, 71)
text(classified$FCN[classified$Serial == 148]+1, 0.02, 148)
text(classified$FCN[classified$Serial == 80], 0.02, 80)
points(classified$MR[classified$Serial == 4] ~ classified$FCN[classified$Serial == 4], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 10] ~ classified$FCN[classified$Serial == 10], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 76] ~ classified$FCN[classified$Serial == 76], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 117] ~ classified$FCN[classified$Serial == 117], cex=2.5,
    pch=0, lwd=2)
text(classified$FCN[classified$Serial == 4], 0.01, 4)
text(classified$FCN[classified$Serial == 10], 0.05, 10)
text(classified$FCN[classified$Serial == 76], 0.1, 76)
text(classified$FCN[classified$Serial == 117], 0.04, 117)
points(classified$MR[classified$Serial == 128] ~ classified$FCN[classified$Serial == 128], cex=2.5,
    pch=0, lwd=2)
points(classified$MR[classified$Serial == 108] ~ classified$FCN[classified$Serial == 108], cex=2.5,
     pch=0, lwd=2)
points(classified$MR[classified$Serial == 130] ~ classified$FCN[classified$Serial == 130], cex=2.5,
     pch=0, lwd=2)
points(classified$MR[classified$Serial == 126] ~ classified$FCN[classified$Serial == 126], cex=2.5,
     pch=0, lwd=2)
text(classified$FCN[classified$Serial == 128], 0.02, 128)
text(classified$FCN[classified$Serial == 108]-0.3, 0.055, 108)
text(classified$FCN[classified$Serial == 130]+0.2, 0.055, 130)
text(classified$FCN[classified$Serial == 126], 0.03, 126)
# samples at FCN = 50
points(classified$MR[classified$Serial == 167] ~ classified$FCN[classified$Serial == 167], cex=2.5,
     pch=0, lwd=2)
points(classified$MR[classified$Serial == 146] ~ classified$FCN[classified$Serial == 146], cex=2.5,
     pch=0, lwd=2)
points(classified$MR[classified$Serial == 153] ~ classified$FCN[classified$Serial == 153], cex=2.5,
     pch=0, lwd=2)
points(classified$MR[classified$Serial == 169] ~ classified$FCN[classified$Serial == 169], cex=2.5,
     pch=0, lwd=2)
text(classified$FCN[classified$Serial == 167]-2, 0.01935, 167)
text(classified$FCN[classified$Serial == 146]-2, 0.39102, 146)
text(classified$FCN[classified$Serial == 153]-2, 0.05577, 153)
text(classified$FCN[classified$Serial == 169]-2, 0.33484, 169)
legend("topleft", title = "SVM classification", legend = c("Positive", "Negative"), pch=c(16,1), cex=1.5)
screen(3)
plot(amplification$FAM[amplification$Index == 171] ~ amplification$Cycle[amplification$Index == 171],
     type="l", xlim=c(0,45), lwd=2, ylim=c(min(amplification$FAM, na.rm=TRUE),
     max(amplification$FAM, na.rm=TRUE)), xlab=expression(bold("Cycle")), ylab=expression(bold("Fluorescence")))
points(amplification$FAM[amplification$Index == 71] ~ amplification$Cycle[amplification$Index == 71],
     type="l", lwd=2, lty=2)
points(amplification$FAM[amplification$Index == 148] ~ amplification$Cycle[amplification$Index == 148],
     type="l", lwd=2, lty=3)
points(amplification$FAM[amplification$Index == 80] ~ amplification$Cycle[amplification$Index == 80],
     type="l", lwd=2, lty=4)
legend("topleft", title = "Reaction index", legend = c(171, 71, 148, 80), lwd = 2, lty=1:4)
screen(4)
plot(amplification$FAM[amplification$Index == 4] ~ amplification$Cycle[amplification$Index == 4],
    type="l", xlim=c(0,45), lwd=2, ylim=c(min(amplification$FAM, na.rm=TRUE),
    max(amplification$FAM, na.rm=TRUE)), xlab=expression(bold("Cycle")),
    ylab=expression(bold("Fluorescence")))
points(amplification$FAM[amplification$Index == 10] ~ amplification$Cycle[amplification$Index == 10],
    type="l", lwd=2, lty=2)
points(amplification$FAM[amplification$Index == 76] ~ amplification$Cycle[amplification$Index == 76],
    type="l", lwd=2, lty=3)
points(amplification$FAM[amplification$Index == 117] ~ amplification$Cycle[amplification$Index ==
    117], type="l", lwd=2, lty=4)
legend("topleft", title = "Reaction index", legend = c(4, 10, 76, 117), lwd = 2, lty=1:4)
screen(5)
plot(amplification$FAM[amplification$Index == 128] ~ amplification$Cycle[amplification$Index == 128],
    type="l", xlim=c(0,45), lwd=2, ylim=c(min(amplification$FAM, na.rm=TRUE),
    max(amplification$FAM, na.rm=TRUE)), xlab=expression(bold("Cycle")),
    ylab=expression(bold("Fluorescence")))
points(amplification$FAM[amplification$Index == 108] ~ amplification$Cycle[amplification$Index ==
    108], type="l", lwd=2, lty=2)
points(amplification$FAM[amplification$Index == 130] ~ amplification$Cycle[amplification$Index ==
    130], type="l", lwd=2, lty=3)
points(amplification$FAM[amplification$Index == 126] ~ amplification$Cycle[amplification$Index ==
    126], type="l", lwd=2, lty=4)
legend("topleft", title = "Reaction index", legend = c(128, 108, 130, 126), lwd = 2, lty=1:4)
screen(6)
plot(amplification$FAM[amplification$Index == 146] ~ amplification$Cycle[amplification$Index == 146],
    type="l", xlim=c(0,45), lwd=2, ylim=c(min(amplification$FAM, na.rm=TRUE),
    max(amplification$FAM, na.rm=TRUE)), xlab=expression(bold("Cycle")),
    ylab=expression(bold("Fluorescence")))
points(amplification$FAM[amplification$Index == 169] ~ amplification$Cycle[amplification$Index ==
    169], type="l", lwd=2, lty=2)
points(amplification$FAM[amplification$Index == 153] ~ amplification$Cycle[amplification$Index ==
    153], type="l", lwd=2, lty=3)
points(amplification$FAM[amplification$Index == 167] ~ amplification$Cycle[amplification$Index ==
    167], type="l", lwd=2, lty=4)
legend("topleft", title = "Reaction index", legend = c(146, 169, 153, 167), lwd = 2, lty=1:4)
dev.off()
```

