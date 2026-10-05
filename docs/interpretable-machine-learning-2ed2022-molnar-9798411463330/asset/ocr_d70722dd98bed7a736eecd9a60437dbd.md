# 9.1 LEARNED FEATURES

+   - The largest number of unique concept detectors is learned for Places356, followed by Places205 and ImageNet last.

+   - The number of unique concept detectors increases with the number of training iterations.

+   - Networks trained on self-supervised tasks have fewer unique detectors compared to networks trained on self-supervised tasks.

+   - In transfer learning, the concept of a channel can change. For example, a dog detector became a waterfall detector. This happened in a model that was initially trained to classify objects and fine-tuned to classify scenes.
- In one of the experiments, the authors projected the channels onto a rotated basis. This was done for the VGG network—"Rotated" does not mean the image was rotated. "Rotated" means we take the 256 channels from the conv5 layer and compute 256 new channels as linear combinations of the original channels. In the process, the channels get entangled. Rotation reduces interpretability, the number of channels aligned with a concept decreases. The rotation was designed to keep the performance of the model the same. The first conclusion: Interpretability of CNNs is axis-dependent. This means that random combinations of channels are less likely to detect unique concepts. The second conclusion: Interpretability is independent of discriminative power. The channels can be transformed with orthogonal transformations while the discriminative power remains the same, but interpretability decreases.

The authors also used Network Dissection for Generative Adversarial Networks (GANs). You can find Network Dissection for GANs on the project's website."

# 9.1.3 Advantages

Feature visualizations give unique insight into the working of neural networks, especially for image recognition. Given the complexity and opacity of neural networks, feature visualization is an important step in analyzing and describing neural networks. Through feature visualization, we have learned that neural networks learn simple edge and texture detectors first and more abstract and object detectors in higher layers. Network dissection expands these insights and makes interpretability of network units measurable.

Network dissection allows us to automatically link units to concepts, which is very convenient.

Feature visualization is a great tool to communicate in a non-technical way how neural networks work.

With network dissection, we can also detect concepts beyond the classes in the classification task. But we need datasets that contain images with pixel-wise labeled concepts.

Feature visualization can be combined with feature attribution methods, which explain which pixels were important for the classification. The combination of both methods allows to explain an individual classification along with local visualization of the learned features

> 9https://gandsect.csail.mit.edu/