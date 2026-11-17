checked under the Events and Logs tab. After a few minutes, the tasks’ status will change to RUNNING, as shown in the following figure:

![](bbox=[0.2, 0.15, 0.8, 0.57])

Figure 13.43: ECS Service–mlapp-cicd

Now, click on the first task, copy its public IP, and enter the public IP, followed by port 8000, in the browser. It should display a message, as shown in the following figure:

![](bbox=[0.3, 0.68, 0.69, 0.72])

```
{"message":"Loan Prediction App"}
```

Figure 13.44: ECS Service–Accessing ml app with a public IP of the first task

Go back and click on the second task, copy its public IP, and enter the public IP followed by port 8000 in the browser. It should display a message, as shown in the following figure:

![](bbox=[0.32, 0.86, 0.67, 0.89])

```
{"message":"Loan Prediction App"}
```

Figure 13.45: ECS Service–Accessing ml app with a public IP of the second task