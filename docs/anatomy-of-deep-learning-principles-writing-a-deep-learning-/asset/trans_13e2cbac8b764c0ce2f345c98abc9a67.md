
`X_row = X.transpose(0,2,3,1).reshape(-1,F)`

然后根据反向推导公式，可以计算出该转置卷积输出的扁平化矩阵 `Z_row`，即：

```
Z_row = np.dot(X_row,K_col.T)
```

最后，根据卷积的反向推导过程，必须将该 `Z_row` 每一行的分布累加到最终输出 `Z` 中。此过程可直接使用 `row2im()` 函数或 `row2im_indices()` 函数完成：

```
Z = row2im_indices(Z_row,Z_shape,self.kH,self.kW,S =self.S,P = self.P)
```

同理，转置卷积的反向推导类似于卷积的正向计算过程。首先，必须将损失函数关于 `Z` 的梯度 `dz` 通过 `im2row()` 或 `im2row_indices()` 函数展平为矩阵 `dZ_row`，其每一行代表一个数据块，然后计算转置卷积输入 `X` 的梯度：

```
dX_row = dZ_row @ K_col
```

可得到关于 `X` 的梯度的扁平化矩阵 `dX_row`，最后将该扁平化矩阵重塑为与 `X` 形状相同的四维张量，即：

```
dX = dX_row.reshape(N,self.H,self.W,self.C)
dX = dX.transpose(0,3,1,2)
```

同理，模型 `K` 的梯度 `dK_col` 的计算过程也类似，将扁平化矩阵 `dK_col` 的形状重塑为与 `K` 相同的形状更为直接：

```
dK_col = self.X_row.T@dZ_row
dK = dK_col.reshape(self.K.shape)
```

根据上述分析，可编写如下转置卷积类 `Conv_transpose`：

```
class Conv_transpose():
    def __init__(self, in_channels, out_channels, kernel_size, stride=1,padding=0):
        super().__init__()
        self.C = in_channels
        self.F = out_channels
        self.kH = kernel_size
        self.kW = kernel_size
        self.S = stride
        self.P = padding
        # filters is a 3d array with dimensions (num_filters, self.K, self.K)
        # you can also use Xavier Initialization.
        #self.K = np.random.randn(self.F, self.C, self.kH, self.kW) #/(self.K*self.K)
        # self.K = np.random.randn(self.C, self.F, self.kH, self.kW) #/(self.K*self.K)
        self.K = np.random.normal(0,1,(self.C, self.F, self.kH, self.kW))
        self.b = np.zeros((1,self.F)) #,1))
        self.params = [self.K,self.b]
        self.grads = [np.zeros_like(self.K),np.zeros_like(self.b)]
        self.X = None
        self.reset_parameters()

    def reset_parameters(self):
        kaiming_uniform(self.K, a=math.sqrt(5))
        if self.b is not None:
            fan_in, _ = calculate_fan_in_and_fan_out(self.K)
            #fan_in = self.F
            bound = 1 / math.sqrt(fan_in)
            self.b[:] = np.random.uniform(-bound,bound,(self.b.shape))

    def forward(self,X):
        '''
        X:       (N,C,H,W)
        K:       (F,C,kH,kW)
        Z:       (N,F,oH,oW)
        X_row:   (N*oH*oW, C*kH*kW)
        K_col:    (C*kH*kW, F)
        Z_row = X_row*K_col:  (N*oH*oW, C*kH*kW)*(C*kH*kW, F) =  (N*oH*oW, F)
        dK_col = X_row.T @dZ_row: (C*kH*kW,N*oH*oW)*(N*oH*oW, F) = (C*kH*kW,F)
        dX_row = dZ_row@K_col.T = (N*oH*oW, F) * (F, C*kH*kW) = (N*oH*oW, C*kH*kW)
        '''
        #convert to multi-channel
        self.X = X
        if len(X.shape)==1:
            X = X.reshape(X.shape[0],1,1,1)
        elif len(X.shape)==2:
            X = X.reshape(X.shape[0],X.shape[1],1,1)
        self.N,self.H,self.W = X.shape[0], X.shape[2], X.shape[3]
        S,P,kH,kW = self.S, self.P,self.kH,self.kW
        self.oH =self.S*(self.H-1)+kH-2*P
        self.oW = self.S*(self.W - 1)+kW - 2*P
        K = self.K
        # Convert (N,F,oH,oW) to (N,oH,oW,F) and flatten to (-1,F)
        F = X.shape[1]
        #assert(F==self.F)
        X_row = X.transpose(0,2,3,1).reshape(-1,F)   #(N*oH*oW,F)
        K_col = K.reshape(K.shape[0],-1).transpose()  #Flattening
        Z_row = np.dot(X_row,K_col.T)
        Z_shape = (self.N,self.F,self.oH,self.oW)
        Z = row2im_indices(Z_row,Z_shape,self.kH,self.kW,S =self.S,P = self.P)
        self.b = self.b.reshape(1,self.F,1,1)
        Z+= self.b
        self.X_row = X_row
        return Z

    def __call__(self,X):
        return self.forward(X)

    def backward(self,dZ):
        N,F,oH,oW = dZ.shape[0], dZ.shape[1],dZ.shape[2], dZ.shape[3]
        S,P,kH,kW = self.S, self.P,self.kH,self.kW
        dZ_row = im2row_indices(dZ,self.kH,self.kW,S=self.S,P=self.P)
        K_col = self.K.reshape(self.K.shape[0],-1).transpose()  #Flattening
        dX_row = dZ_row @ K_col    # (o,f) = (9,18)(18,1) = (9,1)
        dK_col = self.X_row.T@dZ_row  #(1,9)(9,18)     #Z_row = X_row @ K_col
        dK = dK_col.reshape(self.K.shape)
        db = np.sum(dZ,axis=(0,2,3))
        db = db.reshape(-1,F)
        # (N*H*W, C)
        dX = dX_row.reshape(N,self.H,self.W,self.C)
        dX = dX.transpose(0,3,1,2)
        self.grads[0] += dK
        self.grads[1] += db
        return dX

    #-------- add the gradient of the regular term ---
    def reg_grad(self,reg):
        self.grads[0]+= 2*reg * self.K

    def reg_loss(self,reg):
        return  reg*np.sum(self.K**2)

    def reg_loss_grad(self,reg):
        self.grads[0]+= 2*reg * self.K
        return  reg*np.sum(self.K**2)
```

**注意**：有时人们会使用卷积操作来模拟转置卷积的计算过程，但这种模拟过程不仅复杂，而且计算量大，因此没有实际意义。感兴趣的读者可参考以下网址：

[http://deeplearning.net/software/theano/tutorial/conv_arithmetic.html](http://deeplearning.net/software/theano/tutorial/conv_arithmetic.html)

### 8.8.3 卷积生成对抗网络 DCGAN 的实现

借助转置卷积，可将低维隐向量转换为高分辨率图像。因此，卷积对抗网络的生成器可用带有转置卷积层的神经网络表示，而判别器可用普通卷积神经网络表示。这种对抗生成网络即为卷积生成对抗网络（DCGAN）。接下来，使用该 DCGAN 网络训练 Mnist 手写数字集，使生成器能从隐向量输出类似于训练集中手写数字图像的图像。

首先，仍将 Mnist 手写数字集读取为训练样本：

```
import data_set as ds
import matplotlib.pyplot as plt
%matplotlib inline
train_set, valid_set, test_set = ds.read_mnist()
train_X, train_y = train_set
valid_X, valid_y = valid_set
test_X, test_y = valid_set
print(train_X.dtype)
print(train_X.shape)
print(train_y.dtype)
print(train_y.shape)
ds.draw_mnists(plt,train_X,range(10))
plt.show()
train_X = train_X.reshape(train_X.shape[0],1,28,28)
print(train_X.shape)
```

```
float32
(50000, 784)
int64
(50000,)
```

![](EPUB/media/file201.png "fig:")
(50000, 1, 28, 28)

然后使用转置卷积类、卷积类及其他网络层类，分别定义代表生成器和判别器的神经网络 `G` 和 `D`：

```
from util import *
from NeuralNetwork import *
from GAN import *
np.random.seed(100)
random_name = 'no'
random_value =  0.01
G = NeuralNetwork()
z_dim = 100
ngf=28
ndf=28
nc=1
G.add_layer(Conv_transpose(z_dim, ngf*4,4,1,0))   # ->(ngf*4) x 4 x 4
G.add_layer(BatchNorm(ngf*4))
G.add_layer(Relu()) #Leaky_relu(0.2))
```
