![](bbox=[0.26, 0.09, 0.72, 0.28])

FIGURE 10.1 Sensor data after sub-activity-related abnormal behavior is generated.

activity, the sensor $M_{26}$ is repeated more than usual, which can be used to emulate the usage of a computer. A snapshot for sub-activity-related abnormal behavior synthesis is depicted in Figure 10.1, where ONabn shows the inserted sensor activations.

Moreover, an addleror set of WSU dataset is used because it reflects the confusion and forgetting anomaly types such as forgetting to turn water tap off.

```
Algorithm 10.2: Simulation of Sub-Activity-Related Abnormal Behavior

**Input:** Sequence of $S$ of sensor activations of an activity $A$ such as $S = <a_1, a_2, ..., a_n>$. A sensor type $M$ that is involved in activity $A$. $A$ and $M$ are carefully chosen to reflect a dementia-related abnormal behavior (e.g. sensor $M_6$ in activity *working*). 
**Output:** $S = <a_1, M, a_2, M, a_3, ..., M, a_n>$
while true do
    Choose a random position $p$ in $S$
    Insert $M$ into $S$ at position $p$
end
```

# 10.5 SPATIO-TEMPORAL ACTIVITY RECOGNITION AND ABNORMAL BEHAVIOR DETECTION

RNNs have shown promising results in some sequence modeling problems such as speech recognition [61], machine translation [62,63], handwriting recognition and generation or translation, language modeling and protein secondary structure prediction [64]. Daily life activities can be modelled