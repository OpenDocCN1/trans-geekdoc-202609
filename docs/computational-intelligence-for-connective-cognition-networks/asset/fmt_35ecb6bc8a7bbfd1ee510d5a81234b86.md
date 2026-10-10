
## Training the CNN Model

During the training process, preprocessed images are fed into the CNN model. The model’s weights are updated through backpropagation to minimize the loss function and improve performance.

## Testing the CNN Model

The trained model is evaluated on a separate labeled dataset that was not used during training. Metrics like accuracy, precision, recall, and F1 score are calculated to assess the model’s effectiveness in detecting forgeries.

## Hyperparameter Tuning

To improve the CNN’s performance, key hyperparameters—such as the learning rate, batch size, and number of epochs—should be fine-tuned. Techniques like grid search or random search can be employed to optimize these hyperparameters.

## Deployment and Monitoring

The trained CNN model can be used to detect fake images in real time in a production environment. The model’s output can be used after preprocessing the input photos using the same methods as during training.

## System Monitoring and Development

The effectiveness of the picture forgery detection system should be regularly assessed and enhanced. This can be achieved by gathering user feedback, examining how the model performs when applied to fresh data, and modifying the model as required.

## Summary

Overall, developing and training the CNN model, testing and refining the model, deploying the system, and continuously monitoring and optimizing its performance are all steps in the implementation of an image fraud detection system utilizing CNNs.

### 5.4.1 Image Forgery Detection Using CNN Python (Trained Using CASIA2 Dataset)

*   Begin by importing all necessary libraries and mounting Google Drive if you’re using Google Colab (Figure 5.6a).

    ![Figure 5.6 Import libraries and prepare images.](html/images/9781032942346_C005_006.jpg)

    **Figure 5.6** Import libraries and prepare images.

*   Convert an image to an error level analysis (ELA) image (Figure 5.6b).

*   Prepare an image by converting it to ELA and resizing it (Figure 5.6c).

*   Dataset Preparation: Load and preprocess the dataset. Randomly select and shuffle the images for both genuine and forged categories (Figure 5.7a and b).

    ![Figure 5.7 Data preparation and pre-processing.](html/images/9781032942346_C005_007.jpg)

    **Figure 5.7** Data preparation and pre-processing.

*   Train-Test Split process: Divide the dataset into separate training and validation subsets (Figure 5.8).

    ![Figure 5.8 Train-test data split.](html/images/9781032942346_C005_008.jpg)

    **Figure 5.8** Train-test data split.

*   Define and compile the CNN model (Figure 5.9).

    ![Figure 5.9 CNN model.](html/images/9781032942346_C005_009.jpg)

    **Figure 5.9** CNN model.

*   Train the CNN model with early stopping and Plot Training History (Figure 5.10a and b).

    ![Figure 5.10 CNN early stopping and plotting.](html/images/9781032942346_C005_010.jpg)

    **Figure 5.10** CNN early stopping and plotting.

*   Evaluate the model using a confusion matrix and performance metrics (Figure 5.11a). Predict the class of new images and calculate the accuracy on a test set of fake and real images (Figure 5.11b).

    ![Figure 5.11 Results code.](html/images/9781032942346_C005_011.jpg)

    **Figure 5.11** Results code.

The implementation of an image forgery detection system employing CNNs may encounter several problems. Here are some important points to think about:

*   **Dataset bias**: Bias in the training dataset may have an impact on how well the CNN model performs. For instance, the model may become biased towards one class or the other if the training dataset contains an excessive amount of legitimate or altered photos. A diverse array of photos must be gathered, and the classes must be as evenly distributed as feasible, to overcome this problem.

*   **Limited data availability**: For rare instances of picture forgeries, it can be difficult to compile a sizable collection of labelled images. The CNN model may overfit to the training dataset if the dataset that is trained with is too small, and it may perform badly on fresh data. This problem can be solved by using data augmentation techniques to fictitiously expand the dataset and strengthen the model’s robustness.

*   **Computing power**: Using a sizable dataset to train a CNN model might demand a lot of processing power, such as powerful GPUs and lots of RAM. This can be costly and might call for specialized gear. Cloud computing platforms can be utilized to rent compute resources on an as-needed basis to solve this problem.

*   **Interpretability**: It can be difficult to grasp how CNN models generate their predictions because of their difficulty in interpretation. This might be a problem in situations where explainability is crucial. To visualize which areas of the image are most crucial for the model’s predictions, techniques like saliency maps and gradient-based attribution can be employed to solve this problem.

*   **Adversarial attacks**: CNN models are susceptible to adversarial attacks, in which a minor perturbation is injected into the input image to make the model predict incorrectly. In applications where security is crucial, this can be a problem. This problem can be solved by using methods like adversarial training and input preprocessing to strengthen the model’s defense against hostile attacks.

## 5.5 Result Analysis

The test dataset can be divided into multiple groups depending on the type of counterfeit (e.g., copy-move, splicing, or retouching) to know the system’s capacity to find out various forgeries. This allows for a distinct assessment of the system’s performance for each category. A confusion matrix shown in Figure 5.12 illustrates the performance of a classification model on a test dataset with known true values. It provides a visual representation of the algorithm’s effectiveness.

![Figure 5.12 Confusion matrix.](html/images/9781032942346_C005_012.jpg)

**Figure 5.12** Confusion matrix.

*   **Accuracy**: The overall accuracy of the model, which is the ratio of correctly predicted instances (both true positives and true negatives) to the total instances is calculated. The accuracy of 87.0% indicates that the model is generally performing well.

```
Accuracy = (TP + TN) / (TP + TN + FP + FN) = (370 + 357) / (370 + 357 + 46 + 62)
= 727 / 835 ≈ 0.870 (or 87.0%)
```

*   **Precision (for Real)**: The ratio of correctly predicted real images to the total predicted real images. The precision of 88.9% indicates that when the model predicts an image as real, it is correct 88.9% of the time.

```
Precision = TP / (TP + FP) = 370 / (370 + 46) ≈ 0.889 (or 88.9%)
```

*   **Recall (Sensitivity or True Positive Rate, for Real)**: The ratio of correctly predicted real images to the total actual real images. The recall of 85.6% indicates that the model correctly identifies 85.6% of the real images.

```
Recall = TP / (TP + FN) = 370 / (370 + 62) ≈ 0.856 (or 85.6%)
```

*   **F1 Score (for Real)**: The harmonic mean of precision and recall. F1 Score of 87.2% strikes a balance between precision and recall, offering a unified metric that accounts for both false positives and false negatives.

```
F1 Score = 2 × (Precision × Recall) / (Precision + Recall)
= 2 × (0.889 × 0.856) / (0.889 + 0.856) ≈ 0.872 (or 87.2%)
```

*   **Specificity**: The ratio of correctly predicted fake images to the total actual fake images. The specificity of 88.6% indicates that the model correctly identifies 88.6% of the fake images.
