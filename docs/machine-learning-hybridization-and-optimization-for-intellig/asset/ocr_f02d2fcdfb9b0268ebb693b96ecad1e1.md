# TABLE 13.2 Accuracy values

| Training accuracy | Validation accuracy |
| --- | --- |
| 97% | 92% |

We were able to get a training accuracy of 97% and a validation accuracy of 92%. These metrics are indicative that the model was able to classify the images fairly well, and it can be applied in a real-world situation.

# 13.7.2 DOCKER

In this subsection, we go over the findings of the application of Docker in our proposed system.

![](bbox=[0.178, 0.418, 0.79, 0.595])

# FIGURE 13.7 Docker images for the model

In Figure 13.7, we observe the image of the model successfully created. Docker images are templates which define how Docker containers would be created. They are the basic component for the reproducibility of code. They define how the containers need to be initialized and how the environment needs to be set up. To create reusable entities in the Docker environment, we firstly need to create a Docker image for our work. This image can then be shared and used to create any number of Docker containers, which are instances of the image running in their independent environments, with all their requirements available in their isolated environment.