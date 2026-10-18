
# 代码实现

```python
return pool_out

def init_filter(shape, poolsz):
    w = np.random.randn(*shape) / np.sqrt(np.prod(shape[:-1]) + shape[-1]*np.prod(shape[:-2] / np.prod(poolsz)))
    return w.astype(np.float32)

def rearrange(X):
    # input is (32, 32, 3, N)
    # output is (N, 32, 32, 3)
    N = X.shape[-1]
    out = np.zeros((N, 32, 32, 3), dtype=np.float32)
    for i in xrange(N):
        for j in xrange(3):
            out[i, :, :, j] = X[:, :, j, i]
    return out / 255

def main():
    train = loadmat('../large_files/train_32x32.mat') # N = 73257
    test = loadmat('../large_files/test_32x32.mat') # N = 26032
    # Need to scale! don't leave as 0..255
    # Y is a N x 1 matrix with values 1..10 (MATLAB indexes by 1)
    # So flatten it and make it 0..9
    # Also need indicator matrix for cost calculation
    Xtrain = rearrange(train['X'])
    Ytrain = train['y'].flatten() - 1
    print len(Ytrain)
    del train
    Xtrain, Ytrain = shuffle(Xtrain, Ytrain)
    Ytrain_ind = y2indicator(Ytrain)
    Xtest = rearrange(test['X'])
    Ytest = test['y'].flatten() - 1
    del test
    Ytest_ind = y2indicator(Ytest)
    # gradient descent params
    max_iter = 20
    print_period = 10
    N = Xtrain.shape[0]
    batch_sz = 500
    n_batches = N / batch_sz
    # limit samples since input will always have to be same size
    # you could also just do N = N / batch_sz * batch_sz
    Xtrain = Xtrain[:73000,]
    Ytrain = Ytrain[:73000]
    Xtest = Xtest[:26000,]
    Ytest = Ytest[:26000]
    Ytest_ind = Ytest_ind[:26000,]
    # initialize weights
    M = 500
    K = 10
    poolsz = (2, 2)
    W1_shape = (5, 5, 3, 20) # (filter_width, filter_height, num_color_channels, num_feature_maps)
    W1_init = init_filter(W1_shape, poolsz)
    b1_init = np.zeros(W1_shape[-1], dtype=np.float32) # one bias per output feature map
    W2_shape = (5, 5, 20, 50) # (filter_width, filter_height, old_num_feature_maps, num_feature_maps)
    W2_init = init_filter(W2_shape, poolsz)
    b2_init = np.zeros(W2_shape[-1], dtype=np.float32)
    # vanilla ANN weights
    W3_init = np.random.randn(W2_shape[-1]*8*8, M) / np.sqrt(W2_shape[-1]*8*8 + M)
    b3_init = np.zeros(M, dtype=np.float32)
    W4_init = np.random.randn(M, K) / np.sqrt(M + K)
    b4_init = np.zeros(K, dtype=np.float32)
    # define variables and expressions
    # using None as the first shape element takes up too much RAM unfortunately
    X = tf.placeholder(tf.float32, shape=(batch_sz, 32, 32, 3), name='X')
    T = tf.placeholder(tf.float32, shape=(batch_sz, K), name='T')
    W1 = tf.Variable(W1_init.astype(np.float32))
    b1 = tf.Variable(b1_init.astype(np.float32))
    W2 = tf.Variable(W2_init.astype(np.float32))
    b2 = tf.Variable(b2_init.astype(np.float32))
    W3 = tf.Variable(W3_init.astype(np.float32))
    b3 = tf.Variable(b3_init.astype(np.float32))
    W4 = tf.Variable(W4_init.astype(np.float32))
    b4 = tf.Variable(b4_init.astype(np.float32))
    Z1 = convpool(X, W1, b1)
    Z2 = convpool(Z1, W2, b2)
    Z2_shape = Z2.get_shape().as_list()
    Z2r = tf.reshape(Z2, [Z2_shape[0], np.prod(Z2_shape[1:])])
    Z3 = tf.nn.relu( tf.matmul(Z2r, W3) + b3 )
    Yish = tf.matmul(Z3, W4) + b4
    cost = tf.reduce_sum(tf.nn.softmax_cross_entropy_with_logits(Yish, T))
    train_op = tf.train.RMSPropOptimizer(0.0001, decay=0.99, momentum=0.9).minimize(cost)
    # we'll use this to calculate the error rate
    predict_op = tf.argmax(Yish, 1)
    t0 = datetime.now()
    LL = []
    init = tf.initialize_all_variables()
    with tf.Session() as session:
        session.run(init)
        for i in xrange(max_iter):
            for j in xrange(n_batches):
                Xbatch = Xtrain[j*batch_sz:(j*batch_sz + batch_sz),]
                Ybatch = Ytrain_ind[j*batch_sz:(j*batch_sz + batch_sz),]
                if len(Xbatch) == batch_sz:
                    session.run(train_op, feed_dict={X: Xbatch, T: Ybatch})
                if j % print_period == 0:
                    # due to RAM limitations we need to have a fixed size input
                    # so as a result, we have this ugly total cost and prediction computation
                    test_cost = 0
                    prediction = np.zeros(len(Xtest))
                    for k in xrange(len(Xtest) / batch_sz):
                        Xtestbatch = Xtest[k*batch_sz:(k*batch_sz + batch_sz),]
                        Ytestbatch = Ytest_ind[k*batch_sz:(k*batch_sz + batch_sz),]
                        test_cost += session.run(cost, feed_dict={X: Xtestbatch, T: Ytestbatch})
                        prediction[k*batch_sz:(k*batch_sz + batch_sz)] = session.run(
                            predict_op, feed_dict={X: Xtestbatch})
                    err = error_rate(prediction, Ytest)
                    print "Cost / err at iteration i=%d, j=%d: %.3f / %.3f" % (i, j, test_cost, err)
                    LL.append(test_cost)
        print "Elapsed time:", (datetime.now() - t0)
        plt.plot(LL)
        plt.show()

if __name__ == '__main__':
    main()
```

# Conclusion

I really hope you had as much fun reading this book as I did making it.

Did you find anything confusing? Do you have any questions?

I am always available to help. Just email me at: [info@lazyprogrammer.me](mailto:info@lazyprogrammer.me)

Do you want to learn more about deep learning? Perhaps online courses are more your style. I happen to have a few of them on Udemy.

A lot of the material in this book is covered in this course, but you get to see me derive the formulas and write the code live:

[Deep Learning: Convolutional Neural Networks in Python](https://www.udemy.com/deep-learning-convolutional-neural-networks-theano-tensorflow)

[https://www.udemy.com/deep-learning-convolutional-neural-networks-theano-tensorflow](https://www.udemy.com/deep-learning-convolutional-neural-networks-theano-tensorflow)

The background and prerequisite knowledge for deep learning and neural networks can be found in my class “Data Science: Deep Learning in Python” (officially known as “part 1” of the series). In this course I teach you the feedforward mechanism of a neural network (which I assumed you already knew for this book), and how to derive the training algorithm called backpropagation (which I also assumed you knew for this book):

[Data Science: Deep Learning in Python](https://udemy.com/data-science-deep-learning-in-python)

[https://udemy.com/data-science-deep-learning-in-python](https://udemy.com/data-science-deep-learning-in-python)

The corresponding book on Kindle is:

[https://kdp.amazon.com/amazon-dp-action/us/bookshelf.marketplacelink/B01CVJ19E8](https://kdp.amazon.com/amazon-dp-action/us/bookshelf.marketplacelink/B01CVJ19E8)

Are you comfortable with this material, and you want to take your deep learning skillset to the next level? Then my follow-up Udemy course on deep learning is for you. Similar to previous book, I take you through the basics of Theano and TensorFlow - creating functions, variables, and expressions, and build up neural networks from scratch. I teach you about ways to accelerate the learning process, including batch gradient descent, momentum, and adaptive learning rates. I also show you live how to create a GPU instance on Amazon AWS EC2, and prove to you that training a neural network with GPU optimization can be orders of magnitude faster than on your CPU.

[Data Science: Practical Deep Learning in Theano and TensorFlow](https://www.udemy.com/data-science-deep-learning-in-theano-tensorflow/)

[https://www.udemy.com/data-science-deep-learning-in-theano-tensorflow](https://www.udemy.com/data-science-deep-learning-in-theano-tensorflow)

In part 4 of my deep learning series, I take you through unsupervised deep learning methods. We study principal components analysis (PCA), t-SNE (jointly developed by the godfather of deep learning, Geoffrey Hinton), deep autoencoders, and restricted Boltzmann machines (RBMs). I demonstrate how unsupervised pretraining on a deep network with autoencoders and RBMs can improve supervised learning performance.

[Unsupervised Deep Learning in Python](https://www.udemy.com/unsupervised-deep-learning-in-python)

[https://www.udemy.com/unsupervised-deep-learning-in-python](https://www.udemy.com/unsupervised-deep-learning-in-python)
