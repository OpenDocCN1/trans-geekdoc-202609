# Design implementation of PPE detection system using YOLOv9 19

continue to pose a significant concern. Conventional monitoring techniques frequently take a long time, prone to human error, and are not real the suggested approach seeks CV to address these issues. The main component of the solution is a YOLO9-based system with two main features that improve worker safety: (1) Automated PPE Detection: This encourages adherence to safety procedures and provides feedback for training enhancements by automatically identifying employees and confirming PPE usage. (2) Real-Time Worker Fall Detection: This feature allows for prompt intervention in fall-prone workplaces, preventing severe injuries, by identifying falls as they happen. The suggested approach seeks to improve real-time hazard identification, automate safety monitoring, enabling proactive actions, and collect important data for a data-driven safety culture. Through the use of YOLOv9 and CV, it aims to provide a more secure workplace by using an automated system. The investigation addressed the problem of precise PPE and fall detection in real-time workplace monitoring.

A strategy with multiple stages was used to accomplish this. The initial step was gathering and selecting relevant datasets that included pictures of workers of fall and PPE. Careful preprocessing methods were used after data collection to ensure the data's quality and usefulness for object detection model training. Ultimately, a potent YOLO9 model was selected for its capacity to accurately detect PPE and falls in workplace settings in real time. The YOLO9 model was trained using a dataset that was obtained from Roblox, a platform renowned for offering superior CV datasets. The collection includes 7,784 photos for fall detection and 1,613 images for PPE kit detection, each of which captures a different workplace scenario. The "PPE Dataset" is an extensive image collection designed to facilitate the development of machine learning algorithms for workplace safety. Its main goal is to enable training and improvement of models for identifying and classifying various kinds of PPE. By focusing on the identification of PPE, the dataset aims to foster the development of automated surveillance systems capable of upholding safety standards, ultimately reducing workplace accidents.

Phase 1 - Collection: Images are gathered from diverse sources, encompassing various environments, lighting conditions, and angles.

Phase 2 - Annotation: Continuous labeling of images with precise bounding.

Phase 3 - Model Training: Training of advanced object detection models. Class Types: The PPE dataset includes annotated images across four primary PPE categories:

Boots: Safety footwear, comprising steel-toe and insulated boots.
Helmet: Different types of helmets and hard hats.
Person: Individuals with and without PPE to enhance person detection alongside PPE recognition.

Vest: High-visibility vests and reflective safety gear for visibility in low-light condition.