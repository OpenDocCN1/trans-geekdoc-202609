```
shap.dependence_plot("PP fiber quantity (kg/m3)", shap_values, x_test,)
```

![](bbox=[0.09, 0.145, 0.64, 0.415])

```
shap.dependence_plot("Moisture content (%)", shap_values, x_test,xmin="percentile(30)", xmax="percentile(90)")
```

![](bbox=[0.09, 0.515, 0.64, 0.785])