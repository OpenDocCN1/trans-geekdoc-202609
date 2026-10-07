# # Result

```
In [1] runfile('/O/1/Development_2.0/ML_phase_3_ML_Intro/ml_p3_ch14_dp_BLTZ/
prct_RBM.py', wdir='Dr/1/Development_2.0/ML_phase_3_ML_Intro/ml_p3_ch14_dp_BLTZ')
Epoch. 1.
loss = 0.3745898604393054
Epoch. 2.
loss = 0.2449556178510856
Epoch. 3.
loss = 0.2507295629617837
Epoch. 4.
loss = 0.2438576570433044
Epoch. 5.
loss = 0.2508241567224175
Epoch. 6.
loss = 0.2465479856472015
Epoch. 7.
loss = 0.2476613223557039
Epoch. 8.
loss = 0.25108692049980164
Epoch. 9.
loss = 0.2465537935493766
Epoch. 10.
loss = 0.248631545727281
Evaluation of Test loss = 0.2431282029337383
```

We can see that in *test_set* prediction we have **Test-Loss 0.2632**, i.e. more than 75% correct predictions.

# ## Comparison between predicted and real results

![](bbox=[0.095, 0.335, 0.904, 0.473])

From this comparison we can see that the *predicted result* from *RBM*, we have some *ratings* that are not originally rated. Also we get 75% correct predictions for the *movies* that are *originally rated* (marked red).