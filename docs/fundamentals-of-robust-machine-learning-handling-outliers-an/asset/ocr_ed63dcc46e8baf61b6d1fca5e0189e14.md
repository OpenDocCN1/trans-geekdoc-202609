```
```python
setx_df['yval'] = sety_df['yval']
setx_df['flag'] = setr_df['flag']
set1 = setx_df[setx_df['flag']==1]
set0 = setx_df[setx_df['flag']==0]
plt.scatter(set1['xval'], set1['yval'], color='red')
plt.scatter(set0['xval'], set0['yval'], color='blue')
plt.show()
```
```

# **8.4** (Project) In this project, you will run CELR using the LogisticRegression() module of the sklearn library. The code below assumes that the previous project was completed.

# a) Create a data frame with a polynomial expansion of order 2 of the two variables.

```
```python
setx_df = pd.DataFrame(setx,columns=["xval"])
sety_df = pd.DataFrame(sety,columns=["yval"])
setr_df = pd.DataFrame(y,columns=['flag'])
setx_df['yval'] = sety_df['yval']
setx_df['flag'] = setr_df['flag']
setx_df['x2'] = setx_df['xval']**2
setx_df['y2'] = setx_df['yval']**2
setx_df["Ones"] = 1
train_df = setx_df[setx_df['flag']!=-1]
train_df.head()
```
```

# b) Run logistic regression based on CELR.

```
```python
Xd = train_df.drop(["flag","Ones"],axis=1)
X = np.array(Xd)
y1 = train_df["flag"]
y = np.array(y1)
logreg = LogisticRegression()
logreg.fit(X, y)
```
```

# c) Plot the nonlinear decision boundary and comment on the results.

```
```python
b1 = [logreg.coef_[0,0],logreg.coef_[0,1],
logreg.coef_[0,2], logreg.coef_[0,3],
logreg.intercept_]
plt.figure() # Create a new figure window
set1 = train_df[train_df['flag']==1]
set0 = train_df[train_df['flag']==0]
plt.scatter(set1['xval'],set1['yval'], \
color='red')
plt.scatter(set0['xval'],set0['yval'], \
color='blue')
```
```