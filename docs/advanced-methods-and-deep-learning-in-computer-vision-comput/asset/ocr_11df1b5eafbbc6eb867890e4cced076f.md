al., 2017). Each action category contains between 400 to 1,000 video clips, whose duration is around 10 seconds.

**OTB** (or OTB-2015) has 100 short videos with per-frame annotations of bounding boxes and 11 attributes, such as illumination and scale variations, occlusion, nonrigid object deformation, or out-of-view (Wu et al., 2015). OTB-13, the first release, contained 51 sequences.

**VOT**¹ contains 60 videos of fewer than 1,500 frames at 30 fps with various animals, people, or moving objects, often acquired with a moving camera. Examples of scenes include a person carrying a book, gymnastics, ants moving, flying birds, moving drones, a moving car on the road, fish in a water tank, people playing basketball, soccer, and handball. Per-frame annotations are available of rotated bounding boxes, segmentation masks, and attributes.

# 15.6 Image processing

In this section, we discuss adversarial attacks that aim at misleading image processing operations, such as *edge detection* (Cosgrove and Yuille, 2020) and *motion estimation* (Ranjan et al., 2019).

**Edge Attack** is devised to craft adversarial perturbations for a CNN-based edge detection model, HED (Xie and Tu, 2015). HED is trained on BSDS500 and combines the feature maps extracted from each convolution layer to classify whether each pixel in the image belongs to the object boundary or not. Edge Attack estimates the loss function for the edge detection and crafts the perturbations that maximize the gradient of the loss function (Goodfellow et al., 2015).

**Optical Flow Attack (OFA)** (Ranjan et al., 2019) aims to adversarially perturb two consecutive pairs of images (**x**_k, **x**_{k+1}) in a video such that the labels associated with the optical flow, i.e., the displacement vectors (*u*, *v*), are incorrectly predicted (untargeted attack). Because of the limited availability of datasets with dense optical flow annotations, OFA uses the optical flow prediction of the model *f*(·) as pseudo-annotation to self-supervise the learning of the *region-based* (e.g., circular patch) adversarial perturbation δ. OFA applies (e.g., pastes) the learned adversarial patch onto the image. In addition to perturbing a small number of pixels within a pair of consecutive images, OFA constrains the adversarial perturbation to be quasi-imperceptible, such that

$$\|\mathbf{x}_k - \hat{\mathbf{x}}_k\|_0 + \|\mathbf{x}_{k+1} - \hat{\mathbf{x}}_{k+1}\|_0 < \epsilon, \tag{15.1}$$

where $\epsilon$ is a small constant (bounded perturbation), while the predicted output of the optical flow model $f(\cdot, \cdot)$ on the perturbed images is significantly affected, i.e.,

$$\| f(\mathbf{x}_k, \mathbf{x}_{k+1}) - f(\hat{\mathbf{x}}_k, \hat{\mathbf{x}}_{k+1}) \| > E, \tag{15.2}$$

where $E$ is a large constant.

¹ https://www.votchallenge.net.