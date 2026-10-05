
[content]

# 表 A.2 逻辑回归代码——续

| 每个折叠中测试样本的评估指标 |
| :--- |
| acc_t.append(accuracy_score(y_test, y_pred)) f1_t.append(score(y_test, y_pred)) |
| roc_t.append(roc_auc_score(y_test, y_pred)) # 打印训练样本上的结果 |
| print(np.mean(np.array(acc))) print(np.mean(np.array(f1))) print(np.mean(np.array(roc))) |
| # 打印测试样本上的结果 print(np.mean(np.array(acc_t))) |
| print(np.mean(np.array(f1_t))) print(np.mean(np.array(roc_t))) |

# 10. 支持向量机

SVM 见表 A.3。

表 A.3 支持向量机。

| import numpy as np pandas as pd import deepchem as dc |
| :--- |
| from sklearn.linear_model import LogisticRegression |
| from sklearn.metrics import accuracy_score, roc_auc_score, f1_score |
| from sklearn.model_selection import KFold from sklearn.svm import SVC # 如果你使用 |
| Google Colab 运行代码，你需要挂载驱动器 # 如果你使用自己的电脑 |
| 运行代码，你不需要这些来自 google.colab 的命令 import |
| drive.mount('/content/drive') # 读取数据 |
| data = np.read_csv('/content/drive/My_tox21.csv') |
| smiles = data.loc[:], data.columns = 'smiles' labels = data.loc[:], data.columns = 'NR-AR-LBD' # 使用 DeepChem 为每个 SMILES 序列提取 ECFP 特征 |
| featureizer = dc.CircularFingerprint(size=1024) ecfp = featureizer.featurize(smiles) |
| XD=[]- for i in range(len(smiles)): ecfp = featureizer.featurize(smiles.loc[i]) ecfp = |
| np.square(ecfp) XD = np.append(XD,index[0]) # 为了评估模型，使用 k 折交叉验证 |
| 从数据集中带有 NaN 标签的样本 index = np.where(np.isnan(labels)) labels = |
| labels[index[0]] k=KFold(splits=5) kf.get_n_splits(XD) acc=1, acc_t=[], f1_t=[], roc_t=[] |
| [] for train_index, test_index in kf.split(XD): |
| X_train, X_test = XD[train_index], XD[test_index] |
| y_train, y_test = labels[train_index], labels[test_index] y_train = y_train + (-1)*(train==0) |
| y_test = y_test + (-1)*(test==0) # 在训练样本上拟合 SVM 模型。核函数 |
| 参数可以设置为另一个值。需帮助，请参阅或 |
| scikit-learn 软件包的文档。 |
| clf = SVC(gamma='auto', kernel='rbf', class_weight='balanced').fit(X_train, y_train) |
| y_pred = clf.predict(X_train) # 计算每个折叠中训练样本的评估指标 |
| acc.append(accuracy_score(y_train, y_pred)) f1.append(f1_score(y_train, y_pred)) |
| roc.append(roc_auc_score(y_train, y_pred)) y_pred = clf.predict(X_test) # 计算 |

# 表 A.3 支持向量机——续

| 每个折叠中测试样本的评估指标 |
| :--- |
| acc_t.append(accuracy_score(y_test, y_pred)) f1_t.append(score(y_test, y_pred)) |
| roc_t.append(roc_auc_score(y_test, y_pred)) # 打印训练样本上的结果 |
| print(np.mean(np.array(acc))) print(np.mean(np.array(f1))) print(np.mean(np.array(roc))) |
| # 打印测试样本上的结果 print(np.mean(np.array(acc_t))) |
| print(np.mean(np.array(f1_t))) print(np.mean(np.array(roc_t))) |

# 11. 随机森林代码

随机森林代码见表 A.4。

# 表 A.4 随机森林。

```python
import numpy as np pandas as pd import deepchem as ds
from sklearn.metrics import accuracy_score, roc_auc_score, f1_score
from sklearn.model_selection import KFold
from sklearn.ensemble import RandomForestClassifier # 如果你使用 Google Colab 运行
t 代码，你需要挂载驱动器 # 如果你使用自己的电脑运行代码，你不需要
need 这些来自 google.colab 的命令 drive.mount('/content/drive') # 读取
data data = pd.read_csv('/drive/smiles.csv'); labels = data.loc[:]; data.columns == 'NR-AHR' # 应该选择另一个任务 # 使用 DeepChem 为每个 SMILES 序列提取 ECFP 特征 featurizer=dc.CircularFingerprint(size=1024) XD = []
for i in range(len(smiles)): ecfp = featurizer.featurize(smiles.loc[i]) ecfp = np.squeeze(ecfp)
XD.append(ecfp) labels = np.array(labels) # 从数据集中移除 NaN 标签 index = np.where(np.isnan(labels)) labels = labels[index[0]], # 使用交叉验证评估模型
kf = KFold(n_splits=5); acc = [], acc_t = [], roc_t = [] for train_index, test_index in kf.split(XD)
print("TRAIN", train_index, "TEST:", test_index)
X_train, X_test = XD[train_index], XD[test_index]
y_train, y_test = labels[train_index], labels[test_index] # 在训练样本上拟合随机森林模型。"estimators", "criterion" 和 "max_depth" 可以设置为另一个值。需帮助，请参阅 scikit-learn 的文档。
clf = RandomForestClassifier(estimators=100,criterion='gini',class_weight='balanced',max_depth=4).fit(X_train, y_train)
y_pred = clf.predict(X_train) # 计算每个折叠中训练样本的评估指标
acc.append(accuracy_score(y_train, y_pred)) f1.append(f1_score(y_train, y_pred))
roc.append(roc_auc_score(y_train, y_pred)) y_pred = clf.predict(X_test) # 计算每个折叠中测试样本的评估
acc_test.append(accuracy_score(y_test, y_pred))
```

# 表 A.4 随机森林——续

| roc_t.append(roc_auc_score(y_test, y_pred)) # 打印训练样本上的结果 |
| print(np.mean(np.array(acc))) print(np.mean(np.array(f1))) print(np.mean(np.array(roc))) |
| # 打印训练样本上的结果 print(np.mean(np.array(acc_t))) |
| print(np.mean(np.array(f1_t))) print(np.mean(np.array(roc_t))) |

# 12. 回归任务的深度学习

回归任务的深度学习见表 A.5。

表 A.5 回归任务的深度学习。

```python
import numpy as np pandas as pd import keras
from keras.models import Model
from keras.preprocessing import sequence
from keras.models import Sequential, load_model
from keras.layers import Dense, Dropout, Activation
from keras.layers import Embedding
from keras.models import Model
from keras.callbacks import ModelCheckpoint, EarlyStopping
from keras import optimizers, layers from tensorflow.keras import regularizers
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error, r2_score # 如果你使用 Google Colab
run 代码需要挂载驱动器到你的电脑运行代码，你不需要这些来自 google.colab 的命令 drive.mount('/content/drive') # 读取数据 data = pd.read_csv('/content/Drive/Delney-processed.csv')
smiles = data.loc['smiles']
labels = data.loc['ESOL predicted log solubility in mols per litre'] # 将 SMILES 句子的每个元素显示为整数（数字）
smiles_dict = {"#2": "29", "#30": "31", "#31": "1", "#4": "32", "#33": "34", "#2": "2", "#35": "0", "#3": "3", "#36": "2", "#4": "5", "#37": "4", "#5": "7", "#8": "6", "#9": "9", "#8": "7", "#40": "4", "#41": "A", "#42": "8", "#42": "B", "#9": "E", "#43": "D", "#10": "G", "#44": "F", "#11": "#45": "H5", "#12": "K", "#46": "M", "#47": "L", "#13": "O", "#48": "N", "#14": "P", "#15": "S", "#49": "#16": "R", "#16": "U", "#50": "T", "#17": "W", "#51": "V", "#18": "Y", "#52": "#53": "Z", "#23": "Z", "#19": "54", "#20": "a", "#55": "s", "#56": "b", "#21": "e", "#57": "d", "#22": "g", "#58": "#23": "f", "#24": "l", "#59": "h", "#60": "o", "#25": "i", "#61": "n", "#26": "s", "#62": "#27": "t", "#28": "u", "#64": "6", "#65": "6", "#67": "67", "#68": "p", "#69": "j"}
```

# 表 A.5 回归任务的深度学习——续

| 以及设置 X_train, X_test, y_train, y_test = train_test_split(labels, test_size=0.3) |
| :--- |
| 定义模型的架构 XInput(shape=(100,)) |
| FC1 = Dense(1024, activation='relu')(XInput) |
| FC2 = Dropout(0.1)(FC1) |
| FC3 = Dense(1024, activation='relu')(FC2) |
| FC4 = Dropout(0.1)(FC3) |
| FC5 = Dense(512, activation='relu')(FC4) |
| predictions = Dense(1,activity_regularizer=Regularizers.l1(1e-5))(FC5) # 创建模型 |
| interactionModel = Model(inputs=XInput, outputs=predictions) # 在输出中打印
| 模型架构 interactionModel.summary() # 编译模型。选择损失 |
| 函数、优化器算法和指标 |
| interactionModel.compile(optimizer='sgd', loss='mse', metrics=['mse']) # 准备 |
| 馈模型的训练数据 XD = np.array(X_train) labels = np.array(y_train) |
| 从训练样本中移除带有 NaN 标签的样本 index = |
| np.where(~np.isnan(labels)) labels = labels[index[0],:] XD = XD[index[0],:] # 训练模型 |
| interactionModel.Fit(XD,labels, batch_size=256,epochs=100) # 在训练样本上预测 |
| 样本 y_pred = interactionModel.predict(np.array(XD)) # 打印训练样本
| 评估指标 print(mean_squared_error(labels, y_pred)) |
| print(r2_score(labels, y_pred)) |

