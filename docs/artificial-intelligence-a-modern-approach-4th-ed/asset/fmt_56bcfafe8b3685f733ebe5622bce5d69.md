
Even a little bit of unobservability can cause serious trouble. For example, the braking rule given earlier assumes that the condition `car-in-front-is-braking` can be determined from the current percept—a single frame of video. This works if the car in front has a centrally mounted and hence uniquely identifiable brake light. Unfortunately, older models have different configurations of taillights, brake lights, and turn-signal lights, and it is not always possible to tell from a single image whether the car is braking or simply has its taillights on. A simple reflex agent driving behind such a car would either brake continuously and unnecessarily, or, worse, never brake at all.

We can see a similar problem arising in the vacuum world. Suppose that a simple reflex vacuum agent is deprived of its location sensor and has only a dirt sensor. Such an agent has just two possible percepts: [`Dirty`] and [`Clean`]. It can `Suck` in response to [`Dirty`]; what should it do in response to [`Clean`]? Moving `Left` fails forever if it happens to start in square `A`, and moving `Right` fails forever if it happens to start in square `B`. Infinite loops are often unavoidable for simple reflex agents operating in partially observable environments.

Escape from infinite loops is possible if the agent can randomize its actions. For example, if the vacuum agent perceives [`Clean`], it might flip a coin to choose between `Right` and `Left`. It is easy to show that the agent will reach the other square in an average of two steps. Then, if that square is dirty, the agent will clean it and the task will be complete. Hence, a randomized simple reflex agent might outperform a deterministic simple reflex agent.

### Randomization
We mentioned in [Section 2.3](#Chapter02-03.xhtml#sec2-3) that randomized behavior of the right kind can be rational in some multiagent environments. In single-agent environments, randomization is usually not rational. It is a useful trick that helps a simple reflex agent in some situations, but in most cases we can do much better with more sophisticated deterministic agents.

## 2.4.3 Model-based reflex agents
The most effective way to handle partial observability is for the agent to keep track of the part of the world it can't see now. That is, the agent should maintain some sort of internal state that depends on the percept history and thereby reflects at least some of the unobserved aspects of the current state. For the braking problem, the internal state is not too extensive—just the previous frame from the camera, allowing the agent to detect when two red lights at the edge of the vehicle go on or off simultaneously. For other driving tasks such as changing lanes, the agent needs to keep track of where the other cars are if it can't see them all at once. And for any driving to be possible at all, the agent needs to keep track of where its keys are.

### Internal state
Updating this internal state information as time goes by requires two kinds of knowledge to be encoded in the agent program in some form. First, we need some information about how the world changes over time, which can be divided roughly into two parts: the effects of the agent's actions and how the world evolves independently of the agent. For example, when the agent turns the steering wheel clockwise, the car turns to the right, and when it's raining the car's cameras can get wet. This knowledge about "how the world works"—whether implemented in simple Boolean circuits or in complete scientific theories—is called a transition model of the world.

### Transition model
Second, we need some information about how the state of the world is reflected in the agent's percepts. For example, when the car in front initiates braking, one or more illuminated red regions appear in the forward-facing camera image, and, when the camera gets wet, droplet-shaped objects appear in the image partially obscuring the road. This kind of knowledge is called a sensor model.

### Sensor model
Together, the transition model and sensor model allow an agent to keep track of the state of the world—to the extent possible given the limitations of the agent's sensors. An agent that uses such models is called a model-based agent.

### Model-based agent
[Figure 2.11](#Chapter02-04.xhtml#fig2-11) gives the structure of the model-based reflex agent with internal state, showing how the current percept is combined with the old internal state to generate the updated description of the current state, based on the agent's model of how the world works. The agent program is shown in [Figure 2.12](#Chapter02-04.xhtml#fig2-12). The interesting part is the function `UPDATE-STATE`, which is responsible for creating the new internal state description. The details of how models and states are represented vary widely depending on the type of environment and the particular technology used in the agent design.

×![](images/Fig-14.jpg)
Figure 2.11 A model-based reflex agent.

×![](images/Fig-15.jpg)
Figure 2.12 A model-based reflex agent. It keeps track of the current state of the world, using an internal model. It then chooses an action in the same way as the reflex agent.

Regardless of the kind of representation used, it is seldom possible for the agent to determine the current state of a partially observable environment exactly. Instead, the box labeled "what the world is like now" ([Figure 2.11](#Chapter02-04.xhtml#fig2-11)) represents the agent's "best guess" or sometimes best guesses, if the agent entertains multiple possibilities. For example, an automated taxi may not be able to see around the large truck that has stopped in front of it and can only guess about what may be causing the hold-up. Thus, uncertainty about the current state may be unavoidable, but the agent still has to make a decision.

## 2.4.4 Goal-based agents
Knowing something about the current state of the environment is not always enough to decide what to do. For example, at a road junction, the taxi can turn left, turn right, or go straight on. The correct decision depends on where the taxi is trying to get to. In other words, as well as a current state description, the agent needs some sort of goal information that describes situations that are desirable—for example, being at a particular destination. The agent program can combine this with the model, the same information as was used in the model-based reflex agent, to choose actions that achieve the goal. [Figure 2.13](#Chapter02-04.xhtml#fig2-13) shows the goal-based agent's structure.

×![](images/Fig-16.jpg)
Figure 2.13 A model-based, goal-based agent. It keeps track of the world state as well as a set of goals it is trying to achieve, and chooses an action that will eventually lead to the achievement of its goals.

### Goal
Sometimes goal-based action selection is straightforward—for example, when goal satisfaction results immediately from a single action. Sometimes it will be more tricky—for example, when the agent has to consider long sequences of twists and turns in order to find a way to achieve the goal. Search ([Chapters 3](#Chapter03-00.xhtml), [4](#Chapter04-00.xhtml), and [6](#Chapter06-00.xhtml)) and planning ([Chapter 11](#Chapter11-00.xhtml)) are the subfields of AI devoted to finding action sequences that achieve the agent's goals.
