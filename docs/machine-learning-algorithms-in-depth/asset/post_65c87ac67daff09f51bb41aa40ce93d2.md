
```python
from sklearn.datasets import make_blobs
from sklearn.metrics import adjusted_rand_score
from sklearn.metrics import normalized_mutual_info_score
from sklearn.model_selection import train_test_split

import math
import matplotlib.pyplot as plt
import matplotlib.cm as cm

tf.keras.utils.set_random_seed(42)

SAVE_PATH = "/content/drive/MyDrive/Colab Notebooks/data/"

def scheduler(epoch, lr):
    if epoch < 4:
        return lr
    else:
        return lr * tf.math.exp(-0.1)

def generate_data(N):
    pi = np.array([0.2, 0.4, 0.3, 0.1])
    mu = [[2,2], [-2,2], [-2,-2], [2,-2]]
    std = [[0.5,0.5], [1.0,1.0], [0.5,0.5], [1.0,1.0]]
    x = np.zeros((N,2), dtype=np.float32)
    y = np.zeros((N,2), dtype=np.float32)
    z = np.zeros((N,1), dtype=np.int32)
    for n in range(N):
        k = np.argmax(np.random.multinomial(1, pi))
        x[n,:] = np.random.multivariate_normal(mu[k], np.diag(std[k]))
        y[n,:] = mu[k]
        z[n,:] = k
    #end for
    z = z.flatten()
    return x, y, z, pi, mu, std

def tf_normal(y, mu, sigma):
    y_tile = K.stack([y]*num_clusters, axis=1) #[batch_size, K, D]
    result = y_tile - mu
    sigma_tile = K.stack([sigma]*data_dim, axis=-1) #[batch_size, K, D]
    result = result * 1.0/(sigma_tile+1e-8)
    result = -K.square(result)/2.0
    oneDivSqrtTwoPI = 1.0/math.sqrt(2*math.pi)
    result = K.exp(result) * (1.0/(sigma_tile + 1e-8))*oneDivSqrtTwoPI
    result = K.prod(result, axis=-1)   #[batch_size, K] iid Gaussians
    return result

def NLLLoss(y_true, y_pred):
    out_mu = y_pred[:,:num_clusters*data_dim]
    out_sigma = y_pred[:,num_clusters*data_dim : num_clusters*(data_dim+1)]
    out_pi = y_pred[:,num_clusters*(data_dim+1):]

    out_mu = K.reshape(out_mu, [-1, num_clusters, data_dim])

    result = tf_normal(y_true, out_mu, out_sigma)
    result = result * out_pi
    result = K.sum(result, axis=1, keepdims=True)
    result = -K.log(result + 1e-8)
    result = K.mean(result)
    return tf.maximum(result, 0)

#generate data
X_data, Y_data, z_data, pi_true, mu_true, sigma_true = generate_data(4096)

data_dim = X_data.shape[1]
num_clusters = len(mu_true)

num_train = 3500
X_train, X_test, Y_train, Y_test = X_data[:num_train,:], \
    X_data[num_train:,:], Y_data[:num_train,:], Y_data[num_train:,:]
z_train, z_test = z_data[:num_train], z_data[num_train:]

#visualize data
plt.figure()
plt.scatter(X_train[:,0], X_train[:,1], c=z_train, cmap=cm.bwr)
plt.title('training data')
plt.show()
#plt.savefig(SAVE_PATH + '/mdn_training_data.png')

batch_size = 128
num_epochs = 128

hidden_size = 32
weight_decay = 1e-4

#MDN architecture
input_data = Input(shape=(data_dim,))
x = Dense(32, activation='relu')(input_data)
x = Dropout(0.2)(x)
x = BatchNormalization()(x)
x = Dense(32, activation='relu')(x)
x = Dropout(0.2)(x)
x = BatchNormalization()(x)

mu = Dense(num_clusters * data_dim, activation='linear')(x)
sigma = Dense(num_clusters, activation=K.exp)(x)
pi = Dense(num_clusters, activation='softmax')(x)
out = concatenate([mu, sigma, pi], axis=-1)

model = Model(input_data, out)

model.compile(
    loss=NLLLoss,
    optimizer=tf.keras.optimizers.Adam(),
    metrics=["accuracy"]
)

model.summary()

#define callbacks
file_name = SAVE_PATH + 'mdn-weights-checkpoint.h5'
checkpoint = ModelCheckpoint(file_name, monitor='val_loss', verbose=1,
    save_best_only=True, mode='min')
reduce_lr = LearningRateScheduler(scheduler, verbose=1)
early_stopping = EarlyStopping(monitor='val_loss', min_delta=0.01,
    patience=16, verbose=1)
#tensor_board = TensorBoard(log_dir='./logs', write_graph=True)
callbacks_list = [checkpoint, reduce_lr, early_stopping]

hist = model.fit(X_train, Y_train, batch_size
    =batch_size, epochs=num_epochs, callbacks
    =callbacks_list, validation_split=0.2,
    shuffle=True, verbose=2)

Y_pred = model.predict(X_test)

mu_pred = Y_pred[:,:num_clusters*data_dim]
mu_pred = np.reshape(mu_pred, [-1, num_clusters, data_dim])
sigma_pred = Y_pred[:,num_clusters*data_dim : num_clusters*(data_dim+1)]
pi_pred = Y_pred[:,num_clusters*(data_dim+1):]
z_pred = np.argmax(pi_pred, axis=-1)

rand_score = adjusted_rand_score(z_test, z_pred)
print("adjusted rand score: ", rand_score)

nmi_score = normalized_mutual_info_score(z_test, z_pred)
print("normalized MI score: ", nmi_score)

mu_pred_list = []
sigma_pred_list = []
for label in np.unique(z_pred):
    z_idx = np.where(z_pred == label)[0]
    mu_pred_lbl = np.mean(mu_pred[z_idx,label,:], axis=0)
    mu_pred_list.append(mu_pred_lbl)

    sigma_pred_lbl = np.mean(sigma_pred[z_idx,label], axis=0)
    sigma_pred_list.append(sigma_pred_lbl)
#end for

print("true means:")
print(np.array(mu_true))

print("predicted means:")
print(np.array(mu_pred_list))

print("true sigmas:")
print(np.array(sigma_true))

print("predicted sigmas:")
print(np.array(sigma_pred_list))

#generate plots
plt.figure()
plt.scatter(X_test[:,0], X_test[:,1], c=z_pred, cmap=cm.bwr)
plt.scatter(np.array(mu_pred_list)[:,0], np.array(mu_pred_list)[:,1],
            s=100, marker='x', lw=4.0, color='k')
plt.title('test data')

plt.figure()
plt.plot(hist.history['loss'], 'b-', lw=2.0, label='train')
plt.plot(hist.history['val_loss'], '--r', lw=2.0, label='val')
plt.title('Mixture Density Network')
plt.xlabel('Epochs')
plt.ylabel('Negative Log Likelihood Loss')
plt.legend(loc='upper left')
```

Learning rate schedule

Synthetic ground truth data

Isotropic multivariate Gaussian

Negative log likelihood loss

Training params

Model params

Cluster means

Diagonal covariance

Mixture proportions

![](img/325742126d3ff007c6c385f4ffb5c3be_284_0.png)

![](img/325742126d3ff007c6c385f4ffb5c3be_285_0.png)

Figure 11.8 shows the cluster centroids overlayed with test data in addition to training and validation loss.

Figure 11.8  Mixture density network: cluster centroids and training and validation loss

We can see that inferred means are close to cluster centers. It’s interesting to note that for this initialization, two of the cluster means coincide. Feel free to experiment with different seeds and numbers of training points to understand the behavior of the model. Also, we find that both training and validation loss are decreasing with the number of epochs. In the following section, we will look at a powerful transformer architecture based on self-supervised learning.

## 11.3 Attention and transformers

Attention allows a model to adaptively pay attention to different parts of the input by adjusting attention weights. Attention mechanisms can be applied to many kinds of neural networks but were first used in the context of recurrent neural networks (RNNs). In Seq2Seq neural models, such as those used in machine translation, the output context vector that summarizes the input sentence does not have access to individual input words. This results in poor performance, as measured by the BLEU score. We can avoid this bottleneck by letting the output attend to input words directly, in a weighted fashion. In other words, we can compute the context vector as a weighted sum of input word vectors h^enc_s.

$$c_t = \sum_s a_{ts}h_s^{enc} \tag{11.10}$$

Here, $a_{ts}$ are learned attention weights given by the following.

$$a_{ts} = \frac{\exp\{\operatorname{score}(h_{t-1}^{dec}, h_s^{enc})\}}{\sum_{s'} \exp\{\operatorname{score}(h_{t-1}^{dec}, h_{s'}^{enc})\}} \tag{11.11}$$

There are several ways to learn the scoring function (e.g., the multiplicative style).

$$\operatorname{score}(a,b) = a^T W b \tag{11.12}$$

Here, $W$ is an intermediate trainable matrix. We can generalize attention as a soft dictionary lookup. A soft dictionary lookup refers to a type of search in which an exact match is not found. This is useful when searching for words that may have been misspelled or are related to the search term. We can think of attention as comparing a set of target vectors or queries $q_i$ with a set of candidate vectors or keys $k_j$. For each query, we compute how much the query is related to every key and then use these scores to weigh and sum the values $v_j$ associated with every key. Thus, we can define the attention matrix $A$ as follows.

$$A_{ij} = \operatorname{score}(q_i,k_j) \tag{11.13}$$

Given the attention weights in $A_{ij}$, we compute a weighted combination of values $v_j$ associated with each key. As a result, for the $i$-th query, we have the following.

$$r_i = \sum_j A_{ij}v_j = \sum_j \operatorname{score}(q_i,k_j)v_j \tag{11.14}$$

Here, we can choose a normalized multiplicative score with $W=1$.

$$\operatorname{score}(q_i,k_j) = \frac{q_i^T k_j}{\sqrt{D}} \tag{11.15}$$

In matrix notation, where we have $N$ queries ($Q$ of size $N\times D$) and $N$ key–value pairs ($K$ of size $N\times D$), we can write down the result (weighted set of values $V$, whose keys $K$ most resemble the query $Q$).

$$\begin{aligned} R &= \operatorname{attention}(Q,K,V)=AV \\ &= \operatorname{score}(Q,K)V = \operatorname{softmax}\left(\frac{QK^T}{\sqrt{D}}\right)V \end{aligned} \tag{11.16}$$
