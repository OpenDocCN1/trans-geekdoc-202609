# Chapter 3

# Image Retrieval

The list of matches can be used to retrieve the image details. The index of the items will be returned.

> Visit https://github.com/spotify/annoy for a complete implementation of ANNOY and its benchmark comparison against other approximate nearest neighbour algorithms, in terms of accuracy and speed.

# Advantages of ANNOY

There are many reasons for using ANNOY. The main advantages are listed as follows:

+   * Has a memory-mapped data structure, hence, less intensive on RAM. The same file can be shared among multiple processes due to this.
* Multiple distances such as Manhattan, Cosine, or Euclidean can be used for computing the similarity between the query image and target database.

# Autoencoders of raw images

An autoencoder is an unsupervised algorithm for generating efficient encodings. The input layer and the target output is typically the same. The layers between decrease and increase in the following fashion:

![](bbox=[0.124, 0.558, 0.863, 0.853])

[ 100 ]