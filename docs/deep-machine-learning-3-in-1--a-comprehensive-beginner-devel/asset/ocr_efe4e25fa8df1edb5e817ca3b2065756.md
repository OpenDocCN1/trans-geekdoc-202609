# Sequence Data

Whenever time matters in data, it is wiser to store the data inside a 3D tensor that has quite an explicit 3D tensor. Here each sample ought to be encoded in the form of a 3D tensor. The time axis always is considered a second axis by tradition. Take a look at a couple of examples.

Suppose there is a dataset of the stock prices. As each minute passes, the current price of a particular stock has to be stored, along with the lowest and highest prices from the last minute. So, in this way each minute is being encoded in the form of a 3D vector. When the day ends, the entire trading day is encoded as follows (350, 3) in case the trading day has 350 minutes in total. You can use a 3D tensor to store 250 days’ worth of data as follows (250, 350, 3). Each sample of the tensor would be worth a single day’s worth of data.

You also can form a dataset of multiple tweets where you can encode a single tweet that consists of 250 characters. Each character of the tweet can be encoded as a binary vector of size 128 - the number of alphabets is 128. You can then encode each tweet as a 2D tensor in the following form (250, 128). If you have to create a dataset of 100,000 tweets, it will look like the following (100000, 250, 128).

# Images

Typically, images consist of three dimensions namely width, height, and depth of the color. Grayscale images similar to that are contained in MNIST digits possess a solitary color channel. They can be stored in 2D tensors. An image, by tradition, is packed in 3D tensors. Grayscale images have a 1-dimensional color channel. If you have a batch of 256 grayscale images that have 128, 128 sizes, you can store them in the following form (256, 128, 128, 1).

If we talk about conventions for images tensors, those are two namely channels-first conventions and channels-last convention.

# Videos

Video data is the type of real-world data for which you will need 5D tensors. A video should be viewed in the form of a frame sequence where each frame