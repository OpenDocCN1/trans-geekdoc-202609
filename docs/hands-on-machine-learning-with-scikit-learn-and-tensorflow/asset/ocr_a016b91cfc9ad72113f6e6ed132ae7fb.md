Simply projecting onto a plane (e.g., dropping x_j) would squash different layers of the Swiss roll together, as shown on the left of Figure 8-5. However, what you really want is to unroll the Swiss roll to obtain the 2D dataset on the right of Figure 8-5.

![](bbox=[0.142, 0.159, 0.857, 0.335])

Figure 8-5. Squashing by projecting onto a plane (left) unrolling the Swiss roll (right)

# Manifold Learning

The Swiss roll is an example of a 2D manifold. Put simply, a 2D manifold is a shape that can be bent and twisted in a higher-dimensional space. More generally, a d-dimensional manifold is part of an n-dimensional space (where d < n) that locally resembles a d-dimensional hyperplane. In the case of the Swiss roll, d=2 and n=3: it locally resembles a 2D plane, but it is rolled in the third dimension.

Many dimensionality reduction algorithms work by modeling the manifold on which the training instances lie; this is called Manifold Learning. It relies on the manifold assumption, also the manifold hypothesis, which holds that most real-world high-dimensional datasets lie close to a much lower-dimensional manifold. This assumption is very empirically observed.

Once again, think about the MNIST dataset: all handwritten digit images have some similarities. They are made of connected lines, the borders are white, they more or less centered, and so on. If you randomly generated images, a ridiculously fraction of them would look like handwritten digits. In other words, the degrees of freedom available to you if you try to create a digit image are dramatically lower than the degrees of freedom you would have if you were allowed to generate any image you wanted. These constraints then squeeze the dataset into a lower-dimensional manifold.

The manifold assumption is often accompanied by another implicit assumption: that the task at hand (e.g., classification or regression) will be simpler if expressed in the lower-dimensional space of the manifold. For example, in the top row of Figure 8-6 the Swiss roll is split into two spaces: in the 3D space (on the left), the decision-