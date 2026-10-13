
Taking this view, it is easy to see why, when adding more layers, the training error should not increase. In the worst case, when all information has been extracted up to a layer *r*, we expect that adding an extra layer should implement the identity mapping, i.e., **y**^(*r*) = *H*(**y**^(*r*−1)) = **y**^(*r*−1). That is, the extra layer adds no information and simply copies the input to the output. However, it seems that once the network starts becoming very deep, accuracy gets “saturated” and the optimization tools have difficulty to come up with an accurate enough solution to this identity mapping, at least within a feasible time.

![Figure 18.32 When a network is very deep, it turns out that the training error starts increasing when the number of layers exceeds some number, instead of being decreased (red curve) as expected from theory.](images/B978044329238500024X/gr032.jpg)

**Figure 18.32** When a network is very deep, it turns out that the training error starts increasing when the number of layers exceeds some number, instead of being decreased (red curve) as expected from theory.

One way to bypass this difficulty is proposed in [67]. The idea is to fit an alternative equivalent mapping, i.e.,

*F*(**y**^(*r*−1)) = *H*(**y**^(*r*−1)) − **y**^(*r*−1).

Then the original mapping, *H*(**y**^(*r*−1)), becomes equal to *F*(**y**^(*r*−1)) + **y**^(*r*−1). In practice, it turns out that optimizing with respect to the residual mapping, *F*, is easier than optimizing with respect to the original one, *H*. In the extreme case, when an identity mapping should be realized, it seems that it is easier to push the residual to zero than fitting the identity one.

The use of residual representation is not new and has been used before in the context of vector quantization. The essence of the residual learning is to introduce the so-called *residual* building block, shown in **Figure 18.33**. In this way, a number of layers, say, two, as in the case of the figure, are stacked together, and we *explicitly* let these layers fit the residual mapping, via the so-called shortcut or skip connections. Each weight layer performs a transformation over its input, e.g., convolutions. If **y**^(*r*) and **y**^(*r*−1) are of different dimension, then the identity mapping shortcut is modified to *W***y**^(*r*−1), where *W* is a matrix of appropriate dimensions.

![Figure 18.33 Two successive layers in a network have been combined and their implied combined transformation is performed via the identity mapping, implemented by the red line shortcut/skip connection.](images/B978044329238500024X/gr033.jpg)

**Figure 18.33** Two successive layers in a network have been combined and their implied combined transformation is performed via the identity mapping, implemented by the red line shortcut/skip connection.

**Figure 18.34**A shows a schematic example of a so-called plain network (no residuals involved) that comprises a sequence of convolutional layers. Its residual counterpart is shown in **Figure 18.34**B. Note that if the identity shortcut is used, then no extra parameters are involved and training follows the standard backpropagation rationale. A variant of the residual network, known as *highway* network, has been proposed (e.g., [60,184]), where extra data dependent gating functions that control the flow in the shortcuts have been introduced.

![Figure 18.34 (A) The layout of a plain network and (B) the corresponding layout with the use of shortcuts.](images/B978044329238500024X/gr034.jpg)

**Figure 18.34** (A) The layout of a plain network and (B) the corresponding layout with the use of shortcuts.

In [67], networks as deep as 50 to 152 layers have been constructed. In spite of such sizes, it is reported that the overall number of arithmetic operations remains substantially lower than that required by VGG-16, at an improved performance in error rates. In [202], the concept of residual networks is combined with that of the inception networks. It is reported that training with residual connections can accelerate the training of inception networks significantly.
