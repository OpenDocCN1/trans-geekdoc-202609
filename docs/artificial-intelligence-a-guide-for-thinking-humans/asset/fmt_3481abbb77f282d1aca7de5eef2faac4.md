
The trolley problem has been a staple of undergraduate ethics classes for the last century. Most people answer that it would be morally preferable for the driver to steer onto the spur, killing the single worker and saving the group of five. But philosophers have found that a different framing of essentially the same dilemma can lead people to the opposite answer.^()

The trolley problem has recently reemerged as part of the media’s coverage of self-driving cars.^()

In 2016, three researchers published results from surveys of several hundred people who were given trolley-problem-like scenarios that involved self-driving cars, and were asked for their views of the morality of different actions. In one survey, 76 percent of participants answered that it would be morally preferable for a self-driving car to sacrifice one passenger rather than killing ten pedestrians. But when asked if they would buy a self-driving car programmed to sacrifice its passengers in order to save a much larger number of pedestrians, the overwhelming majority of survey takers responded that they themselves would not buy such a car.^()

Some AI ethics researchers have suggested that we give up trying to directly program moral rules for machines, and instead have machines learn moral values on their own by observing human behavior.^()

To my mind, progress on giving computers moral intelligence cannot be separated from progress on other kinds of intelligence: the true challenge is to create machines that can actually `understand` the situations that they confront. As Isaac Asimov’s stories demonstrate, a robot can’t reliably follow an order to avoid harming a human unless it can understand the concept of `harm` in different situations. Reasoning about morality requires one to recognize cause-and-effect relationships, to imagine different possible futures, to have a sense of the beliefs and goals of others, and to predict the likely outcomes of one’s actions in whatever situation one finds oneself. In other words, a prerequisite to trustworthy moral reasoning is general common sense, which, as we’ve seen, is missing in even the best of today’s AI systems.

So far in this book we’ve seen how deep neural networks, trained on enormous data sets, can rival the visual abilities of humans in particular tasks. We’ve also seen some of the weaknesses of these networks, including their reliance on massive quantities of human-labeled data and their propensity to fail in very un-humanlike ways. How can we create an AI system that truly learns on its own—one that is more trustworthy because, like humans, it can reason about its current situation and plan for the future? In the next part of the book, I’ll describe how AI researchers are using games such as chess, Go, and even Atari video games as “microcosms” in order to develop machines with more humanlike learning and reasoning capabilities, and I’ll assess how the resulting superhuman game-playing machines might transfer their skills to the real world.

# Part III

# Learning to Play

# 8

# Rewards for Robots

When the journalist Amy Sutherland was doing research for a book on exotic animal trainers, she learned that their primary method is preposterously simple: “reward behavior I like and ignore behavior I don’t.” And as she wrote in `The New York Times`’ Modern Love column, “Eventually it hit me that the same techniques might work on that stubborn but lovable species, the American husband.” Sutherland wrote about how, after years of futile nagging, sarcasm, and resentment, she used this simple method to covertly train her oblivious husband to pick up his socks, find his own car keys, show up to restaurants on time, and shave more regularly.^()

This classic training technique, known in psychology as operant conditioning, has been used for centuries on animals and humans. Operant conditioning inspired an important machine-learning approach called reinforcement learning. Reinforcement learning contrasts with the supervised-learning method I’ve described in previous chapters: in its purest form, reinforcement learning requires no labeled training examples. Instead, an `agent`—the learning program—performs `actions` in an `environment` (usually a computer simulation) and occasionally receives `rewards` from the environment. These intermittent rewards are the only feedback the agent uses for learning. In the case of Amy Sutherland’s husband, the rewards were her smiles, kisses, and words of praise. While a computer program might not respond to a kiss or an enthusiastic “you’re the greatest,” it can be made to respond to a machine equivalent of such appreciation—such as positive numbers added to its memory.

![FIGURE 22: A Sony Aibo robotic dog, about to kick a robot soccer ball](images/Figure22.jpg)

FIGURE 22: A Sony Aibo robotic dog, about to kick a robot soccer ball

While reinforcement learning has been part of the AI toolbox for decades, it has long been overshadowed by neural networks and other supervised-learning methods. This changed in 2016 when reinforcement learning played a central role in a stunning and momentous achievement in AI: a program that learned to beat the best humans at the complex game of Go. In order to explain that program, as well as other recent achievements of reinforcement learning, I’ll first take you through a simple example to illustrate how reinforcement learning works.

## Training Your Robo-Dog

For our illustrative example, let’s look to the fun game of robot soccer, in which humans (usually college students) program robots to play a simplified version of soccer on a room-sized “field.” Sometimes the players are cute doglike Aibo robots like the one shown in [figure 22](#chapter8.xhtml#fig22). An Aibo robot (made by Sony) has a camera to capture visual inputs, an internal programmable computer, and a collection of sensors and motors that enable it to walk, kick, head-butt, and even wag its plastic tail.

Imagine that we want to teach our robo-dog the simplest soccer skill: when facing the ball, walk over to it, and kick it. A traditional AI approach would be to program the robot with the following rules: Take a step toward the ball. Repeat until one of your feet is touching the ball. Then kick the ball with that foot. Of course, shorthand descriptions such as “take a step toward the ball,” “until one of your feet is touching the ball,” and “kick the ball” must be carefully translated into detailed sensor and motor operations built into the Aibo.

Such explicit rules might be sufficient for a task as simple as this one. However, the more “intelligent” you want your robot to be, the harder it is to manually specify rules for behavior. And of course, it’s impossible to devise a set of rules that will work in every situation. What if there is a large puddle between the robot and the ball? What if a soccer cone is blocking the robot’s vision? What if a rock is blocking the ball’s movement? As always, the real world is awash with hard-to-predict edge cases. The promise of reinforcement learning is that the agent—here our robo-dog—can learn flexible strategies on its own simply by performing actions in the world and occasionally receiving rewards (that is, `reinforcement`) without humans having to manually write rules or directly teach the agent every possible circumstance.

Let’s call our robo-dog Rosie, after my favorite television robot, the wry robotic housekeeper from the classic cartoon `The Jetsons`.^()
