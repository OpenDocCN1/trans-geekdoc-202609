# 4.13 Saving Plots

![](bbox=[0.118, 0.103, 0.881, 0.263])

FIGURE 4.3

In Windows OS, click the New Folder icon.

![](bbox=[0.345, 0.333, 0.654, 0.403])

FIGURE 4.4

Rename New Folder as plots.

Many of us recall the uncomfortable experiences when the drive name changes automatically (especially when using a thumb drive) on different computers. By using here() from the here package, we will always get to the correct path or folder.

To save the plots in the directory named plots in different image formats, we can do this:

```
ggsave(plot = myplot,
  here("plots", "my_pdf_plot.pdf")
```

```
# Saving 6.5 x 4.5 in image
## geom_smooth() using method = 'loess' and formula = 'y ~ x'
```

```
ggsave(plot = myplot,
  here("plots", "my_png_plot.png")
```

```
# Saving 6.5 x 4.5 in image
## geom_smooth() using method = 'loess' and formula = 'y - x'
```

```
ggsave(plot = myplot,
  here("plots", "my_jpg_plot.jpg")
```