+   - Upload Picture: In the activity page, the user has an option to upload the picture of the diseased leaf. The pixel range of the picture is set to a threshold, and the user is expected to upload a picture of the same range.
- Clear Picture: If the user wants to change the picture he has already uploaded, the user clicks on the clear option and uploads other pictures.

# 13.9 Design Diagrams

# 13.9.1 High-Level Design

A flowchart is a graph that portrays a cycle, framework, or PC calculation. They are utilized in the structure and development of straightforward cycles or projects. Like different kinds of charts, they help picture what is happening, helping to comprehend the cycle, and maybe additionally finding more subtle highlights inside the cycle, including such blemishes and bottlenecks.

There are various kinds of flowcharts where each type has its own arrangement of boxes and documentations.

Figure 13.5 represents the flowchart for user where the user logs into the mobile application using his email and password. In the activity page, the user uploads the picture and submits the picture. The pixel range of the picture is set to a threshold; the user is expected to upload a picture of the same range [33, 34]. After the picture has been uploaded, picture processing begins, and noise removal and conversion to grayscale picture take place. The grayscale picture is used to extract features such as the color of the leaf, gradient, width, and height of the leaf. Features extracted are classified based on the type of the disease. Result is displayed to the user, which describes the name of the disease [35, 60].

# 13.9.2 Low-Level Design

The diagram depicts the interactions between objects in sequential order.

Figure 13.6 represents the sequence diagram for user where the user logs into the mobile application using his email and password. In the activity page, the user uploads the picture and submits the picture. The pixel range of the picture is set to a threshold; the user is expected to upload a picture of the same range [36]. After the picture has been uploaded, picture