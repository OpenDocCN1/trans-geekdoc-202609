
![](img/cbc35e0d02425baa6028b87d56263a7f_350_0.png)

Picture [26] depicts the pictures trained using the CNN model. For classification, a CNN model is used where there are numerous convolution layers, which increases the accuracy with every convolution.

The picture depicts as a two-dimensional array of pixels by means of amount in each position. To determine coordinating an element to an image fix, the CNN model duplicates every pixel in the element by the estimation of the relating pixel in the picture [27, 56]. At that point, it includes the appropriate responses and partitions the complete number of pixels in the element. When contrasting two pictures, if any pixel esteems do not coordinate, the images do not match. To complete the process, the process is repeated, lining up the feature with every possible picture patch.

### 13.8.1 Module Characteristics

The following stepwise procedure to be followed:

- Picture acquisition
- Picture processing
- Feature extraction and segmentation
- Image processing
- Picture segmentation
- Classification

**Picture Acquisition**

Picture acquisition is formation of a digitally determined illustration for visual description of a leaf's picture. The primary stage of the scheme is the picture acquisition because the picture has to be obtained to apply various processing methods. It includes the processing and compression of the picture.

**Picture Processing**

The digital pictures are analyzed and manipulated to improve quality. It includes loading a picture, enhancing contrast, converting RGB to HSB, and extracting features.

**Feature Extraction and Segmentation**

In picture handling, the extraction of highlights starts with estimating of primer information that get determined qualities with the point of which are expected to be instructive and non-repetitive, encourages subsequent information and disentanglement steps, and prompts better human translation [28, 57].

Picture division is a cycle of parcelling a computerized picture into numerous fragments. The point of division is to rearrange and change the portrayal of an image which gives considerable and simpler approach to dissect [29, 58].

**Classification**

Arrangement incorporates two periods of preparing and testing utilizing any classifier. In the preparation stage, the classifier is prepared utilizing the estimation of the qualities and its particular objective qualities. This certified classifier is then used to order the image highlights [30, 31].

### 13.8.2 Convolutional Neural System

At the point when the image goes through a convolution layer, the yield of the principal level turns into the contribution of the subsequent layer. What is more, this will occur with each other convolutionary layer [32, 59]. After every convolution activity, the nonlinear layer is included. It has an initiation work, which unites nonlinear properties. Without this property, the system would not be adequately extraordinary and would not have the option to do so reaction variable is displayed.

### 13.8.3 User Application

- Login Page: After the registration process, the user shall proceed to login page, and user provides email address and the password to enter into the activity page.
- Upload Picture: In the activity page, the user has an option to upload the picture of the diseased leaf. The pixel range of the picture is set to a threshold, and the user is expected to upload a picture of the same range.
- Clear Picture: If the user wants to change the picture he has already uploaded, the user clicks on the clear option and uploads other pictures.

## 13.9 Design Diagrams

### 13.9.1 High-Level Design

A flowchart is a graph that portrays a cycle, framework, or PC calculation. They are utilized in the structure and development of straightforward cycles or projects. Like different kinds of charts, they help picture what is happening, helping to comprehend the cycle, and maybe additionally finding more subtle highlights inside the cycle, including such blemishes and bottlenecks.

There are various kinds of flowcharts where each type has its own arrangement of boxes and documentations.

Figure 13.5 represents the flowchart for user where the user logs into the mobile application using his email and password. In the activity page, the user uploads the picture and submits the picture. The pixel range of the picture is set to a threshold; the user is expected to upload a picture of the same range [33, 34]. After the picture has been uploaded, picture processing begins, and noise removal and conversion to grayscale picture take place. The grayscale picture is used to extract features such as the color of the leaf, gradient, width, and height of the leaf. Features extracted are classified based on the type of the disease. Result is displayed to the user, which describes the name of the disease [35, 60].

### 13.9.2 Low-Level Design

The diagram depicts the interactions between objects in sequential order.

Figure 13.6 represents the sequence diagram for user where the user logs into the mobile application using his email and password. In the activity page, the user uploads the picture and submits the picture. The pixel range of the picture is set to a threshold; the user is expected to upload a picture of the same range [36]. After the picture has been uploaded, picture processing begins; noise removal and conversion to the grayscale picture take place. The grayscale picture is used to extract features such as the color of the leaf, gradient, width, and height of the leaf [37, 38]. The features extracted classify the type of the disease. The result is displayed to the user, which describes the name of the disease.

![](img/cbc35e0d02425baa6028b87d56263a7f_353_0.png)

**Figure 13.5** Flowchart for user.

![](img/cbc35e0d02425baa6028b87d56263a7f_354_0.png)

**Figure 13.6** Sequence diagram for user.

### 13.9.3 Test Cases

Table 13.1 provides the test cases which have been carried out with respect to the work.

| Test case no. | Description | Expected output | Actual output | Result |
| --- | --- | --- | --- | --- |
| 1 | The picture pixels are not in the range of 0 to 255 | Upload an picture which is in the range of 0 to 255 | Upload an picture which is in the range of 0 to 255 | Successful |
| 2 | The picture pixels are in the range of 0 to 255 | dispensation of the Picture begins | Processing of the Picture begins | Successful |
| 3 | The uploaded picture does not belong to the five crops chosen for the concept | Displays the message “Upload an picture of the specified crop” | Displays the message “Upload an picture of the specified crop” | Successful |
| 4 | The uploaded picture is not in jpeg format | Displays the message “Upload an picture which is in jpeg format” | Displays the message “Upload an picture which is in jpeg format” | Successful |
| 5 | Internet connection is not available | Displays the message “Internet Connection is required” | Displays the message “Internet Connection is required” | Successful |

## 13.10 Comparison and Screenshot

Figure 13.7 shows that when the user clicks on the mobile application for the first time, the user will be directed to registration page and asked to fill the details such as name, email address, and set the password.

Figure 13.8 depicts the registration process; the user will be directed to the login page users email address, and the password will be entered into the activity page.

Figure 13.9 shows the activity page, and the user has an option to upload the picture of the diseased leaf. The pixel range of the picture is set to a threshold; the user is expected to upload a picture of the same range.

Figure 13.10 displays how user uploads the diseased folio picture of rice.

Figure 13.11 shows steps after the picture has been uploaded. Picture processing begins, and noise removal and conversion to grayscale picture take place.

Figure 13.12 depicts how features are being extracted as of the uploaded picture grayscale picture used to haul out features such as the color of the leaf, gradient, width, and height of the leaf. The features extracted will classify the type of the disease.

Figure 13.13 provides the insight where the result is displayed to the user, which describes the name of the disease. When the diseased rice folio picture is uploaded, the result is displayed as Bacterial Folio Blight.

In Figure 13.14, when the diseased rice folio picture is uploaded, the result is displayed as Brown Folio Spot.

In Figure 13.15, when the diseased rice folio picture is uploaded, the result is displayed as Verticillium wilt of cotton along with the suggestive measure.

In Figure 13.16, it describes that when a healthy picture is uploaded, the result after classification is displayed as unable to find disease.
