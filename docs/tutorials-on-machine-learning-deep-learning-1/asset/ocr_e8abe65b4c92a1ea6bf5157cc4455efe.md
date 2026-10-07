![](bbox=[0.105, 0.023, 0.895, 0.345])

Let's have a look at some other cases. We don't go to the details.

![](bbox=[0.105, 0.415, 0.895, 0.585])

> How the values inside hidden nodes changes from "1" to "-1".

You can see, in our data set, we've got rows with three 0s and 4 nodes. We can encode them into a small format which we just have 2 hidden nodes.

![](bbox=[0.105, 0.608, 0.895, 0.765])

+   - Every state, is represented by a layer using hidden nodes {1, 0} or {1, -1} or {-1, 0} or {-1, -1}.\ Then you just need these weights and Softmax to reconstruct your output.

+   - It is a very simplified example, but this gives an overview of Auto Encoders. Of course Auto Encoder are more complex than that.

+   - Additional reading: For additional reading this is the same blog we already mentioned it's called, "Neural Networks Are Impressively Good At Compression" by Malte Skarupe and will include it in the additional resources.
- Newly written very early introduction to Auto Encoders. Here you can use a much more sophisticated example.