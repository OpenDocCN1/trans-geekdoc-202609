
`X_row = X.transpose(0,2,3,1).reshape(-1,F)`

Then according to the reverse derivation formula, the flattened matrix `Z_row` of the output of this transposed convolution can be calculated, namely:

```
Z_row = np.dot(X_row,K_col.T)
```

Finally, according to the reverse derivation process of the convolution, the distribution of each row of this `Z_row` must be accumulated to the final output `Z`. This process can directly use the `row2im()` function or `row2im_indices()` function completes:

```
Z = row2im_indices(Z_row,Z_shape,self.kH,self.kW,S =self.S,P = self.P)
```

Similarly, the reverse derivation of the transposed convolution is similar to the forward calculation process of the convolution. First, the gradient `dz` of the loss function with respect to `Z` must be flattened by the `im2row()` or `im2row_indices()` function Matrix `dZ_row`, each row of which represents a data block, and then calculates the gradient of the input `X` of the transposed convolution:

```
dX_row = dZ_row @ K_col
```

You can get the flattened matrix `dX_row` about the gradient of `X`, and finally reshape this flattened matrix into a four-dimensional tensor with the same shape as `X`, namely:

```
dX = dX_row.reshape(N,self.H,self.W,self.C)
dX = dX.transpose(0,3,1,2)
```

Similarly, the calculation process of the gradient `dK_col` for model `K` is similar, and it is more straightforward to reshape the shape of the flattened matrix `dK_col` into the same shape as `K`:

```
dK_col = self.X_row.T@dZ_row
dK = dK_col.reshape(self.K.shape)
```

According to the above analysis, the following transposed convolution class `Conv_transpose` can be written:

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

**Note**: People sometimes use convolution operation to simulate the calculation process of transposed convolution, but this simulation process is not only complicated but also has a large amount of calculation, so it has no practical significance. Interested readers can refer to the following URL:

[http://deeplearning.net/software/theano/tutorial/conv_arithmetic.html](http://deeplearning.net/software/theano/tutorial/conv_arithmetic.html)

### 8.8.3 Implementation of convolutional confrontation network DCGAN

With the help of transposed convolution, a low-dimensional hidden vector can be transformed into a high-resolution image. Therefore, the generator of a convolutional adversarial network can be represented by a neural network with transposed convolutional layers, while the discriminator can be represented by a normal convolutional neural network. Such an adversarial generative network is a convolutional adversarial network (DCGAN). Next, use this DCGAN network to train the Mnist handwritten digit set, so that the generator can output an image similar to the handwritten digit image in the training set from a hidden vector.

First, still read the Mnist handwritten digit set as a training sample:

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

Then use the transposed convolution class and the convolution class and other network layer classes to define the neural networks `G` and `D` representing the generator and discriminator respectively:

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
