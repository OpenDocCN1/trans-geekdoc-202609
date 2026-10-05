# Listing 2.38 HouseMNIST.ipynb (part 1)
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

df = pd.read_csv('houses.csv')
df.describe(include='all')

The variable df is a data frame which is a Panda that contains the values and further information. We will be using mainly NumPy arrays that allow simpler vector and matrix operations. We can take some data from the Panda data frame and read them into another. The following program does this and also plots the first ten data points for the house price using the living area in square feet.

# Listing 2.39 HouseMNIST.ipynb (part 2)
Y = df['price_(grands'].values
X = df['sqft_living'].values
plt.plot(X[:10], Y[:10], 'x')

| | bedrooms | bathrooms | sqft_living |
|---|---|---|---||
| count | 21613 | 21613 | 21613 | 21613 |
| mean | 540000 | 3.37 | 2.11 | 2080 |
| std | 367000 | 0.93 | 0.77 | 918 |
| min | 75000 | 0 | 0 | 290 |
| 25% | 321000 | 3 | 1.75 | 1427 |
| 50% | 450000 | 3 | 2.2 | 1900 |
| 75% | 645000 | 4 | 2.5 | 2250 |
| max | 7700000 | 33 | 8 | 13540 |

![](bbox=[0.465, 0.483, 0.796, 0.649])

Fig. 2.7 House price versus size area for houses in King County.

Another famous dataset that we will use is the MNIST dataset from the website <http://yaml.lecun.com/mnist> in a compressed file. This data are also included in machine learning packages, though here we should point out another collection of data which is provided by <https://www.openml.org>. The MNIST dataset contains hand-written numbers first collected by the National Institute for Standards and Technology (NIST) and modified (the M is centered in 28 x 28 images). This specific dataset is called mnist (https://www.openml.org/dataset/554).

The Openml site provides a variety of formats to download them. Since we can download these data also in the csv file, we can use a similar code as in the house example. This version shows how to read columns into a data matrix. Since each image is written into a line, we have to reshape each vector into a matrix before plotting it. An example is shown in Fig. 2.8A.