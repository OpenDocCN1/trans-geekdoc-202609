# 8 Discussion and Analysis

IoT gadgets are classified as virtual machines, made into AWS, and added to the Greengrass facility, as shown in Figure 4 below. At the time of creation, a special announcement was made, public and private keys to all gadgets to verify them through AWS and the Greengrass Core gadget. The connection between the two gadgets is made through a secure system using an MQTT session called the message vendor. Finally, Fig. 5 shows both IoT and Edge hub facilities being successfully deployed and information trading completed at specific times.

The following are some key points to keep in mind about our AWS workspace and model used:

+   - In every model, IoT gadgets are either portable or come with AWS IoT Core.
+   - In our model we added an edge view using the Green grass IoT centre view on AWS, and spoke to it via Pi, so that we could see it as an additional middle ground between IoT and AWS IoT Core gadgets and then a cloud.
+   - Each gadget needs its own authentication, private key, and CA Root announcement (this is an AWS IoT agreement). There are different types of CA Root agreement based on IoT gadget types.
+   - Each gadget needs a strategy, this setting indicates which functions this gadget can perform (interface/find/distribute/purchase, etc.)

![](bbox=[0.1, 0.5, 0.79, 0.85])

Fig. 4: IoT-enabled nodes