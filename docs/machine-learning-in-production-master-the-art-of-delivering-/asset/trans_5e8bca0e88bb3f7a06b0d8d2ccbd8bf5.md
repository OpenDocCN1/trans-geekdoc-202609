

- Tkinter 易于使用，可快速开发桌面应用程序。
- Tkinter 及其小部件的语法易于理解。
- Tkinter 随 Python 一起提供，因此您无需显式安装它。
- Tkinter 是开源的且可免费使用。

## 使用 Tkinter 构建基于 ML 的应用

这里，您需要开发用于数据加载、数据清洗、特征工程、模型构建，最后将训练好的模型保存为 pickle 等序列化对象的 Python 代码。然后，您可以使用训练好的模型在 Tkinter 应用上获得预测。

让我们考虑一个贷款预测场景，目标是预测客户的贷款是否会被批准。重点不在于超参数调整和模型优化。但是，您可以优化模型以提高其整体性能。首先，按如下方式创建 train.py 文件：

```
# Import the required packages
import pandas as pd
import numpy as np
import warnings
warnings.filterwarnings('ignore')
from sklearn.ensemble import RandomForestClassifier

from sklearn import preprocessing
from sklearn.model_selection import train_test_split
from sklearn import metrics
import pickle
```

接下来的步骤，加载数据集并将数值列和分类列的名称分别捕获到单独的变量中。

```
# Load the data
data = pd.read_csv("loan_dataset.csv")
# Missing value treatment (if found)

4. num_col = data.select_dtypes(include=['int64','float64']).columns.tolist()

5. cat_col = data.select_dtypes(include=['object']).columns.tolist()

6. cat_col.remove('Loan_Status')
```

为处理缺失值，您可以使用众数替换分类缺失值，使用中位数替换数值缺失值。

```
1. # Missing value treatment (if found)

2. for col in cat_col:

3. 	data[col].fillna(data[col].mode()[0], inplace=True)

4.

5. for col in num_col:

6. 	data[col].fillna(data[col].median(), inplace=True)
```

与其从数值数据中删除极端值（异常值），不如将其下限限制在 5%，上限限制在 95%。

换句话说，低于 5% 分位数的数据点将被替换为 5% 分位数的值，而另一方面，高于 95% 分位数的数据点将被替换为 95% 分位数的值。

```
1. # Outlier treatment (if found)

2. data[num_col] = data[num_col].apply(

3. 		lambda x: x.clip(*x.quantile([0.05, 0.95])))
```

在许多情况下，联合申请人收入不可用。创建一个名为 TotalIncome 的新特征，它是申请人收入和联合申请人收入的总和。

```
1. # Create a new variable

2. data['TotalIncome'] = data['ApplicantIncome'] + data['CoapplicantIncome']

3. data = data.drop(['ApplicantIncome', 'CoapplicantIncome'], axis=1)
```

您应避免将 Gender 和 Married（婚姻状态）等文本数据传递给模型。使用标签编码技术将分类特征转换为数值特征。目标列 Loan Status 将被编码为数值。

```
1. cat_col.remove('Loan_ID')

2.

3. # Encode categorical features

4. for col in cat_col:

5.     le = preprocessing.LabelEncoder()

6.     data[col] = le.fit_transform(data[col])

7.

8. data['Loan_Status'] = le.fit_transform(data['Loan_Status'])
```

现在，您将使用随机森林分类器构建 ML 模型，并将训练好的模型存储在 pickle 对象中。在这里，您可以使用其他 ML 算法和不同的 ML 技术，例如 GridSearchCV，来提高准确性。在这里，您将构建一个基准 ML 模型。

```
1. # Model building

2. X = data[['Gender', 'Married', 'TotalIncome', 'LoanAmount','Credit_History']]

3. y = data['Loan_Status']

4. features = X.columns.tolist()

5.

6. model = RandomForestClassifier(max_depth=4, random_state = 10)

7.

8. model.fit(X, y)

9.

10. # save the model

11. pickle_model = open("trained_model/model_rf.pkl", mode = "wb")

12. pickle.dump(model, pickle_model)

13. pickle_model.close()

14.

15. # Load the trained model

16. pickle_model = open('trained_model/model_rf.pkl', 'rb')

17. model_rf = pickle.load(pickle_model)

18.

19. prediction = model_rf.predict([[1, 1, 6000, 150, 0]])

20. print(prediction)
```

## Tkinter 应用

完成前面的部分后，您应该有一个训练好的模型的 pickle 对象，它将由 Tkinter 应用使用。在这里，您需要导入两个包，即 **tkinter** 用于构建 GUI，以及 **joblib** 用于加载 pickle ML 模型对象。

创建一个 Python 文件并将其命名为 ml_app.py。

导入 **tkinter** 模块以创建 Tkinter 桌面应用程序。

```
1. from tkinter import *

2.

3. import joblib

4.

5. trained_model = 'E:/tkinter_ml_app/trained_model/model.pkl'

6. model = joblib.load(trained_model)
```

为 ML 应用定义 **MyWindow** 类。在此类中，添加 Tkinter 小部件用于 GUI，并添加 **predict()** 函数以根据用户输入进行预测。在以下代码中，输入字段的标签已使用 **Label()** 小部件创建。

```
1. class MyWindow:

2. def __init__(self, win):

3. # Create a text Label

4. self.lbl0=Label(win, text="Loan Prediction App", font=(25))

5. self.lbl0.pack(pady=10)

6. self.lbl1=Label(win, text='Gender')

7. self.lbl2=Label(win, text='Married')

8. self.lbl3=Label(win, text='Total Income')

9. self.lbl4=Label(win, text='Loan Amount')

10.     self.lbl5=Label(win, text='Credit History')

11.     self.lbl6=Label(win, text='Loan Status')
```

下一步是使用 **Entry()** 小部件为前述字段声明输入框。在此，声明可选参数 **bd**，即输入框 **Entry()** 小部件内部的边框。

**insert()** 小部件在给定位置插入文本。**0**（零）是第一个字符，因此它在开头插入默认文本。

**bind()** 的语法如下：
**widget.bind(event, handler)**

在当前情况下，一个输入小部件通过 **bind()** 链接到 **FocusIn** 事件。这意味着特定的输入小部件已获得焦点，即当给定输入小部件中光标处于活动状态时，它应该执行 **bind()** 内部定义的 lambda 函数。lambda 函数用于在用户单击输入小部件时立即删除其内容。

使用 **Button()** 创建 **Predict** 按钮。

```
1.     # Create an entry widget to accept the user input

2.     self.t1=Entry(bd=2)

3.     self.t1.insert(0, "0:F, 1:M")

4.     self.t1.bind("<FocusIn>", lambda args: self.t1.delete('0', 'end'))

5.

6.     self.t2=Entry(bd=2)

7.     self.t2.insert(0, "0:No, 1:Yes")

8.     self.t2.bind("<FocusIn>", lambda args: self.t2.delete('0', 'end'))

9.

10.    self.t3=Entry(bd=2)

11.    self.t3.insert(0, "E.g. 6000")

12.    self.t3.bind("<FocusIn>", lambda args: self.t3.delete('0', 'end'))

13.

14.   self.t4=Entry(bd=2)

15.   self.t4.insert(0, "E.g. 150")

16.   self.t4.bind("<FocusIn>", lambda args: self.t4.delete('0', 'end'))

17.

18.   self.t5=Entry(bd=2)

19.   self.t5.insert(0, "0:Clear Debts, 1:Unclear Debts")

20.   self.t5.bind("<FocusIn>", lambda args: self.t5.delete('0', 'end'))

21.

22.   self.t6=Entry(bd=2)

23.

24.   # Create a Predict button

25.   self.btn1 = Button(win, text='Predict')
```

Tkinter 带有三个几何管理器：grid、place 和 pack。几何管理器的作用是将小部件排列在特定位置。与其他两个几何管理器相比，place 几何管理器为您提供了更大的灵活性。您可以声明小部件的垂直和水平位置。以下代码提及了每个小部件（包括 **Predict** 按钮）的垂直和水平位置。

```
1.    # Organize widgets appropriately

2.    self.lbl1.place(x=100, y=50)

3.    self.t1.place(x=200, y=50)

4.

5.    self.lbl2.place(x=100, y=100)

6.    self.t2.place(x=200, y=100)

7.

8.    self.lbl3.place(x=100, y=150)

9.    self.t3.place(x=200, y=150)

10.

11.   self.lbl4.place(x=100, y=200)

12.   self.t4.place(x=200, y=200)
```

