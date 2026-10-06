# Step 2. Visualizing the Dataset

The first 10 training images will be displayed using matplotlib library.

Figure 12.

```
import matplotlib.pyplot as plt
img_rows, img_cols, channels= 32,33,2
for i in range(0,9):
    plt.subplot(330 + 1 + i)
    plt.imshow(X_train[i])
plt.show()
```

Figure 13.

![](bbox=[0.218, 0.465, 0.735, 0.765])