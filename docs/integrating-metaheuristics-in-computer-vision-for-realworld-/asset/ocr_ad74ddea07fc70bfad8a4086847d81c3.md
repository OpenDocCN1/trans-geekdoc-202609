# 12.3.6.3 Online Switch

So, we have already discussed about how we used blinky server to connect with the nodeMCU so that the user can manage the house appliances with the mobile phone in his hands. Now we can discuss about how we can improve this.

Let us say we have installed camera in all the rooms in the house. Now we can use OpenCV library in to write a code to detect a person in the house. The camera continuously watches for a person in the home if there was no human found in the room, we can use the computer to control the appliances in the room.

Let's say we have a fan we can switch off it if there was no human more than 10 seconds. If an oven is switched on , we don't use it more than 30 minutes so the system should be attached with timer. Here can see how it can be achieved [6].

# Components Required

+   1. camera
+   2. USB cable
+   3. relay switch
+   4. DB-25 portal

# Components description

+   1. camera
+   Camera is in use to monitor the room continuously. It sends the data to the computer via USB.

+   2. DB-25 portal
+   DB-25 portal was used to send signal from computer to the relay switch. It is the communication link between the switch and the computer.

+   3. Relay Switch
+   Relay switches were used to turn the electrical appliances on and off when the signal from the processed image is negative.

# Working of the system

First, we are going to make an algorithm to detect the face in the room. We use OpenCV Library in this system. But since it only can detect the frontal possess, we also try to detect in any possess which would take additional steps and large amount of database.

This system is just an enhanced version of online switch which can be used for power management purpose. It improvise in the matter of decision-making process by the system itself. It basically has three phases.

+   1. We have to train the system to detect human faces with the live feed of images from the camera working in shorter time to detect it.

+   2. Next, we should process the images in the computer and send a signal to the relay switch.

+   3. And at last, the relay switch should receive the signal and switch off the electrical appliances.