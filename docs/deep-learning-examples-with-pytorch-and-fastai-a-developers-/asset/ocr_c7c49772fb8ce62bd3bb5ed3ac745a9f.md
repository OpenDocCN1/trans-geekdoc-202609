```
→ background images work as expected. */
background-size: auto;
}
.progress-bar-interrupted, .progress-bar-interrupted::
→-webkit-progress-bar {
background: #F44336;
}
</style>
```

100.00% [38/38 00:03<00:00]

# Let’s compare these two:

For the first 1000 rows, this is what our model mostly worked with:

+   - Max_Humidity,
+   - Events,
+   - Mean_TemperatureC,
+   - Max_Wind_speedKm_h and
+   - Mean_Humidity.

The further we go on this list, the less impact this feature made on the prediction. If the importance goes negative, this means that shuffling this particular

![](bbox=[0.12, 0.58, 0.88, 0.87])

column resulted in a benefit for the accuracy of the model.