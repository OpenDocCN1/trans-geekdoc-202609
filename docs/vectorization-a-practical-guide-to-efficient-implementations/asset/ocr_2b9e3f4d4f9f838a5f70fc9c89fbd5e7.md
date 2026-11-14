lookup, then apply the weights along the first two dimensions (batch and sequence), and finally pool the sequence dimension with summation.

Again, we can test our implementation with some faked inputs. Notice that comparing Keras, items are using 1-based indexing, with 0 as paddings. Both items and weights are dense tensors of the same shape.

```
```
inputs = {
    "items": torch.tensor([[2, 3, 0], [4, 1, 5]]),
    "weights": torch.tensor([[[1.3, 2.7, 0.0], [2.1, 4.6, 0.8]]]),
}
model = Autoencoder(num_items=1000, emb_size=128)
z = model(**inputs)
```
```

Printing the model with `print(model)` gives us

```
```
Autoencoder(
    (embed): Embedding(1000, 128, padding_idx=0)
    (decoder): Sequential(
        (0): ReLU()
        (1): Linear(in_features=128, out_features=1000, bias=True)
        (2): Sigmoid()
    )
)
```
```

# Bibliography

Martn Abadi, Ashish Agarwal, Paul Barham, Eugene Brevdo, Zhifeng Chen, Craig Citro, Greg S. Corrado, Andy Davis, Jeffrey Dean, Matthieu Devin, Sanjay Ghemawat, Ian Goodfellow, Andrew Harp, Geoffrey Irving, Michael Isard, Yangqing Jia, Rafal Jozefowicz, Lukasz Kaiser, Manjunath Kudlur, Josh Levenberg, Dan Mané, Rajat Monga, Sherry Moore, Derek Murray, Chris Olah, Mike Schuster, Jonathon Shlens, Benoit Steiner, Ilya Sutskever, Kunal Talwar, Paul Tucker, Vincent Vanhoucke, Vijay Vasudevan, Fernanda Viegas, Oriol Vinyals, Pete Warden, Martin Wattenberg, Martin Wicke, Yuan Yu, and Xiaoqiang Zheng. Tensorflow RaggedTensor. https://www.tensorflow.org/api_docs/python/tf/RaggedTensor, 2023.

Denis Baylor, Eric Breck, Heng-Tze Cheng, Noah Fiedel, Chuan Yu Foo, Zakaria Haque, Salem Haykal, Mustafa Ispir, Vihan Jain, Levent Koc, Chiu Yuen Koo, Lukasz Lew, Clemens Mewald, Akshay Naresh Modi, Neoklis Polyzotis, Sukriti Ramesh, Sudip Roy, Steven Euijong Whang, Martin Wicke, Jarek Wilkiewicz, Xin Zhang, and Martin Zinkevich. Tensorflow Transform Sparse Left Align. https:////