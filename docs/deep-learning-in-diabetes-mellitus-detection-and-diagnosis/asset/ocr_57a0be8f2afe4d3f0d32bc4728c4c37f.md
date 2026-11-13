x₁ – pregnancies, x₂ – glucose, x₃ – blood pressure, x₄ – skin thickness,
x₅ – insulin, x₆ – body mass index (BMI), x₇ – diabetes pedigree function,
and x₈ – age. These eight input parameters of each medical record are
given as input for input feature layer. The proposed model has three fully
connected layers each containing 50 hidden neurons. From Figure 7.3, it
is understood that all the neurons from input feature layer are connected
to all neurons of the fully connected layers. This scheme continues till the
softmax layer. Batch normalization is carried out to make the network
faster and stable. Batch normalization works by normalizing the output of
a previous activation layer by subtracting the batch mean and dividing by
the batch standard deviation [26]. After this step, the result is then scaled
and shifted by two learnable parameters, gamma and beta, which are
unique to each layer [26]. A ReLU is an activation function that introduces
the property of nonlinearity to a DLM and solves the vanishing gradients
issue of the neural network [27]. The output of the fully connected layer
is given to the softmax layer that gives the probability score of each class.
Based on this probability, the output of the classification layer is category
'1' or '0'. Category '1' represents the DM and '0' represents non-DM.

# 7.5 DATASET

Two similar datasets as shown in Table 7.2 are downloaded to develop
and test the DLM. The dataset shared by the hospital from Frankfurt,
Germany, is downloaded from Kaggle [28]. The dataset has 2000 DM test
readings that contain parameters such as x₁ – pregnancies, x₂ – glucose,
x₃ – blood pressure, x₄ – skin thickness, x₅ – insulin, x₆ – body mass index
(BMI), x₇ – diabetes pedigree function, x₈ – age and outcome class (Y, N).
To have same output class with the other dataset, the category Y and N are
changed to 1 and 0. The primary objective of these datasets was to predict
whether a patient is afflicted with DM or not.

The second dataset PIDD is downloaded from Kaggle [29]. This dataset
has 768 DM test readings with the same parameters as the previous data-
set. The aim of DM detection is to build a simple DLM using Germany

TABLE 7.2 Description of Dataset

| Properties | Germany | PIDD |
|---|---|---|
| Features | 9 | 9 |
| Samples | 2000 | 768 |
| Missing values | 0 | 0 |
| Target class | 2 (Y, N) | 2 (0, 1) |