# 2.2.3 How LSTM works

So we've got the inside-look of our simple-Standard-RNN. And this is the problem lines.
This operation that happens here is a neural-network-layer-operation.
In a simple word: outputs coming into this module and this operation's applied and then goes into the next module operation's applied, and so on.
When we back propagate, it goes through all of those operation, and that's where the weights are applied (that's where W_rec is sitting). And through this back propagation, the gradient vanishes, which means that the weights cannot be updated properly or fast enough to train the network properly. This is the standard RNN.

Now Following image is the LSTM version of RNN.

![](bbox=[0.398, 0.303, 0.864, 0.497])

Notice the main point here was setting W_rec = 1. Well that's this line flows straight here (the upper line), that pipeline at the top of the LSTM version of RNN.

![](bbox=[0.398, 0.545, 0.834, 0.574])

There's not much going on, just two pointwise operations (removal & addition) and no Complex Neural Network Layered Operations happening in this line.

![](bbox=[0.368, 0.637, 0.808, 0.762])

Actually LSTMs have this pipeline as a memory cell or call it memory pipeline. This pipeline flows through time, sometimes it faces pointwise operations to remove/add something.
But mostly it flows through times freely and therefore when you back propagate through these LSTMs, you don't face vanishing gradient problem.

However, all complex-operations are brought out to this down part (image on the Right).

![](bbox=[0.638, 0.873, 0.864, 0.946])