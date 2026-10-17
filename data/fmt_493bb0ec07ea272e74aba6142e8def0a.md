
0 iter: 1.0985916677722303
480 iter: 0.7056240023920841
960 iter: 0.6422407772314334
1440 iter: 0.5246104670488081
1920 iter: 0.4186441561530432
2400 iter: 0.37118840941018727
2880 iter: 0.34583485668931857
3360 iter: 0.32954842747580104
3840 iter: 0.31961537369884196
4320 iter: 0.3124394704919282
4800 iter: 0.30620107113884415

![](img/file98.png)

**图 4-31 损失曲线**

改进后的神经网络框架网站代码位于文件 `NeuralNetwork.py` 中。

### 4.3.9 Fashion-MNIST 分类训练

以下代码使用 Fashion-MNIST 训练集训练神经网络模型：

```python
import mnist_reader
X_train, y_train = mnist_reader.load_mnist('data/fashion', kind='train')
X_test, y_test = mnist_reader.load_mnist('data/fashion', kind='t10k')
print(X_train.shape, y_train.shape)
print(X_train.dtype, y_train.dtype)
```

```
(60000, 784) (60000,)
uint8 uint8
```

```python
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
trainX = X_train.reshape(-1, 28, 28)
print(trainX.shape)
# plot first few images
for i in range(9):
    # define subplot
    plt.subplot(330 + 1 + i)
    # plot raw pixel data
    plt.imshow(trainX[i], cmap=plt.get_cmap('gray'))
# show the figure
plt.show()
```

```
(60000, 28, 28)
```

![](img/file99.png)

**图 4-32 Fashion 数据集中的图像**

观察数据值可知，原始值应为 0-255 的整数，除以 255 后可转换为 0 到 1 之间的实数：

```python
train_X = trainX.astype('float32') / 255.0
print(np.mean(trainX), np.mean(train_X))
```

```
72.94035223214286 0.2860402
```

定义训练的神经网络模型：

```python
import numpy as np
import util
np.random.seed(1)

nn = NeuralNetwork()
nn.add_layer(Dense(784, 500))
nn.add_layer(Relu())
nn.add_layer(Dense(500, 200))
nn.add_layer(Relu())
nn.add_layer(Dense(200, 100))
nn.add_layer(Relu())
nn.add_layer(Dense(100, 10))
```

定义优化器对象：

```python
learning_rate = 0.01
momentum = 0.9
optimizer = SGD(nn.parameters(), learning_rate, momentum)
```

开始训练：

```python
epochs = 8
batch_size = 64
reg = 0  # 1e-3
print_n = 1000

losses = train_nn(nn, train_X, y_train, optimizer, cross_entropy_grad_loss, epochs, batch_size, reg, print_n)

plt.plot(losses)
```

#### 训练损失曲线

```
0 iter: 2.3016755298047347
1000 iter: 1.1510374540057933
2000 iter: 0.47471113470221005
3000 iter: 0.5333139450988945
4000 iter: 0.259167391843765
5000 iter: 0.3629363583454308
6000 iter: 0.3486191552507917
7000 iter: 0.4914253677369693
```

![](img/file100.png)

**图 4-33 训练损失曲线**

```python
print(np.mean(nn.predict(train_X)==y_train))
test_X = X_test.reshape(-1,28,28).astype('float32')/255.0
print(np.mean(nn.predict(test_X)==y_test))
```

```
0.87965
0.8585
```

### 4.3.9 读写模型参数

有时模型训练时间很长，可以暂停训练过程，将训练好的模型参数保存到文件中，下次再从文件中读取模型参数，以便在上次训练的基础上继续训练。为此，可以在神经网络类 `NeuralNetwork` 中添加读取（`save_parameters()`）和写入（`load_parameters()`）模型参数的功能：

```python
class NeuralNetwork:  
    def __init__(self):
        self._layers = []
        self._params = []
 
    def add_layer(self, layer):      
        self._layers.append(layer)
        if layer.params: 
           # for  i in range(len(layer.params)): 
            for  i, _ in enumerate(layer.params):                         
                self._params.append([layer.params[i],layer.grads[i]])            
    
    def forward(self, X): 
        for layer in self._layers:
            X = layer.forward(X) 
        return X   

    def __call__(self, X):
        return self.forward(X)
    
    def predict(self, X):
        p = self.forward(X)       
        if p.ndim == 1:     #single sample
            return np.argmax(ff)  
        return np.argmax(p, axis=1)   # multiple samples  
   
    def backward(self,loss_grad,reg = 0.):
        for i in reversed(range(len(self._layers))):
            layer = self._layers[i] 
            loss_grad = layer.backward(loss_grad)
            layer.reg_grad(reg) 
        return loss_grad
    
    def reg_loss(self,reg):
        reg_loss = 0
        for i in range(len(self._layers)):
            reg_loss+=self._layers[i].reg_loss(reg)
        return reg_loss
    
    def parameters(self): 
        return self._params
    
    def zero_grad(self):
        for i,_ in enumerate(self._params):           
            #self.params[i][1].fill(0.) 
            self.params[i][1][:] = 0 
            
    def get_parameters(self):
        return self._params   
    
    def save_parameters(self,filename):
        params = {}
        for i in range(len(self._layers)):
            if self._layers[i].params:
                params[i] = self._layers[i].params
        np.save(filename, params)               
        
    def load_parameters(self,filename):
        params = np.load(filename,allow_pickle = True)
        count = 0
        for i in range(len(self._layers)):
            if self._layers[i].params:
                layer_params = params.item().get(i)
                self._layers[i].params = layer_params                
                for j in range(len(layer_params)):                   
                    self._params[count][0] = layer_params[j]
                    count+=1   
```

使用以下代码测试上述模型的读写功能。

```python
from NeuralNetwork import *
nn = NeuralNetwork()
nn.add_layer(Dense(3, 2,('xavier',0.01)))
nn.add_layer(Relu())
nn.add_layer(Dense(2, 4,('xavier',0.01)))
nn.add_layer(Relu())

def print_nn_parameters(params,print_grad=False): 
    for p,grad in params:  
        print("p",p)
        if print_grad:
            print("grad",grad)
        print()    
print_nn_parameters(nn.get_parameters())
nn.save_parameters('model_params.npy')
nn.load_parameters('model_params.npy')
print_nn_parameters(nn.get_parameters())
```

```
p[[0.0027318 0.00063939]
     [-0.00144845 0.00138133]
     [-0.01521812 0.0023785 ]]
    
p [[0.0.]]
    
p [[-0.00825534 -0.01301992 0.00130655 0.00532404]
     [-0.01092436 -0.00243776 0.00889602 0.00531146]]
    
p [[0. 0. 0. 0.]]
    
p[[0.0027318 0.00063939]
     [-0.00144845 0.00138133]
     [-0.01521812 0.0023785 ]]
    
p [[0.0.]]
    
p [[-0.00825534 -0.01301992 0.00130655 0.00532404]
     [-0.01092436 -0.00243776 0.00889602 0.00531146]]
    
p [[0. 0. 0. 0.]]
```

![](img/file238.png)![](img/file239.png)![](img/file240.png)![](img/file241.png)![](img/file242.png)![](img/file243.png)![](img/file244.png)![](img/file245.png)![](img/file246.png)![](img/file247.png)![](img/file248.png)![](img/file249.png)![](img/file250.png)![](img/file251.png)![](img/file252.png)![](img/file253.png)![](img/file254.png)![](img/file255.png)![](img/file256.png)![](img/file257.png)![](img/file258.png)

数据和算法是机器学习的两大要素。优质的数据和优秀的算法都能提升机器学习的性能与效果。高质量数据的获取需要成本。如何在现有数据基础上通过数据处理和增强提升数据质量与数量，以及如何通过各种实战技巧提升机器学习模型和算法的性能，也是基于神经网络的深度学习实践必备技能。

## 5.1 数据处理

现代人工智能实践证明，数据是机器学习的关键。神经网络原理简单明了，它之所以能在众多复杂的机器学习方法中脱颖而出，关键在于数据。数据越多，机器学习性能越好。当然，高性能硬件可以提高算法执行效率，但算法效果取决于是否有足够多样的训练数据。对于过拟合函数，增加数据量能有效改善过拟合。除了数据量，数据质量也很重要。除了通过收集、生成数据等各种手段获取尽可能多的数据外，数据增强、归一化、特征工程是常用的数据处理方法，用于在现有数据情况下增加数据量、提高数据质量。

### 5.1.1 数据增强

数据增强是指在现有数据条件下，通过对数据进行各种变换和裁剪来增加数据量。例如对一幅图像，通过镜像、旋转、剪切、变形、滤波、变色、加噪、遮挡等图像操作，可以从一张原始图像变换出许多图像，从而增加数据总量。

以下代码可使用 `skimage` 的 `io` 模块读取图像：

```python
import numpy as np
import matplotlib.pyplot as plt
from skimage import io, transform

image = io.imread('cat.png')
print(image.shape)
plt.imshow(image)
plt.show() 
```

```
(403, 544, 3)
```

![](img/file101.png)

**图 5-1 原始图像**

图像的高和宽分别为 403 和 544，彩色图像由红（R）、绿（G）、蓝（B）三个通道图像组成。即每个位置的图像像素由红（R）、绿（G）、蓝（B）三种颜色组成。

可以通过 `numpy` 数组操作对图像进行各种变换，例如 `image[:,::-1, :]` 可对图像进行水平镜像翻转：

```python
img = image[:,::-1, :]
plt.imshow(img)
plt.show() 
```

![](img/file102.png)

**图 5-2 水平翻转**

另一个例子是窗口裁剪图像：

```python
img = image[50:300,90:400, :]
plt.imshow(img)
plt.show() 
```

![](img/file103.png)

**图 5-3 裁剪图像**

或者直接处理图像的每个像素：

#### 图像处理示例
