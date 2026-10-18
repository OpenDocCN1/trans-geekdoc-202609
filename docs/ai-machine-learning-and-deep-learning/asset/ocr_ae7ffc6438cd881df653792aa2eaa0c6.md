![](bbox=[0.1, 0.08, 0.82, 0.52])

FIGURE 12.2 Data-centric federated learning.

# 12.3.1.1 Model-centric Federated Learning

This the more common of the two types [10]. In model-centric, the model is hosted in a cloud service, and its API is preconfigured (layers, weight, etc.). Each individual downloads the model, enhances it, and uploads a newer version. But this could happen over a long period of time, frequently weeks and months. A great example is Google’s GBoard mobile app. It learns users’ typing preferences over time without sending any private data. The learning is distributed and happens remotely, updating a central model through a suitable federation technique.

# 12.3.1.2 Data-centric Federated Learning

Less common than model-centric but more suitable for experimentation science, data-centric is hosted inside a cloud server not as a model but as a