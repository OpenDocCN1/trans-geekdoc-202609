Next you can put these into an easily indexed collection called transformed list and apply your transforms in parallel. Finally you use a data loader that applies these transforms in parallel.

Generally speaking, all the development of the fast.ai library was done by highly leveraging parallel computing on the GPU. E.g. most of the computer vision pipeline that is included with fastai is done in parallel on the GPU, minimizing computing time.

If you are interested in the facts behind architecture design decisions in fast.ai, you should watch this video of Jeremy Howard on Youtube:
https://youtu.be/bHVqO5YyNbU

# 1.4 Using Google’s Colab-Tool

If you want to run the examples in this book and you don’t have a GPU on your own, you have a few options.

You can start an EC2 instance on Amazon AWS (or any other computing platform). This will bill you for the time while running the instance. Make sure you have selected an instance level with a GPU. There are a few pros and cons though. If you are working on production level projects, you should consider a secure and reliable infrastructure stack. Then running a GPU server on a cloud platform will be a good solution.

For learning or working on examples/prototypes, etc. there is another handy option.

Google provides a tool called Colab that is (kind of) a hosted Jupyter Notebook instance which is completely free of charge, but of course with some caveats:

+   - Google does not reassure access to a GPU but there are hardly times without GPU access.
+   - Most of the time your session is paired to old, and rather slow, Tesla K80 GPUs.
+   - Your session is reset after a maximum runtime of 12 hours. This means all your data will be lost after 12 hours if you do not upload it to another storage