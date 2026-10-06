In [4]: from sklearn import preprocessing
Input = preprocessing.scale(dt.drop(columns='Rainfall')).values
Output = dt['Rainfall']
inp_X,tst_X,out_y,tst_y = train_test_split(
Input,Output,test_size=0.2)
CModel = linear_model.LogisticRegression()
CModel.fit(inp_X,out_y)

Out[4]: LogisticRegression()

Our model is trained. Now we can test model’s predictions with actual values. To visualize it we need to use the LabelEncoder and encode the Rainfall labels into numeric values. We will also print the accuracy of our model

Accuracy: 0.4315690860872

Out[5]: <matplotlib.axes.AxesSubplot object at 0x239fe07>

![](bbox=[0.293, 0.621, 0.813, 0.856])

so our model didn’t performed well. So here’s a question for you - why is the accuracy of our model is below 50%? (without reading further)