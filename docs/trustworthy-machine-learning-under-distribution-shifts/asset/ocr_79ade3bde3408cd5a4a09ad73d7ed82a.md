# Exemplar under Distribution Shift

# Varying In-Context Length

![](bbox=[0.135, 0.156, 0.843, 0.335])

+   - length=1
- length=2
- length=3
- length=4
- length=5

FIGURE 5.9. Performance analysis of in-context exemplars: (left) under distribution shift; (right) varying the exemplar length.

**Effect of Varying In-Context Length.** Here, we analyze the effect of increasing exemplar length during inference. Here we consider one positive and negative exemplar pair as length 1. Here we vary the length from 1 to 5 and show the results in Figure 5.9 right. We observe slight improvement when the length gradually increases which is consistent with the theoretical findings [297]. However, when the length is longer than 4 the performance drops and the predictions of MLLM unstable could be other than “True” or “False”. This might be due to the limited capacity of MLLMs on handling a certain amount of information, which is worth conducting studies on sophisticated MLLMs in the future.

**Performance of OOD Detection.** At last, we consider a more challenging scenario where data from open classes could exist in the target dataset. We simulate this situation by choosing 60% of the classes as closed classes and the rest are open classes. To detect such open-class data, i.e., OOD detection [28, 306]⁶, we use the vision model prediction confidence as a baseline and compare with the MLLM reasoning confidence as well as the detection score $\Delta$ in Equation (5.4). The result is shown in Figure 5.10. In the upper row, we observe the similar clearly distinguishable distributions using our score $\Delta$ as in Figure 5.6. In the lower row, we show the F1 score of each detection criterion under a threshold varied from 0 to 1 on three datasets. When a criterion produces confidence larger than the threshold, it would predict as close-class data, other as open-class ones. Based on the result, we find

> ⁶Note that OOD detection here is different from the previous setting: here focus on detecting open-class data, and previous one focuses on detecting prediction errors.