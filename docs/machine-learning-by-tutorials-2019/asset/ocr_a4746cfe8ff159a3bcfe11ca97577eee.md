Unfortunately, there are also many images where the model doesn't so well:

![](bbox=[0.3538, 0.1435, 0.6462, 0.3935])

# Is this fair?

An IOU of 0.03, that's very bad. But can you really blame this on the model? This image has many apples, and you can argue that the model did indeed find (a portion of) an apple, just not the one in the annotation.

This image really isn't a fair test of our simple localization model, which was only trained to find a single object at a time. In the next chapter, you'll train a proper object detection model that can handle images like these and will find all the apples.

Another example:

![](bbox=[0.3538, 0.6055, 0.6462, 0.8555])

# Not great, but not really wrong either