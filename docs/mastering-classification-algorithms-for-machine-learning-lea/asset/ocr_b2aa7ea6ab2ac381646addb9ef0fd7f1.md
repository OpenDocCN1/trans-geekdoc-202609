id2699

```
0 19
1 37
2 28
3 99
4 32
```

[5 rows x 2703 columns]

Note that for each image, we have 2,702 features (1 column out of the 2,703 columns being developed for the label.

Now let us visualize the images. First, we will randomly pick any data point and see the traffic sign in that image. Notice that we can use the method imshow() from the matplotlib library to display an image.

```
from skimage.io import imread, imshow
```

```
import matplotlib.pyplot as plt
```

```
%matplotlib inline
```

```
dfTemp = df.drop([COLUMN_FILEPATH, COLUMN_FILENAME, COLUMN_LABEL],
            axis = 1, inplace = False)
```

```
columns = dfTemp.columns
```

```
def getImage(rowNumber):
    image1DArray = np.empty([RESIZE_X * RESIZE_Y * CHANNELS])
```

```
for column in columns:
```

```
    columnNumber = int(column.replace(COLUMN_IDENTIFIER, ''))
    image1DArray[columnNumber] = int(dfTemp.iloc[rowNumber][column])
```