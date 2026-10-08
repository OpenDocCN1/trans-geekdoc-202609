seconds. In that sense, making a decision to stop at ten seconds is too late. The real-world time available is only about 8 seconds since there needs to be the time to come to a stop, if that's the right thing to do.

We now have the case of an AI self-driving car which is confronted with trying to determine if there is a stop sign ahead, and the AI has about 8 seconds to do so. There are potential adverse consequences if the AI decides to not stop the car and if the stop sign is truly a stop sign. Of course, you might be thinking, well, just bring the self-driving car to a halt anyway, as a precaution, even if it's not a stop sign, but if you ponder this for a moment I think you'll realize that suddenly coming to a halt can have equally undesirable consequences. The car behind you might ram into you. Etc.

For AI self-driving cars, they tend to have five key stages when processing the world around them and taking action. Those five stages are:

+   - Sensor Data Collection
- Sensor Fusion
- Virtual World Model Updating
- AI Action Plan Updating
- Car Controls Commands Issuance

The self-driving car that is trying to figure out the situation with the stop sign has to first contend with detecting the stop sign. This would primarily involve the visual sensors such as the cameras on the self-driving car. The images collected by the cameras would be examined by the AI, often using a machine learning model to do so.

This could be an artificial neural network that has been trained on thousands and thousands of images of street signs. The images of this particular suspected street sign would be fed into the neural network. The neural network might indicate that it is or is not a stop sign, or might provide an indication with some amount of probability attached to it. In essence, there's say a 65% chance that it is a stop sign. This though needs to be balanced against the aspect that this implies there's a 35% chance it is not a stop sign.

In theory, the sensor data collection should occur and after having