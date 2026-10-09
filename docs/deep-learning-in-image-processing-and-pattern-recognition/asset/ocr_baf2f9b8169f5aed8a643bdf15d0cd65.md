The MSACP algorithm is embedded into the ATSS, and the results of the experiment are shown in Table 2. In the three optimization experiments, the overall improvement effect is best when $n$ is set to three. The $AP$ is increased by $1.2\%$ compared with the CPA algorithm. When $n = 2$ and $n = 4$, the $AP$ increases by $0.4\%$ and $0.3\%$, respectively, compared with the CPA algorithm. For Table 3, the MSACP algorithm was embedded into the AutoAssign model. In three optimization experiments, the overall improvement effect is best when $n$ is set to two. The $AP$ is improved by $3.5\%$ compared with the CPA algorithm. When $n = 3$ and $n = 4$, the $AP$ is increased by $2.8\%$ and $2.6\%$ compared with the CPA algorithm, respectively. The MSACP algorithm provides phased optimization for the training dataset according to the training information, which makes the information distribution actively adapt to different stages of model training.

Table 1. The training results are compared by the Grid RCNN model (epoch = 12).

| Method | AP (%) | AP_50 (%) | AP_75 (%) | AP_s (%) | AP_m (%) | AP_l (%) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| origin | 43.4 | 53.4 | 51.0 | 8.7 | 58.5 | 81.7 |
| CPA | 49.7 | 62.3 | 58.9 | 10.7 | 66.7 | 84.7 |
| n = 2 | 50.0 | 62.6 | 58.8 | 9.6 | 66.7 | 84.7 |
| n = 3 | 50.7 | 63.4 | 59.5 | 10.5 | 68.4 | 85.7 |
| n = 4 | 50.9 | 63.5 | 59.5 | 11.1 | 68.6 | 86.7 |

Table 2. The training results are compared by the ATSS model (epoch = 12).

| Method | AP (%) | AP_50 (%) | AP_75 (%) | AP_s (%) | AP_m (%) | AP_l (%) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| origin | 39.3 | 51.1 | 45.7 | 15.5 | 48.8 | 69.4 |
| CPA | 48.4 | 62.1 | 56.4 | 13.7 | 61.2 | 84.2 |
| n = 2 | 48.8 | 62.4 | 56.9 | 13.6 | 61.5 | 85.5 |
| n = 3 | 49.0 | 62.7 | 57.0 | 13.5 | 61.6 | 85.5 |
| n = 4 | 48.7 | 62.4 | 56.6 | 13.7 | 61.3 | 85.5 |

Table 3. The training results are compared by the AutoAssign model (epoch = 12).

| Method | AP (%) | AP_50 (%) | AP_75 (%) | AP_s (%) | AP_m (%) | AP_l (%) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| origin | 48.0 | 66.2 | 55.5 | 25.8 | 58 | 75.6 |
| CPA | 49.9 | 66.5 | 58 | 21.4 | 60.3 | 80.7 |
| n = 2 | 53.4 | 71.6 | 61.9 | 22.9 | 64.8 | 82.1 |
| n = 3 | 52.7 | 70.9 | 60.7 | 23.6 | 63.8 | 82.5 |
| n = 4 | 52.5 | 70.5 | 61.3 | 23.5 | 63.7 | 80.8 |

# 4.3. Performance Detection of MSACP under Different Training Amounts

The MSACP algorithm divides the total training amount into multiple stages on average. Before starting the next stage of training, the class information of the training dataset will be adjusted adaptively according to the training situation of the current stage. The amount of training in each stage is related to the amount of the hyper-parameters, epoch and $n$. In Section 3.2, the epochs of the models were all 12. It is necessary to use the MSACP algorithm to examine models with a different epoch.

In this section, three models with more epochs are selected, including SSD512 [35], NAS FGN [36], and YOLOv3 [17]. The SSD512 and YOLOv3 models belong to the one-stage range. The NAS FGN model is a classic feature pyramid network. Their experimental results are listed in Tables 4–6, respectively. For Table 4, the MSACP algorithm is tested with the model SSD512. The epoch of this model is 24. In these three experiments, the overall improvement effect of model SSD512 is the best when $n = 2$. The $AP$ reaches $52.9\%$, which is improved by $0.5\%$ over the CPA algorithm. When $n = 3$ and $n = 4$, the corresponding AP increases by $0.2\%$ and $0.4\%$ compared to the CPA algorithm, respectively. MSACP adaptively adjusts the class information of the training dataset according to the training condition of the model SSD512 to improve the training quality.