```
alpha = 0.8, width = 0.2) +
geom_line(aes(x = snr, y = mean_PVE, color = method)) +
theme_bw() +
theme(legend.position = "bottom") +
labs(x = "SNR", y = "PVE", color = "")

full_plot <- rte_plot + pve_plot

return(full_plot)
}
generate_plot(results, 500, 50, 10)
```

![](bbox=[0.155, 0.355, 0.495, 0.605])

![](bbox=[0.505, 0.355, 0.865, 0.605])

```
generate_plot(results, 500, 100, 10)
```