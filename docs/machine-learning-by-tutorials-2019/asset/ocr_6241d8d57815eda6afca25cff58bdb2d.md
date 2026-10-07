# Ground-truth will set you free

Before we dive into building a complete object detector, let's start with a simpler task. You will first extend last chapter's MobileNet-based classification model so, in addition to the regular class prediction, it also outputs a single bounding box that tries to localize where the most important object is positioned in the image.

Just predict one bounding box, how hard could it be? (Answer: It's actually easier than you might think.)

First, we should revisit the dataset.

Even though this new neural network will now make a different kind of prediction, the training procedure is still the same: You provide a dataset that consists of the images and the targets. You also provide a suitable loss function that calculates how wrong the model's predictions are by comparing them to the targets. Then you use a Stochastic Gradient Descent optimizer like Adam, to find the values for the model's learnable parameters that make the loss as small as possible. Been there, done that.

No matter what your neural network performs, whether it's predicting classes or bounding boxes — or the weather or stock prices or anything else — the training process is always the same. However, each task needs its own kind of training data. And for object detection tasks, the training data must contain bounding box information.

Previously, the targets were just the class names for the images, but now they must also include the so-called ground-truth bounding boxes that tell you where the objects are located inside the images. Without these bounding annotations, the loss function wouldn't be able to calculate how wrong the model is, and training the model to predict bounding boxes would be impossible.

We have provided the bounding box annotations for the snacks dataset as a set of CSV files. To get a feel for how they work, you'll now take a closer look at those annotations. Create a new Lypter notebook or follow along with **final/Localization.ipynb** from this chapter's resources.