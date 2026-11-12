![](bbox=[0.135, 0.125, 0.855, 0.675])

FIGURE 1.23 Results of the opening and closing operations on grayscale images. (a) Original image, (b) image with salt and pepper noise, (c) result of the opening operation on (b), (d) result of the closing operation on (b), and (e) result of the filter of opening and closing on (b).

This process is known as a ‘sequential filter’. The effect of this filter on grayscale images allows for smoother results than those obtained by simply opening and closing the filter (Figure 1.24). Algorithm 1.2 shows the process of implementing the sequential filter.