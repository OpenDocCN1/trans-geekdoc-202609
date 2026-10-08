
## Similarity Learning

Here is a sample of the images present in the dataset:

![](img/48c861eac4dc634fbf2a09fdbe884beb_189_0.png)

Proposed by Cao et al. and reproduced from http://www.robots.ox.ac.uk/~vgg/vgg_face2/web_page_img.png

The minimum, mean, and maximum number of images per unique person are 87, 362.6, and 843 respectively.

## Computing the similarity between faces

The computing of face similarities is a multi-step problem. The faces have to be detected, followed by finding the fiducial points. The faces can be aligned with the fiducial points for comparison. As I have mentioned earlier, face detection is similar to object detection. So, in order to find the similarities between faces, we will first import the required libraries and also the facenet library, with the help of the following code:

```python
import scipy.misc
import tensorflow as tf
import numpy as np
import os
import facenet
print(facenet)
from facenet import load_model, prewhiten
import align.detect_face
```

## Similarity Learning

## Chapter 6

The images can be loaded and aligned as shown:

```python
def load_and_align_data(image_paths, image_size=160, margin=24,
    gpu_memory_fraction=1.0):
    minsize = 20
    threshold = [0.6, 0.7, 0.7]
    factor = 0.709

    print('Creating networks and loading parameters')
    with tf.Graph().as_default():
        gpu_options = tf.GPUOptions(per_process_gpu_memory_fraction=gpu_memory_fraction)
        sess = tf.Session(config=tf.ConfigProto(gpu_options=gpu_options,
            device_placement=False))
        with sess.as_default():
            pnet, rnet, onset = align.detect_face.create_mtcnn(sess, None, None)
    
    nrof_samples = len(image_paths)
    img_list = [None] * nrof_samples
    for i in range(nrof_samples):
        img = misc.imread(os.path.expanduser(image_paths[i]), mode='RGB')
        img_size = np.array(img.shape)[0:2]
        bounding_boxes = align.detect_face.detect_face(img, minsize,
            pnet, rnet, threshold, factor)
        det = np.squeeze(bounding_boxes[0, 0:4])
        bb = np.zeros(4, dtype=np.int32)
        bb[0] = np.maximum(det[0] - margin / 2, 0)
        bb[1] = np.maximum(det[1] - margin / 2, 0)
        bb[2] = np.minimum(det[2] + margin / 2, img_size[1])
        bb[3] = np.minimum(det[3] + margin / 2, img_size[0])
        cropped = img[bb[1]:bb[3], bb[0]:bb[2], :]
        aligned = misc.resize(cropped, (image_size, image_size),
            interp='bilinear')
        prewhitened = prewhiten(aligned)
        img_list[i] = prewhitened
    images = np.stack(img_list)
    return images
```

## Similarity Learning

Now we will process the image paths to get the embeddings. The code for the same is given here:

```python
def get_face_embeddings(image_paths, model='/20170512-110547/'):
    images = load_and_align_data(image_paths)
    with tf.Graph().as_default():
        with tf.Session() as sess:
            load_model(model)
            images_placeholder = tf.get_default_graph().get_tensor_by_name("input:0")
            embeddings = tf.get_default_graph().get_tensor_by_name("embeddings:0")
            phase_train_placeholder = tf.get_default_graph().get_tensor_by_name("phase_train:0")
            feed_dict = {images_placeholder: images, phase_train_placeholder: False}
            emb = sess.run(embeddings, feed_dict=feed_dict)
    return emb
```

Now we will compute the distance between the embeddings using the following code:

```python
def compute_distance(embedding_1, embedding_2):
    dist = np.sqrt(np.sum(np.square(np.subtract(embedding_1,
embedding_2)))
    return dist
```

This function will compute the Euclidean distance between the embeddings.

## Finding the optimum threshold

Using the preceding functions, the accuracy of this system can be calculated. The following code can be used for calculating the optimum threshold:

```python
import sys
import argparse
import os
import re
from sklearn.metrics import classification_report
from sklearn.metrics import accuracy_score
```

## Similarity Learning

## Chapter 6

Now, the image paths are obtained from the folder, using the following code:

```python
def get_image_paths(image_directory):
    image_names = sorted(os.listdir(image_directory))
    image_paths = [os.path.join(image_directory, image_name) for name in image_names]
    return image_paths
```

The distances of images are obtained when embeddings are passed, as shown in the following code:

```python
def get_labels_distances(image_paths, embeddings):
    target_labels, distances = [], []
    for image_path_1, embedding_1 in zip(image_paths, embeddings):
        for image_path_2, embedding_2 in zip(image_paths, embeddings):
            if re.sub(r'\d+', '', image_path_1).lower() == re.sub(r'\d+', '', image_path_2).lower():
                target_labels.append(0)
            else:
                distances.append(compute_distance(embedding_1, embedding_2))
    return target_labels, distances
```

Replace distance metric here

The threshold is varied as shown in the following code and various metrics are:

```python
def print_metrics(target_labels, distances):
    accuracies = []
    for threshold in range(50, 150):
        predicted_labels = [1 if dist < threshold else 0 for dist in distances]
        accuracy = accuracy_score(target_labels, predicted_labels)
        print(classification_report(target_labels, predicted_labels))
        print('Accuracy:', accuracy)
        accuracies.append(accuracy)
    print(max(accuracies))
```

Now, the image paths are obtained from the folder, using the following code-to:

```python
def main(args):
    image_paths = get_image_paths(args.image_directory)
    embeddings = get_face_embeddings(image_paths)
    target_labels, distances = get_labels_distances(image_paths, embeddings)
    print_metrics(target_labels, distances)

if __name__ == '__main__':
    parser = argparse.ArgumentParser()
    parser.add_argument('image_directory', type=str, help='Directory
    containing the images to be compared')
    parsed_arguments = parser.parse_args(sys.argv[1:])
    main(parsed_arguments)
```

## Face clustering

Face clustering is the process of grouping images of the same person together. The embeddings of faces can be extracted, and a clustering algorithm such as K-means can be used to cluster the faces. TensorFlow provides an API called tf.contrib.learn.kmeans for the K-means algorithm. The K-means algorithm groups data points together.

## Summary

In this chapter, we covered the basics of similarity learning. We studied algorithms such as metric learning, Siamese networks, and FaceNet. We also covered loss functions such as contrastive loss and triplet loss. Two different domains, ranking and recommendation, were also covered. Finally, the step-by-step walkthrough of face identification was covered by understanding several steps including detection, fiducial points, similarity scoring.

In the next chapter, we will understand Recurrent Neural Networks and their use in Natural Language Processing. Later, we will use language models combined with image models for the captioning of images. We will visit several algorithms for this problem and see an implementation of two different types of data.

## Image Captioning

In this chapter, we will deal with the problem of captioning images. This involves detecting the objects and also coming up with a text caption for the image. Image captioning can also be called **Image to Text translation**. Once thought a very tough problem, we have reasonably good results on this now. For this chapter, a dataset of images with corresponding captions.

We will cover the following topics in this chapter:

- Understand the different datasets and metrics used to evaluate them
- Understand some techniques used for natural language processing problems
- Different words for vector models
- Several algorithms for image captioning
- Adverse results and scope for improvement

## Understanding the problem and datasets

The process of automatically generating captions for images is a key deep learning task, as it combines the two worlds of language and vision. The uniqueness of the problem makes it one of the primary problems in computer vision. There are few datasets for this problem. The most famous of the datasets is an extension of the COCO dataset covered in object detection in Chapter 4, Object Detection.
