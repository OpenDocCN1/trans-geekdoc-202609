# 3.5.2 Level set methods

Before proceeding any further, let us extend the active contours approach where contours are represented as implicit surfaces by means of level set function. It includes a level set function whereby it transforms from one state to another in capturing the edges of the objects. One of the strengths of level set methods is the interaction with topology changes such as contour merging and splitting, which is important for sharp and dynamic geometry. This flexibility is especially advantageous in medical imaging, for structures are vastly different from one another.

# 3.5.3 Deformable models

Other model-based techniques are deformable models, incorporating a priori beliefs about the shape and appearance of objects to drive the segmentation process. These models deform and fit the observed data by using statistical shape models also known as templates. This deformation was achieved according to the objective function capable of maintaining consistency of the models with the image features. As has already been seen, deformable models are quite useful when the structure in the images has similar shape in different people, such as organs, but needs fine-tuning for appearance and small shape differences.

# 3.5.4 Statistical shape models

Statistical shape models extract information from a training set of examples of the shape we are modeling. These models represent object shapes as distortions from the average shape that is embedded in a lower dimensional shape space. Using the training data, statistical shape models identify the changes that occur in shape onto which new images are mapped for segmentation. It is especially advantageous in linear structures where the geometry is seen to vary little from the main structure, such as with bones, and this approach could potentially improve segmentation results if prior information about within-class shape variation is available.

# 3.5.5 Template matching

Template matching means applying templates of certain anatomic structures and then using them to match and segment images. Usually, it expands the image data to the predetermined templates and utilizes the relevant similarity assessment to make a decision on the selection. Template matching in general can employ the correlation approach, a feature-based approach. Although this method proves efficient in certain