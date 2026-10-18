![](bbox=[0.107, 0.087, 0.79, 0.459])

**Fig. 2:** Cloud Edge IoT model

# 7 Implementation of the Recommended Cloud-Edge-IoT Model

Our approach to ensuring security measures put in place before sending enabled gadgets to IoT has been proven in terms of planning and ensuring that they can safely transfer and share information, protecting data encryption. Fig. 3 below shows the emergence of machinery, system, and book model. The model contains AWS cloud as expert cloud, Raspberry Pi 4 as Edge Node, and Virtual Machines as IoT gadgets. The framework we have created is a paid AWS record for full acceptance of assets provided by AWS, including testament keys and encryption, approval and validation.

From the assets acquired by AWS, we have implemented AWS Identity and Access Management (IAM) web administration. It allows us to control client login by setting up an IAM (customer representation) account for all clients. For security reasons, we did not use the AWS Root account but started the IAM client with authorized authorization. Designing the Raspberry Pi as a Edge hub (AWS Greengrass Core), AWS Greengrass Core works directly with the cloud and works locally.