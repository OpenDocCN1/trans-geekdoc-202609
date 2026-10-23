Think of this use-case: While we do our transforms, the keypoints could be moved outside of the image range (e.g. RandomResizeCrop - this transform crops the image). While doing the cropping, the coordinates of our keypoints could be moved outside of the cropped image.

We can handle this case differently: * Should we keep the point and let the model guess the new keypoint coordinates or * do we want our model to remove the point

We will build a custom ClampBatch transform. Later on we do have to use the block because our model will either use padding or squishing on the resize transforms.