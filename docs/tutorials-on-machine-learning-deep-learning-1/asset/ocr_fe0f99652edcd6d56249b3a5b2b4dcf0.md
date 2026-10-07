| Index | Type | Value |
|---|---|--|
| 0 | list | (8.0, 3.0, 4.0, 3.0, 0.0, 4.0, 1.0, 0.0, ...) |
| 1 | list | (4.0, 0.0, 0.0, 0.0, 0.0, 0.0, ...) |
| 2 | list | (8.0, 0.0, 0.0, 0.0, 0.0, 0.0, ...) |
| 3 | list | (8.0, 0.0, 0.0, 0.0, 0.0, 0.0, ...) |
| 4 | list | (8.0, 0.0, 0.0, 0.0, 0.0, 0.0, ...) |
| 5 | list | (4.0, 0.0, 0.0, 0.0, 2.0, 0.0, ...) |
| 6 | list | (8.0, 0.0, 0.0, 0.0, 0.0, 0.0, ...) |
| 7 | list | (8.0, 0.0, 0.0, 0.0, 0.0, 0.0, ...) |
| 8 | list | (8.0, 0.0, 0.0, 0.0, 0.0, 0.0, ...) |
| 9 | list | (8.0, 0.0, 0.0, 0.0, 0.0, 0.0, ...) |

![](bbox=[0.535, 0.041, 0.856, 0.246])

Notice each line has different ratings now. Since we use *dict* rated ratings *1, 6, 10,* and *12*, many there could be less, *0* for those.

Also used *list()*, to make sure that *ratings* are a **list**.

```
new_data.append(list(ratings))
```

Note in following, range is there because no *user0* in our dataset, and *loop* excludes *nb_users + 1*, so our users will be **nb_users**.

```
for id in range(1, nb_users + 1):
```

# 14.4.6 Data Preprocessing 4: Convert Matrices to torch.Tensor

We've converted our **training set** and **our test set** into **arrays** of **users** in lines and **movies** in columns.

+   * The **columns** are the *features* that are going to be the **input nodes** in the **network**.

+   * For each we will have its ratings of *all the movies*, *zeros*, and these are going to be the **input nodes** for this observation going into the **network**.

+   * Then **PyTorch** comes into place, we will build the architecture with PyTorch **tensors**.

+   * A tensor is a multi-dimensional array but instead of a *NumPy* array, this is a **PyTorch array**.

+   * In fact, we could build it with *NumPy* array, but that would be less efficient and that we're using **tensors** using the **torch tensors**.

**NOTE**: With **TensorFlow** have exactly the same. With **TensorFlow** we work with tensors.

+   * Those are another kind of **tensor**, another of **multi-dimensional matrix**, and so we could implement our **AE/RM** from scratch with **TensorFlow**

+   * But for **AE/RM**, **PyTorch** gives better results, and also this is much simpler.

```
# Converting the data into Torch Tensors
train_set = torch.FloatTensor(train_set_cnt)
test_set = torch.FloatTensor(test_set_cnt)
```

Now **training set** and **test set** are torch tensors. two are multi-dimensional matrices by **PyTorch**.

+   * We used the class **FloatTensor**, that creates two objects of this **train_set** and **test_set**: These objects will be the **torch.tensor**.

+   * A **tensor** is a multi-dimensional array with a single **data-type**. Since we're taking the **FloatTensor** class, the data-type will be **float**.

+   * Inside each those classes, we use one **argument** which has to be a **list of lists**, our **train-set** and **test-set** (list-lists).

+   * The **FloatTensor** class expects a **list of**.