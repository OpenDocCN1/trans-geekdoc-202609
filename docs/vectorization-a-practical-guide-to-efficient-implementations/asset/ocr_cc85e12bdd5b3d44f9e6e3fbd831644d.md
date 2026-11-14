```
100%|| 469/469 [00:13<00:00, 33.88it/s]
100%|| 79/79 [00:01<00:00, 50.92it/s]
Epoch 10/10: train_loss - 0.46, eval_loss - 0.43, eval_acc - 0.87
```

# ## 9.4 Bucketizing Values

Suppose we have a continuous variable in a given range, and we would like to
divide the range into several smaller index ranges, which we call buckets (a.k.a bins) so
that we could assign an integer index to indicate which bucket each value falls into.
This is called **Binning** or **Bucketization**. Hence, the continuous variable
becomes a categorical or ordinal variable. For example, given the continuous feature,
\(x = [0, 1, 2, 3, 4, 5, 6, 7, 8]\), we would like to assign integer values according to
the following range buckets:

```
\( x \in \left\{ \begin{aligned} [0, 3) \rightarrow 0 \\ [3, 6) \rightarrow 1 \\ [6, 9) \rightarrow 2 \end{aligned} \right. \)
```

Then, the bucketized values are indices = [0, 0, 0, 1, 1, 1, 2, 2, 2].

There are several ways we can bucketize values using vectorization. NumPy’s
`np.digitize`, Tensorflow’s `tf.raw_ops.Bucketize`, and PyTorch’s
`torch.bucketize` conveniently serve this purpose, though the default
formulation of these libraries can be different. Given a list of continuous values
and the buckets specified as a monotonically increasing list [_b_<sub>0</sub>, _b_<sub>1</sub>, _b_<sub>2</sub>,
_b_<sub>3</sub>, ..., _b_<sub>_N_</sub>], where \( b_0 < b_1 < b_2 < \cdots < b_N \), and the buckets are arranged as
\( (-\infty, b_0), [b_0, b_1), [b_1, b_2) \dots, [b_{N-1}, b_N), [b_N, +\infty) \) (i.e. left inclusive, right exclusive,
or \( b_{i-1} \le x < b_i \) for the _i_th bucket). This totals _N_ + 2 buckets since these
functions add two special buckets that account for values beyond the specified
range. Let us denote this as the “left-inclusive” formulation. Alternatively, the
buckets can also be formulated as \( (-\infty, b_0], (b_0, b_1], \dots, (b_{N-1}, b_N], (b_N, +\infty) \)
(i.e. left exclusive, right inclusive, or \( b_{i-1} < x \le b_i \) for the _i_th bucket). Let
us call this the “left-exclusive” formulation. Interestingly, `np.digitize`
(numpy==1.26.1) uses the “left-inclusive” formulation when it is called with
the default `right=False` setting, while setting `right=True` switches it to
use the “left-exclusive” formulation; Tensorflow’s `tf.raw_ops.Bucketize`
also uses and can only use “left-inclusive” formulation. Interestingly, the default
behavior of `torch.bucketize` is the opposite of the default behavior of
`np.digitize`. `torch.bucketize` uses “left-exclusive” formulation by
default when setting `right=False`, while setting `right=True` switches its
behavior to “left-inclusive.”