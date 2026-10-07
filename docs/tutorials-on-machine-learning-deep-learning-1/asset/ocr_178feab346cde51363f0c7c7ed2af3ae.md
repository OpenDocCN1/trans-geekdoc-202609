Since Dummy variables of Geography appears first in our feature matrix, we need not to rearrange the columns for our new data-point = new_dt_pt,

Also we not need to re-arrange other columns, they are in order.

From, row_no = 0 to 4 and 6 we notice Male = 1 and female = 0
Credit card: yes = 1, no = 0
Active-member: yes = 1, no = 0

Hence we represent our new data-point new_dt_pt as:
0.0, 0.0, 600, 1, 40, 3, 60000.0, 2, 1, 50000.0

If we use it as a list, it won't be a row, it will be a vector/column:
[[0.0, 0.0, 600, 1, 40, 3, 60000.0, 2, 1, 50000.0]]

To make it as row of the feature matrix we define it as a List-of [[1]], as 1x11 matrix
[[0.0, 0.0, 600, 1, 40, 3, 60000.0, 2, 1, 50000.0]]

NumPy array: also need to convert it to NumPy array, use np.array (here imported as np):
np.array([[0.0, 0.0, 600, 1, 40, 3, 60000.0, 2, 1, 50000.0]])
We put it the called variable new_dt_pt.

Scale: We scale this new data-point new_dt_pt, using our Standard Scaler st_x.
Predict: Finally predict the new-data-dt_pt, using the classifier ann_classifier and transformed the probability intoTrue/False using threshold: 0.5.

```
new_dt_pt = np.array([[0.0, 0.0, 600, 1, 40, 3, 60000.0, 2, 1, 50000.0]])
new_dt_pt = st_x.transform(new_dt_pt) # scaling
predict_data_pt = ann_classifier.predict(new_dt_pt) > 0.5
```

All code for new data-point prediction

```
# create a 2D "NumPy array" (in our x_train.format)
# it will be similar to a single row of our x_train
# "used to define a single row of a 2-D array
new_data_pt = np.array([[0.0, 0.0, 600, 1, 40, 3, 60000.0, 2, 1, 50000.0]]) # scaling
new_data_pt = st_x.transform(new_data_pt) # scaling
predict_data_pt = ann_classifier.predict(new_data_pt) > 0.5 # Predict the data-point
```

Result: The prediction is "False". That is the customer not going to leave the Bank since Leave = 1, stay = 0 in deponent variable, "Exited". Here True/False is predicted by 0.

| new_dt_pt | Array of float64 | [[-0.5690444 -0.5739368 -0...]] |
|---|---|---||
| predict_data_pt | Array of bool | (1, 11) | [[False]] |

Hence we don't Goodbye to that customer.