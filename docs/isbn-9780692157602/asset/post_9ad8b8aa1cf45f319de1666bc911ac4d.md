
notably known as an infinite loop.

What does this have to do with AI self-driving cars?

At the Cybernetic AI Self-Driving Car Institute, we are developing AI software and also caution fellow tech firms and auto makers to make sure that their AI for self-driving cars does not suffer a freeze.

## The Freezing Robot Problem

The kind of freeze we are referring to is commonly called the Freezing Robot Problem (FRP).

Imagine that an AI self-driving car is driving down the street. Up ahead is a street sign that kind of looks like a stop sign. It is bent and mauled. You’ve maybe seen these before — it looks like some hooligan decided to hang on the stop sign and bend it into a pretzel. Now, it could be that it isn’t really a stop sign at all, and it just is some kind of art piece that resembles a stop sign. Or, maybe it is indeed a legally valid stop sign and that in spite of the now bent out-of-shape structure it is really truly a stop which must be obeyed.

In this murky aspect of trying to ascertain if the stop sign is true or not, it is possible to encounter the Freezing Robot Problem. Here’s how.

Let’s assume that the self-driving car is approaching the sign and has ten seconds until it reaches where the sign is posted. We now have a time limit – a decision needs to be made within no later than 10 seconds. If the decision occurs at 15 seconds, it’s too late and the self-driving car would likely have already driven past the sign, having merely continued forward since there was no other command from the AI otherwise. If it really is a stop sign, the self-driving car has then broken the law, and possibly endangered other cars and pedestrians.

Some AI self-driving car pundits claim that a self-driving car will never break the law, for which I say hogwash.

Even if the decision can be reached in the ten seconds, let’s pretend that for the car to be brought to a halt would require at least 2 seconds. In that sense, making a decision to stop at ten seconds is too late. The real-world time available is only about 8 seconds since there needs to be the time to come to a stop, if that's the right thing to do.

We now have the case of an AI self-driving car which is confronted with trying to determine if there is a stop sign ahead, and the AI has about 8 seconds to do so. There are potential adverse consequences if the AI decides to not stop the car and if the stop sign is truly a stop sign. Of course, you might be thinking, well, just bring the self-driving car to a halt anyway, as a precaution, even if it's not a stop sign, but if you ponder this for a moment I think you'll realize that suddenly coming to a halt can have equally undesirable consequences. The car behind you might ram into you. Etc.

For AI self-driving cars, they tend to have five key stages when processing the world around them and taking action. Those five stages are:

- Sensor Data Collection
- Sensor Fusion
- Virtual World Model Updating
- AI Action Plan Updating
- Car Controls Commands Issuance

The self-driving car that is trying to figure out the situation with the stop sign has to first contend with detecting the stop sign. This would primarily involve the visual sensors such as the cameras on the self-driving car. The images collected by the cameras would be examined by the AI, often using a machine learning model to do so.

This could be an artificial neural network that has been trained on thousands and thousands of images of street signs. The images of this particular suspected street sign would be fed into the neural network. The neural network might indicate that it is or is not a stop sign, or might provide an indication with some amount of probability attached to it. In essence, there's say a 65% chance that it is a stop sign. This though needs to be balanced against the aspect that this implies there's a 35% chance it is not a stop sign.

In theory, the sensor data collection should occur and after having done an assessment in this case of the image, the next stage should take place of the sensor fusion. Let’s suppose though that for some reason, the sensor data collection stage won’t give up to the sensor fusion stage.

Perhaps the sensor data collection and analysis stage starts to process the image of the stop sign, and the neural network gets bogged down trying to figure out what the image consists of. Meanwhile, the clock is ticking. After let’s say 10 seconds occur, the neural network finishes its work and reports that it is a stop sign and then releases into the next stage, the sensor fusion stage. Guess what? It’s too late. The AI self-driving car has now proceeded to drive past the sign. Not a good thing.

This is similar to the human freezing problem. The chess player for whatever reason did not finish making his move in the time allotted. In this case, the sensor data collection and analysis did the same thing. It did not finish its efforts in time. This we’ll refer to as a Robot Freezing Problem. Bad stuff indeed.

We can reuse the same reasons of why the human freezing problem occurs, and recast it into the Robot Freezing Problem. Essentially, the same conditions that lead to a human freezing can be generally ascribed to the AI freezing. I don’t want to overly push the analogy since I want to make clear that today’s AI is not the same as the human mind. Today’s AI is much cruder, by far. I am just saying that we can use the human freezing problem to inform us about the nature of the Robot Freezing Problem.

First, it could be that the AI is not aware of the time constraint and so it fails to abide by the need to get something done in time. In our view, the AI must be always watching the clock. It must always be estimating how much time is allowed. It must be “self-aware” as to how much time it is using, including even when it is estimating the amount of time that can be used.

Next, the AI can freeze due to becoming too absorbed in a matter at hand. In the case of the stop sign, the sensor data collection and analysis became overly absorbed and used up the available time. The overarching AI system needs to tell each component how much time it can use, and then must monitor the component. When a component goes beyond its allotted time, the overarching AI has to have some contingencies of what to do, especially if the result coming from the component is now empty or only half-baked.

In terms of people freezing when their minds are blank, the analogy to the Freezing Robot Problem would be a circumstance where suppose the neural network receives an image it has never seen before. There is nothing within to help decide what the sign is. In a blank posture, there should be some kind of contingency of what the stage will do. If it reverts to some other more exhaustive means to try and analyze the image, this could be another wrong move since it might use up more time.

For the circumstance of potential confusion leading to freezing up in humans, imagine if the sensor data analysis conveyed to the sensor fusion that the image is muddled and cannot be ascertained. Meanwhile, suppose the sensor fusion is designed in such a manner that if the sensor data analysis is incomplete, the sensor fusion loops back to the sensor data collection stage and tells it to try harder or try again. This could end-up in confusion and the time runs out.

This same example could also be likened to the infinite loop of choosing between the pawn and the queen on the chessboard. The sensor fusion loops to the sensor data analysis. The sensor data analysis pushes to the sensor fusion and offers the same analysis it had done originally. These two get caught in looping back-and-forth with each other. The third stage, the virtual world model updates stage, just keeps waiting for those two other stage to decide what's going on.

The AI system can also become potentially overwhelmed. Suppose besides trying to decide about the stop sign, meanwhile a pedestrian darts out into the street. And, another car that's behind the self-driving car is menacing the self-driving car by getting overly close to it. And, the internal engine sensors are reporting that the engine is overheating. And, one of the computer processors used by the AI has just failed and the AI needs to shift over to a different processor. A lot of things can be happening in real-time simultaneously. This could
