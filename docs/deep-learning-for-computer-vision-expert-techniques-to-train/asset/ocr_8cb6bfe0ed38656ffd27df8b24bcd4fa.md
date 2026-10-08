# Similarity Learning

# Chapter 6

```
image_input: fiducial_data_batch.images,
landmark_input: fiducial_data_batch.landmarks,
gender_input: fiducial_data_batch.gender,
smile_input: fiducial_data_batch.smile,
glasses_input: fiducial_data_batch.glasses,
headpose_input: fiducial_data_batch.pose,
dropout_bool: True
}
if batch_no % 10 == 0:
loss, _landmark_loss, _ = session.run(
[loss_operation, landmark_loss],
feed_dict={
image_input: fiducial_test_data.images,
landmark_input: fiducial_test_data.landmarks,
gender_input: fiducial_test_data.gender,
smile_input: fiducial_test_data.smile,
glasses_input: fiducial_test_data.glasses,
headpose_input: fiducial_test_data.pose,
dropout_bool: False
})
```

This process can be used to detect the facial features as well as landmarks.

![](bbox=[0.136, 0.463, 0.203, 0.526])

# Face recognition

The face recognition or facial recognition is the process of identifying a personage from a digital image or a video. Let's learn about the datasets available for face recognition in the next sections.

# The labeled faces in the wild (LFW) dataset

The LFW dataset contains 13,233 faces with 5,749 unique people and is considered as the standard dataset to evaluate face verification datasets. The dataset can be accessed in the link http://vis-www.cs.umass.edu/lfw/