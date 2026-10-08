# Image Retrieval

# Chapter 3

In the inception model, the bottleneck layer is named pool_3/_reshape:0, and the layer is 2,048 dimensions. The input placeholder name is DecodeJpeg/contents:0, and the resize tensor name is ResizeBilinear:0. We can import the graph definition using tf.import_graph_def with the required tensors for further operations:

```
bottleneck, image, resized_input = (
    tf.import_graph_def(
        graph_definition,
        name='',
        return_elements=['pool_3/_reshape:0',
                         DecodeJpeg/contents:0',
                         'ResizeBilinear:0'])
)
```

Take a query and target image and load it in the memory. The gfile function provides a faster way to load the image into the memory.

```
query_image_path = os.path.join(work_dir, 'cat.1000.jpg')
query_image = gfile.FastGFile(query_image_path, 'rb').read()
target_image_path = os.path.join(work_dir, 'cat.1001.jpg')
target_image = gfile.FastGFile(target_image_path, 'rb').read()
```

Let define a function that extracts the bottleneck feature from an image, using the session and image:

```
def get_bottleneck_data(session, image_data):
    bottleneck_data = session.run(bottleneck, {image: image_data})
    bottleneck_data = np.squeeze(bottleneck_data)
    return bottleneck_data
```

Initiate the session, and pass the image to the forward inference to get the bottleneck values from the pre-trained model:

```
query_feature = get_bottleneck_data(session, query_image)
print(query_feature)
target_feature = get_bottleneck_data(session, target_image)
print(target_feature)
```

Running the above code should be shown as:

+   [ 0.55707922 0.36785451 1.06618118 ..., 0.60118211 0.36407694
0.0996572 ]
[ 0.30421323 0.09263639 0.26213276 ..., 0.72273785 0.30847171
0.08719242 ]