![](Image00001.jpg)

Artificial Intelligence: Reinforcement Learning in Python

By: The LazyProgrammer

 

[Introduction](#text00001.html#chapter-1)

[How to Succeed](#text00002.html#chapter-2)

[What is Reinforcement Learning?](#text00003.html#chapter-3)

[Where to get the Code](#text00004.html#chapter-4)

[The Multi-Armed Bandit](#text00005.html#chapter-5)

[Tic-Tac-Toe](#text00006.html#chapter-6)

[Tic Tac Toe in Code](#text00007.html#chapter-7)

[Markov Decision Processes](#text00008.html#chapter-8)

[Dynamic Programming](#text00009.html#chapter-9)

[Monte Carlo](#text00010.html#chapter-10)

[Temporal Difference Learning](#text00011.html#chapter-11)

[Function Approximation](#text00012.html#chapter-12)

[Conclusion](#text00013.html#chapter-13)

 

 

# Introduction

 

When people talk about artificial intelligence, they usually don’t mean supervised and unsupervised machine learning.

 

These tasks are pretty trivial compared to what we think of AIs doing - playing chess and Go, driving cars, and beating video games at a superhuman level.

 

Reinforcement learning has recently become popular for doing all of that and more.

 

Much like deep learning, a lot of the theory was discovered in the 70s and 80s but it hasn’t been until recently that we’ve been able to observe first hand the amazing results that are possible.

 

In 2016 we saw AlphaGo beat the world Champion in Go.

 

We saw AIs playing video games like Doom and Super Mario.

 

Self-driving cars have started driving on real roads with other drivers and even carrying passengers, all without human assistance.

 

If that sounds amazing, brace yourself for the future because the law of accelerating returns dictates that this progress is only going to continue to increase exponentially.

 

Yet learning about supervised and unsupervised machine learning is no small feat. To date I have over 16 courses just on those topics alone.

 

And still reinforcement learning opens up a whole new world. As you’ll learn in this book, the reinforcement learning paradigm is more different from supervised and unsupervised learning than they are from each other.

 

So what are we going to talk about in this book?

 

What I noticed in reinforcement learning is that there is a huge gap between what you learn theory-wise and what you do during programming.

 

The theory is super abstract so it’s important to continuously think about how it actually applies to doing AI tasks like controlling a robot or playing a game.

 

So to that end, we are actually going to start this book with a game: slot machines.

 

Slot machines, or the bandit problem, as it’s known in reinforcement learning, will introduce us to an important concept called the explore-exploit dilemma. You want to exploit the slot machine you believe is best, but you need to collect enough data from all the slot machines in order to be confident in that belief.

 

We’ll discuss several techniques for making tradeoffs between exploration and exploitation, including the epsilon-greedy method, UCB1, and a Bayesian online learning technique.

 

Reinforcement learning is all about trying to maximize a goal, or to use the terminology in this course, rewards.

 

In A/B testing, the reward is a click on your advertisements or a conversion in your e-commerce store. It’s easy to see how trying to figure out which slot machine is best is the same as choosing the best advertisement to show, mathematically.

 

\---

 

The next game we’ll play is a simple game by the name of Tic Tac Toe.

 

We’re going to start very low level - and come at it from the perspective of being a first-year computer science student. We’ll ask ourselves the question, “How would I code a game-playing agent that will never lose tic-tac-toe?”

 

As you probably already know, there are only a very small set of rules that you need to follow in Tic Tac Toe in order to never lose.

 

After going at it the naive way, we’ll introduce the reinforcement learning way of doing things, and code an agent from scratch that will train itself to play tic-tac-toe.

 

\---

 

In the following sections, we’ll introduce the central framework for solving reinforcement learning problems, known as the Markov Decision Process or MDP.

 

MDPs will allow us to formalize and abstract all the concepts we learned about in tic-tac-toe, so that they can be applied to any game or scenario in the real-world.

 

Then we’ll introduce 3 separate but related techniques for solving MDPs: dynamic programming, Monte Carlo methods, and temporal difference learning.

 

These 3 techniques look very similar so I think what you’ll find interesting is that the hard part is actually differentiating between the 3.

 

\---

 

In the last section, we’ll do a little bit of a teaser and introduce what are known as approximation methods.

 

The disadvantage of the previous 3 solutions to reinforcement learning is that they don’t scale to large state spaces, or in other words, environments where you can find yourself in a large number of different states.

 

The solution to this problem is to use approximation methods, and as you might have guessed, this is where deep learning comes into play, since neural networks are very good “function approximators”.

 

While we won’t explicitly cover deep learning in this course, this course provides all the techniques required to “plug-in” your deep neural networks into your reinforcement learning agents.

 

Without the theory from this course, doing something like deep reinforcement learning wouldn’t make much sense.

 

\---

 

By the end of this book, you’ll understand the framework of reinforcement learning, how the 3 solutions work and the differences between each one, and how to use approximation methods to scale them up.

 

When we talk about approximation methods you’ll understand exactly how you can “plug in” deep neural networks so that when we start talking about deep reinforcement learning (in a later book or course) we can just continue where we left off.

 

So if you are interested in deep reinforcement learning but you don’t know where to start or even what the prerequisites are, this is the book you want to read.

 

# How to Succeed

 

In this chapter I’m going to give you tips on how to navigate this book and how to maximize your returns.

 

Like other online resources, you don’t have exams or grades, so you really have to be the kind of person that takes initiative and is proactive about learning.

 

That means understanding all the equations that get written down, and if there’s a derivation: making sure you understand each step and being able to do the derivation independently.

 

That means writing all the code yourself and trying to do that before looking at my code. You should consider my code to be the “answer” to the problem, not just something you look at without thinking about the problem first.

 

I think people that have taken my other courses and read my other books understand this but from time to time I still see students get confused about how exactly to practice.

 

## Prerequisites

 

Firstly, if you did not know there were prerequisites to this book. Stop right now. You have already failed.

 

This is the #1 reason I see people fail, or get mad at me for making my course/book “too hard”.

 

To reiterate: in order to understand this course, you need to have a good handle on undergraduate-level calculus, probability, Markov models, linear machine learning models, and gradient descent. Of course you must know how to implement all these things in code as well.

 

If you didn’t read these from the product description, and you think reinforcement learning is going to be as easy as how to make your own ads on Google AdWords, you are at the very bottom of the totem pole.

 

If you did read the prerequisites in the course description, but felt confident enough in yourself that you’d “figure it out along the way” due to past experience in technical subjects, then you may possibly be a half step higher on the totem pole.

 

This is all from my students’ experiences, I didn’t just make this up. If you did advanced math in college 20 years ago, it doesn’t count. If you watched some lectures about probability on YouTube for 20 minutes, it doesn’t count. You don’t just need a short review. You need tough technical concepts etched into your mind.

 

## Practice by Coding from Scratch

 

Machine learning isn’t like taking a physics course, there aren’t 20 practice problems at the end of the chapter for you to do.

 

The nice thing about machine learning is that it automatically self-checks.

 

Either the code you wrote runs, or it doesn’t. If it runs, that’s a good first step.

 

Either it behaves as expected, or it doesn’t. If it does behave as expected, that means what you wrote is good and it’s working.

 

Debugging is part of programming. You should be a good debugger and not give up the instant your code throws an error.

 

It’s all part of the process.

 

People think they should be able to do something in an hour when in reality it should take an intelligent person all night or maybe even days.

 

So keep that in mind: everything we do automatically self-checks. Either the code you write works, or it doesn’t. Strive to make it work on your own.

 

Remember that the code in the Github repo (to be discussed) has already been verified to work, so check your work against that.

 

It’s even possible for your code to be better!

 

You absolutely must write the code and do as much of it on your own as you can, ideally working off of the pseudocode from the theory / pseudocode only.

 

The difference between this and my other machine learning courses is that it’s going to feel like we’re doing the same thing over and over again.

 

This is opposed to, for example, my supervised machine learning class where you learned decision trees, Naive Bayes, k-nearest neighbor, and the perceptron. Those were 4 distinct algorithms.

 

In this book all the algorithms look alike, so the real challenge is going to be telling them apart.

 

Understanding the differences between each method and their advantages and disadvantages is the key to this course.

 

You’ve heard me say in previous courses that “all data is the same”.

 

I think it’s pretty easy to achieve this level of perspective in machine learning.

 

When we talk about supervised learning and unsupervised learning, we always deal with the inputs X and the targets Y.

 

We don’t need to specify what X is or what Y is, and you still understand what I’m talking about.

 

You already know that X can represent any feature, that could be age, weight, height, number of pages visited in your ecommerce store, a DNA sequence, etc.

 

Supervised and unsupervised learning works for all different fields, finance, biology, online advertising, and more.

 

We don’t need to specify what we’re talking about - saying X and Y is good enough, because the same algorithms work no matter what the data represents.

 

So we say “all data is the same”. The question you might have is, “does this apply to reinforcement learning as well?”

 

I think the answer is that eventually it will, but it probably won’t at first.

 

Reinforcement learning is more difficult because the interface to the learning agent is much more broad than just features and targets or Xs and Ys.

 

However once you get used to the idea of taking an environment and thinking about how you can encode states, actions, and rewards, you’ll get better and better at abstracting these concepts.

 

So in the future you won’t need to think in terms of specific problems like Tic-Tac-Toe or Gridworld, you’ll instead think in terms of abstract entities like states, actions, and rewards and that instinct will become more automatic over time.

 

In Deep Learning especially, experience has shown me that a lot of people want to jump into Deep Learning because it’s popular at the moment, but they have no idea what the prerequisites are, so they “don’t know what they don’t know”.

 

I have 2 goals:

 

(1) you end the book “knowing what you don’t know”, and

 

(2) “knowing what you need to know, in order to know the things you want to know”.

 

So perhaps your goal is to build an AI that can play Super Mario. This course is going to fill in the gaps, not all the way to that point, but very close. If you think you’ll be programming an AI for Super Mario tomorrow, then you are currently in a state of “you don’t know what you don’t know”. But by the end of the book (1) and (2) will be true.

#  

 

# What is Reinforcement Learning?

 

In this chapter we are going to answer the question, “what is reinforcement learning?”

 

How is it different from supervised and unsupervised learning?

 

What are its applications?

 

We talked a little bit about these things in the introduction and in this chapter we are going to expand on those things.

 

The first thing you’ll notice is how different reinforcement learning is from supervised and unsupervised learning.

 

With supervised and unsupervised learning, we always imagine the same interface, which we’ve modeled around sci-kit learn.

 

For a supervised learning interface, we usually have the functions fit(X,Y), which takes in the input samples X and the targets Y, and predict(X), which takes in input samples X and tries to accurately predict Y.

 

`class SupervisedModel:`

`def fit(X, Y): ...`

`def predict(X): ...`

 

For an unsupervised learning interface, we usually just have a fit(X) function which only takes in some input samples X. Remember that there are no targets in unsupervised learning.

 

Sometimes we have a transform(X) function which takes in some input samples X and turns it into a different representation that we call Z. PCA, Autoencoders, and Restricted Boltzmann Machines are examples of algorithms we’ve seen that can do that.

 

`class UnsupervisedModel:`

`def fit(X): ...`

`def transform(X): ... # sometimes`

 

In contrast, methods like k-means clustering and Gaussian Mixture Models have a fit() function but they don’t transform data. Instead, the parameters of the fitted model tell us something about the data, like which cluster a data point belongs to, and what the variance of that cluster is.

 

The common theme with both of these is that the interface to these is training data. You take some training data, either X & Y, or just X, and you call a fit function.

 

In the case of supervised learning, you can then make predictions on future data.

 

This by itself can be useful. Imagine you’ve written an app that can scan a photo you take at the supermarket, classify what you took a photo of, and then return nutritional information about it.

 

But reinforcement learning is different. Reinforcement learning can guide an agent for how to act in the real world .

 

So the interface to a reinforcement learning agent is much more broad than just data, it’s the entire environment.

 

That environment can be the real world, or it can be a simulated world like a video game.

 

As an example, you could create a reinforcement learning agent to vacuum your house. Then it would be interacting with the real world. You could create a reinforcement learning agent learn to walk. That would also be interacting with the real world.

 

You can be sure that the military is interested in such technologies - they want reinforcement learning agents that can replace soldiers. Not only to walk, but fight, diffuse bombs, and make important decisions while they are out on a mission.

 

So you see now why reinforcement learning is such a big leap from basic supervised and unsupervised learning.

 

The interface isn’t just data, but it could potentially be the entire world.

 

The big leap isn’t that just the interface with the AI is way more broad, but that reinforcement learning algorithms train in a completely different way as well.

 

You’ll see quite a lot of references to psychology, and indeed reinforcement learning can be used to model behavior.

 

Reinforcement learning algorithms have objectives in terms of a goal . This is different from supervised learning, where the objective is to get good accuracy or to minimize a cost function.

 

Reinforcement learning algorithms get feedback as the agent interacts with its environment. So feedback signals, or as we like to call them, “rewards”, are given automatically to the agent by the environment.

 

This is much different from supervised learning where it can be extremely costly and time-consuming to obtain hand-labeled data.

 

So in this way reinforcement learning is very different from supervised learning. Supervised learning requires a hand-labeled dataset, reinforcement learning learns automatically from signals in the environment, so there is no need for hand-labeled data.

 

\---

 

Let’s expand on this idea of a goal.

 

Phrasing our objective in terms of goals allows us to solve a much wider variety of problems.

 

The goal of AlphaGo is to win Go.

 

The goal of a video game AI is to either get as far as possible in the game or achieve a high score.

 

What’s interesting is when you consider animals and specifically humans.

 

Evolutionary psychologists have said that our genes are “selfish” and all they want to do is make more of themselves.

 

This is really interesting because just like AlphaGo, we’ve found many “roundabout” and unlikely ways to achieve this. Experts commented that AlphaGo used some surprising and unusual techniques.

 

For example, you might have a desire to be rich and make lots of money. But have you ever wondered why you feel that way?

 

Perhaps those with the specific set of genes that are related to the desire to be rich, ended up being more prominent in our gene pool due to natural selection.

 

Perhaps having lots of money led to better healthcare and social status, which then helped your genes to maximize their central goal, which was to make more of themselves.

 

Although a number in your bank account has no direct relationship in terms of physical laws to how long you are going to live, it’s a novel solution to the problem.

 

“Desiring and successfully earning money” is just a random example off the top of my head, but you can replace that with any trait you want, like “being healthy and strong”, or “having strong analytical skills”.

 

Knowing the exact factors is a social scientist’s job, we’re just interested in the fact that there is only one main goal that we want to maximize, and various novel ways of achieving it.

 

And these things are always fluctuating in time. At one point in history, seeking as much sugar as possible would give you energy and help you survive. Today, we keep that trait, because evolution is slow, but in today’s world that trait actually kills us.

 

Our genes’ method of maximizing their reward is through mutation and natural selection, which is slow, but an AI’s method of maximizing its reward is reinforcement learning, which is fast.

 

\---

 

Now let’s get into some technical detail.

 

Of course you never sense the entire world all at once, even humans don’t do this. We have sensors which feed signals to our brain from the environment.

 

These signals don’t even tell us everything about the room we’re in, much less the world.

 

So we necessarily have limited information about our environment, as do robots with limited numbers and types of sensors.

 

The measurements we get from these sensors - sight, sound, and touch - make up a “state”.

 

In this course we’ll only look at environments where there are a small finite number of states, but of course it’s possible to consider environments with an infinite number of states too.

 

\---

 

Let’s do a simple example. Consider a tic-tac-toe board where we don’t care about who wins, we just want to put X’s and O’s on the board. The board starts out as empty and we continue to add either X’s or O’s until the board is full.

 

Ex:

 

`+---+---+---+`

`| x | o | x |`

`+---+---+---+`

`| x | x | x |`

`+---+---+---+`

`| x | o | o |`

`+---+---+---+`

 

If you don’t know how tic-tac-toe works, you can do a google search and play the game yourself in the browser.

 

Remember that tic-tac-toe boards are 3x3 boards. What is the total number of states in this environment?

 

Think about this for a minute and then come back to the book.

 

\---

 

Since we’re not considering a tic-tac-toe game where there is a winner after you get 3 X’s or 3 O’s in a row, this problem is very simple.

 

Each location on the board has 3 possible states: empty, X, or O.

 

There are 9 locations in the board.

 

So the total number of states is 3^9.

 

\-----

 

Let’s recap the terms we’ve talked about so far - there are 3 of them and possibly more that I snuck in.

 

The 3 important ones are:

 

Agent : This is the thing that senses the environment and the thing we’re trying to code intelligence and learning into.

 

Environment : This is the real world or the simulated world that your agent lives in.

 

State : These are different configurations of the environment that the agent can sense.

 

\---

 

There are a couple more things to define in reinforcement learning that are central to the subject.

 

First, there is a concept of reward .

 

This is what differentiates reinforcement learning algorithms from other kinds of machine learning algorithms.

 

An agent will try to maximize not only its immediate reward but future rewards as well.

 

Often, reinforcement learning algorithms will find novel ways of accomplishing this.

 

I’m not a Go player myself, but we’ve heard that the AlphaGo program learned unique and unpredictable strategies that led to its beating a world champion at Go.

 

These are things that aren’t intuitive to humans, but reinforcement learning algorithms can automatically figure them out.

 

One potentially dangerous aspect of this is the idea of unintended consequences. We’ve all heard about the idea that an AI could potentially wipe out humanity if it decides that is the best thing for us.

 

Imagine you program your AI to minimize the number of human deaths, and then it decides that, since humanity is going to grow exponentially and hence more people are going to die as well, that it would be better to destroy everyone now in order to minimize more dying in the future.

 

So there is some danger of unintended and dangerous side effects for AIs that are interacting with the real-world.

 

To give you a more low-level example of how and why rewards should be programmed intelligently, think of a robot trying to solve a maze.

 

A reasonable goal might be to simply solve the maze. If you solve the maze, you get a reward of 1, otherwise you get a reward of 0.

 

With this reward structure, it’s possible for a robot to just implement a random strategy and eventually solve the maze.

 

Because we never told it that it should try to solve the maze efficiently, then making random movements until the maze is solved still gets you the reward.

 

Now imagine that we give a reward of -1 for every step the AI takes in the maze. Now the AI has incentive to solve the maze using the least number of steps, and so it will tend to find a more efficient solution this way.

 

We’ll demonstrate this in code later in the book.

 

Notice how a negative reward is like a penalty, which it is. Reward is just the term we always use, whether it be positive or negative. It tells you how good or bad you’re doing.

 

Note that the reward is always a real number.

 

\---

 

So far we’ve defined these terms: agent, environment, state, and reward.

 

The last important concept we need to talk about is actions .

 

Actions are what the agent does in its environment. For example, if you’re a 2-D video game character, your actions might be up, down, left, right, and jump.

 

This is an example of a finite set of actions.

 

There are also examples of an infinite set of actions but we won’t discuss that in this book.

 

The last 3 things we talked about are often thought about as a triple: You’re in a state, you take an action, and you get a reward.

 

We call these (S,A,R) or (state,action,reward) triples.

 

In reinforcement learning, timing is an important concept as well, since every time you play a game you get a sequence of states, actions, and rewards.

 

Within this framework, you start in a state S(t), you take an action A(t), but you receive a reward of R(t+1).

 

So the reward you get always results from the state and action that you took at the previous time.

 

This action also results in you being in a new state, S(t+1).

 

So another important triple is (S(t), A(t), S(t+1)). Usually we just denote this as (s, a, s’).

 

\---

 

That’s reinforcement learning in a nutshell.

 

You program the agent to try to be intelligent.

 

The agent interacts with its environment by being in a state, taking an action based on that state, which then brings it to another state.

 

The environment gives the agent a reward, either positive or negative, when it arrives in the next state.

 

This section is just definitions. In later sections, we’ll dive deeper into the theory and implement code.

#  

 

# Where to get the Code

 

In this section I am going to show you where to get the code for this course.

 

All of the code for my machine learning courses are in my github repo:

 

[https://github.com/lazyprogrammer/machine\_learning\_examples](https://github.com/lazyprogrammer/machine_learning_examples)

 

The relevant folder is “rl”

 

The command to download the code is “git clone” and then my Github URL, which you can copy and paste from the repo homepage.

 

`git clone git@github.com:lazyprogrammer/machine_learning_examples.git`

 

I would recommend using the SSH url so that you don’t need to type in your github password every time you do anything.

 

Make sure you periodically check for updates or run “git pull” so that you have the latest version.

 

All of the data in this course will be mentioned in the relevant section, if needed.

 

If you don’t know how to use Git, or you need help setting up your development environment with the right Python libraries, you’ll want to check out the environment setup lecture on my YouTube channel: [https://www.youtube.com/watch?v=Fm1oXw4hZj0](https://www.youtube.com/watch?v=Fm1oXw4hZj0) .

 

At this stage I suspect that these things are probably trivial for you. This book is designed with that in mind.

 

I always recommend my students try to code for themselves, but if you get stuck or you need help, then the code in my github repo has already been verified to work.

 

So you can always check your code against that.

 

Occasionally people ask me “what are the practice activities for this book?” - the practice is implementing the algorithms you learn about.

 

The point of that is because it’s one thing to watch the theory lectures and understand the concepts at a high level, it’s another thing entirely to understand them so well that you can implement them in code without any reference.

 

This is what computer scientists do, so that’s the approach you should take.

 

Writing all the code yourself in this course is especially important here.

 

The thing I’ve found with reinforcement learning algorithms is that at a high level they all look almost exactly the same .

 

So if all you do is sit there and read the book straight through, you’ll be confused and you’ll probably wonder why I taught you the same thing 3 times.

 

I recommend you do not take this approach, because you won’t get anything out of it.

 

So take initiative, be proactive. Those are the kinds of people this book is for.

 

Only by trying to write the code yourself and struggling through the details will you really start to understand what is being taught.

#  

 

# The Multi-Armed Bandit

 

## Problem Setup and the Explore-Exploit Dilemma

 

In this section of the book we are going to re-examine the multi-armed bandit problem, which you first saw in my course on Bayesian Machine Learning and A/B testing.

 

If you haven’t taken that course, don’t worry too much, since we are going to fully cover the problem in this book.

 

Suppose you go to a casino and you have a choice between 3 slot machines. Each slot machine can give you a reward of 0 or 1, so it’s like a coin toss for now.

 

This is called the multi-armed bandit problem because when you play a slot machine you have to pull on the arm of the machine, and they are bandits because they’re taking your money.

 

The win rate of each of the slot machines is unknown. So for example, they might be 0.1, 0.3, and 0.5. But you wouldn’t know that, you would only be able to discover it by collecting data.

 

Now your goal at the casino is obviously to maximize your winnings. If you were psychic and could determine using your psychic powers which machine had the highest win rate, you would play only that machine, and that’s how you would maximize your winnings.

 

But since you don’t know the win rates, you need to estimate them by collecting data, and that means you have to play each of the machines.

 

This is where the dilemma comes in.

 

You need to collect lots of data for your estimates to be accurate. But if you collect lots of data then you’re going to spend lots of time playing suboptimal bandit arms.

 

So you need to balance between trying to maximize your earnings and trying to obtain accurate measurements of each bandit’s win rate, since in order to maximize your earnings you need to accurately know that information.

 

In traditional A/B testing, what you would do is predetermine ahead of time the number of times you need to play each bandit in order to obtain statistical significance.

 

The number of times you need to play is dependent on a number of things, such as the difference in win rates between each bandit. If the difference is bigger, you need less samples, but if the difference is smaller, you need more samples.

 

This is kind of silly because you don’t know the difference before you start the test, so that’s one of the disadvantages of traditional A/B testing.

 

An important rule of A/B testing is that you do not stop your test early. So if you decided beforehand that you need to play each bandit 1000 times, and by the time you get to 500, you’ve calculated 90% win rate for one bandit, and 10% win rate for another bandit, you’re not allowed to stop.

 

Luckily, we don’t care about statistical significance in this course so we don’t need to follow any of those rules.

 

\---

 

It’s interesting that humans behave the opposite.

 

Suppose you win 2/3 times on one bandit arm, and 0/3 times on another bandit arm.

 

You would probably feel a strong urge to only play the 2/3 bandit from this point forward, even though there is a high probability the other bandit could still be better.

 

If I were to ask you in a statistical way - if you think 2/3 and 0/3 give you accurate measurements, you would say “no way”!

 

As a data scientist you know that there’s a low probability that the first bandit has an actual win rate of 67% and a low probability that the second bandit has an actual win rate of 0%.

 

You know this because 3 is a very tiny sample size.

 

And yet if you are playing slot machines you feel compelled to believe that the first bandit is better.

 

In the coming sections, we’ll learn about algorithms that will systematically make a trade-off between exploration and exploitation.

 

These will allow us to improve upon these 2 poor solutions to the problem, which are human emotion and traditional A/B testing.

 

 

## The Epsilon-Greedy Strategy

 

The first solution to the explore-exploit dilemma is called the epsilon-greedy strategy. This is the most important because it’s the one we’ll be using throughout the course (although any of the other techniques can be equivalently applied).

 

We like it because it’s simple.

 

The way it works is this.

 

We use a small number called epsilon to be the probability of exploration.

 

Typical values for epsilon are 10% or 5%.

 

Here’s some pseudocode that does this.

 

`if random() < eps:`

`play random arm`

`else:`

`choose current best arm`

`update estimate for the arm played (i.e. avg = sum / N)`

 

At each round we generate a random number. If the random number is less than epsilon, we explore, meaning we just choose an arm at random. If the random number is greater than epsilon, we exploit, meaning we choose the arm that has the best maximum so far .

 

So it should be clear from this that eventually, you’ll learn which arm is the true best, even though your initial guesses might be wrong, since every arm always has the chance to get updated.

 

\---

 

In the long run, epsilon-greedy allows us to explore each of the arms an infinite number of times.

 

The problem with this however, is that eventually you’ll get to a point where you’re still exploring when you don’t really need to explore anymore.

 

So if epsilon is 10%, then you’ll still spend 10% of the time choosing suboptimal arms.

 

An A/B test could also be useful here, where you could do a test at a predetermined time to check for statistical significance. If you find statistical significance, you could set epsilon to 0, and effectively you’re only doing the greedy part.

 

However, we’ll see better ways to adapt to what we’ve learned in the near future.

 

 

## Updating a Mean

 

Let’s assume that our rewards aren’t just coin tosses, so we don’t just need to store the number of successes and failures.

 

The general method for solving this problem is to use the mean.

 

This works for coin tosses too, since if you add up all the 0s and 1s you get, and divide by N, you arrive at the maximum likelihood probability of getting a 1.

 

So how do we calculate the sample mean of a random variable?

 

We know that it’s the total sum divided by the number of samples.

 

`Xmean(N) = sum[i=1..N]{ X(i) } / N`

 

What’s the problem with this equation?

 

The problem with this equation is that it requires is to store all N elements in order to calculate the mean.

 

Is there a way to make that calculation more efficient?

 

Indeed there is.

 

The trick is, the mean at the Nth sample can be calculated from the mean at the (N-1)th sample.

 

`Xmean(N) = (1 - 1/N)Xmean(N-1) + (1/N)X(N)`

`Xmean(N) = Xmean(N-1) - (1/N)[Xmean(N-1) - X(N)]`

 

If you don’t see how this works right away try deriving it yourself on paper.

 

So this equation allows us to calculate the mean in a computationally efficient way.

 

Remember this form of the update equation, it’ll be very important throughout the rest of the book.

 

 

## Comparing Different Epsilons in Code

 

In this section we are going to implement epsilon-greedy in code, and demonstrate the effect of different settings of epsilon.

 

If you don’t want to try to code this yourself, although I highly encourage you to do so, the relevant file in the course repo is comparing\_epsilons.py

 

`import numpy as np`

`import matplotlib.pyplot as plt`

` `

`# represents one bandit arm`

`class Bandit:`

`def __init__(self, m):`

`self.m = m # true mean`

`self.mean = 0`

`self.N = 0`

` `

`# simulates pulling the bandit’s arm`

`# is a Gaussian with unit variance`

`def pull(self):`

`return np.random.randn() + self.m`

` `

`# this is the update equation we just learned`

`def update(self, x):`

`self.N += 1`

`self.mean = (1 - 1.0/self.N)*self.mean + 1.0/self.N*x`

` `

` `

`# N = number of times we play`

`# m1, m2, m3 = mean rewards for the 3 arms`

`# eps = epsilon for the epsilon greedy strategy`

`def run_experiment(m1, m2, m3, eps, N):`

`bandits = [Bandit(m1), Bandit(m2), Bandit(m3)]`

` `

`data = np.empty(N)`

`for i in xrange(N):`

`# epsilon greedy`

`p = np.random.random()`

`if p < eps:`

`j = np.random.choice(3)`

`else:`

`j = np.argmax([b.mean for b in bandits])`

`x = bandits[j].pull()`

`bandits[j].update(x)`

` `

`# for the plot`

`data[i] = x`

`cumulative_average = np.cumsum(data) / (np.arange(N) + 1)`

` `

`# plot moving average reward`

`plt.plot(cumulative_average)`

`plt.plot(np.ones(N)*m1)`

`plt.plot(np.ones(N)*m2)`

`plt.plot(np.ones(N)*m3)`

`plt.xscale('log')`

`plt.show()`

` `

`for b in bandits:`

`print b.mean`

` `

`return cumulative_average`

` `

`if __name__ == '__main__':`

`c_1 = run_experiment(1.0, 2.0, 3.0, 0.1, 100000)`

`c_05 = run_experiment(1.0, 2.0, 3.0, 0.05, 100000)`

`c_01 = run_experiment(1.0, 2.0, 3.0, 0.01, 100000)`

` `

`# log scale plot`

`plt.plot(c_1, label='eps = 0.1')`

`plt.plot(c_05, label='eps = 0.05')`

`plt.plot(c_01, label='eps = 0.01')`

`plt.legend()`

`plt.xscale('log')`

`plt.show()`

` `

` `

`# linear plot`

`plt.plot(c_1, label='eps = 0.1')`

`plt.plot(c_05, label='eps = 0.05')`

`plt.plot(c_01, label='eps = 0.01')`

`plt.legend()`

`plt.show()`

 

 

## Optimistic Initial Values

 

In this lecture we are going to look at another way to solve the explore-exploit dilemma called the “optimistic initial values” method.

 

Again it’s very simple.

 

Suppose you knew the true mean of the bandits was much less than 10. The idea is you want to pick an high ceiling for your initial estimate of the bandit mean, and then do your update based on that.

 

E.g.

 

`Xmean(0) = 10`

 

We say this is “optimistic” because the initial value for the sample mean is too good to be true.

 

Since it’s too good to be true, the only thing that can ever happen is it will go down.

 

So if the mean is 1, then as I collect more values, the sample mean is going to converge to 1.

 

In fact, eventually, all the means will eventually settle into their true values, at which point we’ll just be exploiting.

 

But it should be clear that this helps exploration as well.

 

If you haven’t explored a bandit that much, then it’s sample mean is going to be very high, due to the initial setting. In fact it’s going to be higher than everything else, which means you’ll be forced to explore it.

 

So in the main loop, all you need to do is perform the greedy strategy, but using these optimistic means.

 

There are only 2 simple changes we need to make to the epsilon-greedy code to make this work.

 

First, we change the initial setting of the mean to 10.

 

Second, we remove the epsilon part and just do the greedy part.

 

`class Bandit:`

`def __init__(self, m):`

`self.m = m`

`self.N = 0`

`...`

`for i in xrange(N):`

`# optimistic initial values`

`j = np.argmax([b.mean for b in bandits])`

`x = bandits[j].pull()`

`bandits[j].update(x)`

` `

In the code we compare the epsilon-greedy strategy with epsilon=10%, to the optimistic initial value strategy.

 

If you don’t want to try to code this yourself, although I highly encourage you to do so, the relevant file is optimistic\_initial\_values.py

 

\[run the code yourself before moving on!\]

 

So it looks like we do a lot better with optimistic initial values compared to epsilon-greedy. With epsilon-greedy we always end up doing sub-optimally in the long run, but you can see we’re very close to 3 (the max reward) with the optimistic strategy.

 

 

## UCB1

 

In this section we are going to look at yet another method for solving the explore-exploit dilemma.

 

These are all important parts of the reinforcement learning literature, though it might seem we’re being a little too thorough.

 

The main idea behind UCB1 is confidence bounds.

 

Intuitively, you know that if you collect 10 samples and take the mean, this is not as accurate as when you collect 1000 samples and take the mean.

 

If you were to draw a confidence bound around each mean, you would draw a much wider bound around the 10-sample mean, and a much skinnier bound around the 1000-sample mean.

 

In statistics, there is a bound called the Chernoff-Hoeffding bound, and it says that our confidence bound changes exponentially with the number of samples we collect.

 

`P(|Xmean - true_mean| >= eps) <= 2exp(-2*(eps**2)*N)`

 

The bound looks complicated but it becomes less complicated if you read it out slowly.

 

It says that “the probability that the absolute difference between the sample mean and the true mean, is greater than or equal to epsilon - is less than 2 x the exponent of -2(eps^2)N”

 

Where N is the number of samples collected, and epsilon is just an arbitrary small number.

 

The details are outside the scope of this course, but the algorithm is just as simple as all the others we’ve looked at.

 

The idea is, we take the upper confidence bound to be the regular sample mean + sqrt(2 \* ln(N) / Nj).

 

`Xmean= Xmean(j)+2ln(N)/Nj`

 

This is equivalent to “choosing” an epsilon equal to the square root and everything inside it.

 

So let’s talk about what all these symbols mean.

 

`Xmean(j) = regular sample mean of jth bandit arm`

 

N is the total number of times you’ve played the bandits.

 

Nj is the total number of times you’ve played the jth bandit.

 

Now how do we use this formula?

 

Well the idea is similar to the optimistic initial values method.

 

We use the greedy strategy only, but what we’re greedy with respect to is not just the sample mean, but the upper confidence bound of the sample mean.

 

The question is, why does this work?

 

Well the confidence bound seems to be the ratio of 2 things: N, which is the total times you’ve played any bandit, and Nj, the total number of times you’ve played bandit j.

 

So if you’ve played some other bandits many times, but Nj is small, then this ratio ln(N)/Nj is going to be large, which would make the upper confidence bound higher, which would cause you to select this bandit to play.

 

At the same time, if Nj is large, then the ratio is small, at which point the upper confidence bound will shrink.

 

But one key point about this ratio is that the top part grows with the logarithm of N. Which means it’s going to grow more slowly than Nj eventually.

 

That means, as you play all the bandits more and more, the upper confidence bounds will shrink, and you’ll only be using the sample means, which is ok since you’ve collected lots of data.

 

So this also converges to a purely greedy strategy.

 

Let’s look at some pseudocode so we can understand how this works better.

 

It’s essentially just as simple as the optimistic initial values method. We’re just replacing the formula that goes into the argmax, which is now the upper confidence bound.

 

`for n=1..N:`

`j = argmax[j’]{ bandit[j’].mean + sqrt(2*ln(n) / n_j) }`

`pull bandit j`

`update bandit j`

 

Note that there is a small problem where this formula doesn’t work if n\_j is 0. To fix that, you can simply add a small number to the denominator.

 

If you don’t want to try to code this yourself, the relevant file in the course repo is ucb1.py. At the very least, try running it so you can observe the results.

 

 

## Bayesian / Thompson Sampling

 

In this lecture we are going to discuss one of my favorite ways to solve the explore-exploit dilemma, using the Bayesian method.

 

You might also see this technique called Thompson sampling in some sources.

 

To motivate the idea behind the Bayesian method, we want to look at confidence intervals or confidence bounds again.

 

We know intuitively that a sample mean calculated from 10 samples, is not as accurate as a sample mean calculated from 1000 samples.

 

We can use the central limit theorem to say that the confidence interval is “approximately Gaussian” with true mean equal to the expected value of the random variable, and variance equal to the original variance / N.

 

Xmean ~ Normal(true\_mean , true\_variance/N)

X ~ Normal(true\_mean , true\_variance)

 

The reason that Xmean has a distribution is because it’s the sum of random variables. And as you know any function of random variables is also a random variable.

 

The Bayesian paradigm extends this idea even further. Instead of the true mean (we’ll call it mu) being fixed, mu becomes a random variable too.

 

The basic idea behind the Bayesian paradigm is that data is fixed , and parameters are random .

 

In the Bayesian paradigm, parameters have distributions, and what we would like to know, is the distribution of the parameter given data.

 

This makes a lot of sense I hope.

 

Given some data, I should be able to come up with a distribution based on the data that is more accurate than if I didn’t have the data. We call this the posterior distribution:

 

p(param | data)

 

In the Bayesian paradigm, the key tool is Bayes rule, and so we can flip the posterior and compute it from the likelihood and the prior.

 

Likelihood = p(data | param)

Prior = p(param)

 

One disadvantage of the Bayesian method is that we need to choose the prior ourselves, and this can sometimes have a non-negligible effect on the posterior.

 

p(param | data) = p(data | param)p(param) / p(data)

 

p(param | data) proportional to p(data | param)p(param)

 

Since p(data) = integral over p(data | param)p(param)dparam is constant.

 

There are some problems with this formula. One is that it’s very general, in the sense that a differential equation is very general.

 

The integral in the denominator can’t always be found, so we need to resort to mathematical tricks in order to make this work out. And it doesn’t always work out.

 

Luckily, there are a special set of pairs of distributions, such that the posterior will have the same distribution as the prior.

 

These are called conjugate priors .

 

Let’s do a short example to see how the conjugate prior method can be applied to click-through rates.

 

We know that click-through rates are like coin tosses, so they have a Bernoulli likelihood.

 

If you look up on Wikipedia what the conjugate prior for a Bernoulli likelihood is, you’ll find that it’s the Beta distribution.

 

The Beta distribution is always between 0 and 1, which makes sense, and it has 2 parameters, a & b.

 

Knowing this, we can set up our calculation for the posterior.

 

The likelihood can be written as a product, since each coin toss is independent.

 

Let’s call our parameter, probability of the coin toss being 1, r. Then:

 

r ~ Beta(a,b)

 

Likelihood:

 

p(X | r) = prod\[i=1..N\]{ r ^ 1(x(i)=1) (1 - r) ^ 1(x(i)=0) }

 

Remember, the 1(.) function is defined as: 1(true) = 1, 1(false) = 0.

 

The prior is just the PDF of the Beta, which you can simply write down verbatim.

 

p(r) = \[1/B(a,b)\] r ^ (a-1) (1- r) ^ (b-1)

 

To find the posterior, we need to combine the likelihood and the prior and solve for the posterior.

 

p(r | X) proportional to prod\[i=1..N\]{ r ^ 1(x(i)=1) (1 - r) ^ 1(x(i)=0) } \[1/B(a,b)\] r ^ (a-1) (1- r) ^ (b-1)

 

We can drop the Beta function out of the proportionality since it gets absorbed into the normalization constant.

 

The key here is to see that the posterior also takes the form of a Beta distribution, so we can infer what the new parameters of the new Beta are.

 

p(r | X) ~ Beta(a’, b’) where:

 

a’ = a + sum\[i=1..N\] { 1(x(i)=1) }

b’ = b + sum\[i=1..N\] { 1(x(i)=0) }

 

So the new a is just the old a + the # of times X was a 1. The new b is just the old b + the # of times X was a 0.

 

a'=a+#1's

b'=b+#0's

 

There is a script from my A/B testing class that you can run in order to demonstrate how the posterior gets updated as you collect more samples. (Same repository as this class).

 

The file is in the folder ab\_testing and its name is demo.py.

 

We start with the settings a0 = 1 and b0 = 1, which is equivalent to the uniform distribution, which is a suitable prior since we don’t know anything about the true click-through rate prior to starting.

 

In the script, we plot the distribution periodically, and there are some things you should be able to notice.

 

You’ll see that the distribution starts out fat and as it gets updated it gets skinnier and skinnier and taller and taller.

 

The area under the PDF is always 1, so whenever it gets skinnier it must get taller.

 

The reason it’s getting skinnier is because we’re becoming more confident in our estimate of the parameter.

 

In other words, this is a natural way to represent confidence bounds or confidence intervals.

 

Also notice that this is an instance of online learning .

 

The distribution becomes more precise after every single coin toss, not just after we collect all the data.

 

You’ll see that all of the learning methods we’ll look at in this book are able to update iteratively.

 

In my first Bayesian machine learning class, you learned that a Gaussian likelihood is conjugate with a Gaussian prior on the mean.

 

If we place a prior ONLY on the mean mu, and assume the variance is fixed, we can start with these forms of the likelihood and prior.

 

You can see that we’re using precision parameters which is the inverse variance. This makes the math a little easier to work with.

 

X ~ Normal(mu, tau ^ (-1)),

mu ~ Normal(m, lambda ^ (-1))

 

The parameters for the mu distribution are “m” and “lambda”, and so what we are looking for is the update equations for “m” and “lambda”.

 

We can solve for the new m and the new lambda by using Bayes rule again:

 

p(mu | X) proportional to p(X | mu)p(mu)

 

You should find that:

 

lambda’ = lambda + tau\*N

m’ = \[ m\*lambda + tau\*sum\[i=1..N\]{ X(i) } \] / lambda’

 

Remember that N = number of samples we’ve collected and X(i) represents one sample.

 

I would strongly recommend going through the math so that you can solve this yourself (it’s highly non-trivial to represent formulae in this ebook format).

 

\---

 

The last step of this, is to talk about how we apply it to the bandit problem.

 

The answer is sampling.

 

The key part is again the line of code where we choose the bandit.

 

Rather than choosing the argmax of the upper confidence bound like we did with UCB1, we’re going to choose the argmax of samples from each of the bandit means.

 

Remember the means are now probability distributions, so we can draw samples from them.

 

How does this help us explore and exploit?

 

Well you saw in the demo earlier that the distribution always starts out as fat and then gradually becomes skinnier.

 

When the distribution is fat, we still have a high chance of sampling a very high number, and hence when the distribution is fat, we are encouraged to explore more often.

 

When the distribution becomes skinny and we become more confident in our estimates, we explore less and exploit more, since the sample will always be in a very narrow range.

 

So sampling from the Bayesian posterior automatically controls how much exploration and exploitation we do.

 

 

## Comparing Thompson Sampling to Others

 

In this section we are going to write one big script to compare all of the explore-exploit solutions to each other.

 

We have 4 techniques to compare: epsilon-greedy, optimistic initial values, UCB1, and Bayesian sampling.

 

Since we already know epsilon-greedy performs sub-par, we’re going to modify it. How we’re going to do that, is use a decaying epsilon. In particular, we’ll set epsilon to 1/t, where t is the iteration number.

 

We’ll see that in the end all of these perform about the same, which justifies using epsilon-greedy throughout the book.

 

If you don’t want to code this yourself, although I highly recommend you do, the relevant file in the course repo is comparing\_explore\_exploit\_methods.py

 

`import numpy as np`

`import matplotlib.pyplot as plt`

`from comparing_epsilons import Bandit`

`from optimistic_initial_values import run_experiment as run_experiment_oiv`

`from ucb1 import run_experiment as run_experiment_ucb`

` `

`class BayesianBandit:`

`def __init__(self, m):`

`self.m = m`

`# parameters for mu - prior is N(0,1)`

`self.m0 = 0`

`self.lambda0 = 1`

`self.sum_x = 0 # for convenience`

`self.tau = 1`

` `

`def pull(self):`

`return np.random.randn() + self.m`

` `

`def sample(self):`

`return np.random.randn() / np.sqrt(self.lambda0) + self.m0`

` `

`def update(self, x):`

`# assume tau is 1`

`self.lambda0 += 1`

`self.sum_x += x`

`self.m0 = self.tau*self.sum_x / self.lambda0`

` `

` `

`def run_experiment_decaying_epsilon(m1, m2, m3, N):`

`bandits = [Bandit(m1), Bandit(m2), Bandit(m3)]`

` `

`data = np.empty(N)`

`for i in xrange(N):`

`# epsilon greedy`

`p = np.random.random()`

`if p < 1.0/(i+1):`

`j = np.random.choice(3)`

`else:`

`j = np.argmax([b.mean for b in bandits])`

`x = bandits[j].pull()`

`bandits[j].update(x)`

` `

`# for the plot`

`data[i] = x`

`cumulative_average = np.cumsum(data) / (np.arange(N) + 1)`

` `

`# plot moving average ctr`

`plt.plot(cumulative_average)`

`plt.plot(np.ones(N)*m1)`

`plt.plot(np.ones(N)*m2)`

`plt.plot(np.ones(N)*m3)`

`plt.xscale('log')`

`plt.show()`

` `

`for b in bandits:`

`print b.mean`

` `

`return cumulative_average`

` `

` `

`def run_experiment(m1, m2, m3, N):`

`bandits = [BayesianBandit(m1), BayesianBandit(m2), BayesianBandit(m3)]`

` `

`data = np.empty(N)`

`for i in xrange(N):`

`# optimistic initial values`

`j = np.argmax([b.sample() for b in bandits])`

`x = bandits[j].pull()`

`bandits[j].update(x)`

` `

`# for the plot`

`data[i] = x`

`cumulative_average = np.cumsum(data) / (np.arange(N) + 1)`

` `

`# plot moving average ctr`

`plt.plot(cumulative_average)`

`plt.plot(np.ones(N)*m1)`

`plt.plot(np.ones(N)*m2)`

`plt.plot(np.ones(N)*m3)`

`plt.xscale('log')`

`plt.show()`

` `

`return cumulative_average`

` `

`if __name__ == '__main__':`

`eps = run_experiment_decaying_epsilon(1.0, 2.0, 3.0, 100000)`

`oiv = run_experiment_oiv(1.0, 2.0, 3.0, 100000)`

`ucb = run_experiment_ucb(1.0, 2.0, 3.0, 100000)`

`bayes = run_experiment(1.0, 2.0, 3.0, 100000)`

` `

`# log scale plot`

`plt.plot(eps, label='decaying-epsilon-greedy')`

`plt.plot(oiv, label='optimistic')`

`plt.plot(ucb, label='ucb1')`

`plt.plot(bayes, label='bayesian')`

`plt.legend()`

`plt.xscale('log')`

`plt.show()`

` `

` `

`# linear plot`

`plt.plot(eps, label='decaying-epsilon-greedy')`

`plt.plot(oiv, label='optimistic')`

`plt.plot(ucb, label='ucb1')`

`plt.plot(bayes, label='bayesian')`

`plt.legend()`

`plt.show()`

 

Note that we make use of already-written code.

 

Remember that mu is now no longer something we’re trying to find a fixed estimate of, it’s a random variable whose whose distribution has fixed parameters.

 

Bayesian methods are kind of like Inception, so your parameters are random variables, but the parameters of the distributions of the original parameters can also be random variables, and so on.

 

Since the posterior depends on the sum of X, we keep that as an instance variable for convenience. We also know that tau is 1.

 

The new method here is the sample method, which generates a sample from a Gaussian with mean m0 and precision lambda0.

 

The update method just implements the update equations I showed you in the last section.

 

Now we have a function for running the epsilon-greedy experiment with a decaying epsilon. This is largely the same as before, but epsilon is now 1/(i + 1).

 

Next we have the run\_experiment function for Bayesian sampling. The only major change is, as usual in the argmax part, where we call the sample function from earlier.

 

In the main section, we run all 4 experiments, and plot the results.

 

After running the script, you should see that all the methods are about equal. Which method comes out on top usually changes each time you run the script.

 

 

## Nonstationary Bandits

 

In this lecture we are going to discuss the issue of nonstationarity and look at some of the equations we’ve seen more in-depth.

 

This will be useful for later lectures since the same equations are going to show up again and again.

 

So what do we mean by nonstationarity?

 

A stationary process is a process whose statistics don’t change over time.

 

We are interested in the mean, but strictly speaking, there are different types of stationarity.

 

Weak-sense stationarity is when the mean and autocovariance don’t change over time. The autocovariance is a 2nd order statistic.

 

There is also strong-sense stationarity where the entire PDF has to remain the same over time. This is the kind of stationarity that we have, because each bandit has the same distribution each time you pull its arm.

 

Note that a strong-sense stationary process is also a weak-sense stationary process but the reverse is not true.

 

The question is, what if the bandits weren’t stationary? Would it then make sense to calculate the mean as we have been?

 

Recall our mean-update equation from earlier.

 

Xmean(t)=(1-1/t)Xmean(t-1) + (1/t)X(t)

 

Let’s call Xmean Q for convenience. We can rearrange the terms so that we have the 1/t term all by itself.

 

Q(t)=Q(t-1) - (1/t)(Q(t-1) - X(t)), Q(t) = Xmean(t)

 

We can generalize this even further so that the 1/t term is representing by a learning rate alpha, so it kind of looks like gradient descent.

 

Q(t) = Q(t-1) - alpha\*(Q(t-1) - X(t))

 

The key with this equation is, we don’t have to use alpha = 1/t as the learning rate.

 

If you recall from deep learning part 2, a 1/t learning rate was one of the adaptive learning rate techniques we studied.

 

But learning rates can be anything.

 

What if we set alpha to a constant?

 

This should look familiar too.

 

Q(t) = (1 - alpha)\*Q(t-1) + alpha\*X(t)

 

This is something we looked at when we looked at the Theano scan function as a simple example of how to use Theano scan.

 

My YouTube tutorial on the Theano scan function is free to view if you haven’t seen it yet: [https://youtu.be/R-7OGU3V4IY](https://youtu.be/R-7OGU3V4IY)

 

Recall that this implements a simple low-pass filter.

 

If we get rid of the recurrence, we can find Q in terms of all past values of X.

 

Q(t) == alpha \* sum\[k=0..t\]{ (1 - alpha)^k X(t - k) }

 

And from this we can see that Q has an exponentially decaying dependence on X.

 

In this way, Q puts more emphasis on recent values of X rather than past values of X, so it’s like a moving average, or in other words, low pass filter.

 

If you want to run the low pass filter from the Theano scan tutorial, the relevant folder is hmm\_class (same repo as this book) and the relevant file is scan3.py

 

You can see here that we start out with a very noisy sine wave, and after we pass it through the low-pass filter, most of the high-frequency noise goes away.

 

\---

 

There is a popular result you usually see in reinforcement learning literature that talks about the convergence of Q.

 

The result is that Q will converge if the sum of all alphas is infinity, but the sum of all the squares of the alphas is constant.

 

sum\[t=1..inf\]{ alpha(t) } = inf

sum\[t=1..inf\]{ alpha(t)^2 } < inf

 

If you think back to calculus 2, it should be clear from these criteria that constant alpha does not meet these 2 conditions, but alpha = 1/t does.

 

The reason you often see a constant alpha used, is because reinforcement learning problems are often non-stationary, so it doesn’t make sense to try and calculate a sample mean over every collected sample ever.

 

\---

 

Let’s do some simple problems to solidify this concept. We already know that 1/t converges. What about alpha(t) = 1/t^2?

 

Answer: this doesn’t converge because the sum over all alphas is not infinity.

 

What about alpha = 1/t^(2/3)?

 

Answer: In this case, there will be convergence, because the sum over all alphas is infinity, but if we square alpha, the power in the denominator becomes bigger than 1, so that converges to a constant.

#  

 

# Tic-Tac-Toe

 

In this section of the course we are going to approach the tic-tac-toe from a programmatic perspective.

 

First, we’ll look at what you would do if you were a first-year computer science student.

 

First-years are typically just learning the basics of a language like Java or C++, and probably coding a game like tic-tac-toe is a challenge in and of itself.

 

In this course we’ll be directly coding all our environments. And that means coding a tic-tac-toe game as well.

 

It helps to understand the overall picture if you understand in detail every part of the system.

 

In our case, that includes both the agent and the environment and any code that interfaces between the 2.

 

In the next course / book, once you’re more familiar with the ideas of reinforcement learning, we’ll abstract away the environment, so that you won’t be able to poke inside and look at the internals of the game you’re playing. In a way that’s kind of like playing the game in God-mode.

 

So in this lecture we are sort of looking at how you’d play tic-tac-toe in God-mode. You know everything about the game, you know how to play so that you never lose.

 

\---

 

It’s possible to enumerate all these rules, but we won’t since that’s not what this course is about. But I want you to at least consider what they might be.

 

For example, if the board is empty and it’s your turn, you want your first move to be either at the center or a corner.

 

Another rule might be, if your opponent has 2 pieces in a row, you want to put your piece down to block theirs so that they don’t get 3 in a row.

 

Another rule is that if you see 2 of your own pieces in a row and it’s not blocked and it’s your turn, you should complete the row so that you get 3 pieces in a row so that you can win the game.

 

\---

 

So what does this look like in code?

 

Essentially it would be a bunch of if statements.

 

What’s the problem with a bunch of if statements?

 

Well it goes against the whole idea of machine learning.

 

That is, we want one algorithm that can generalize to many problems. Just like how we can use a neural network for classifying pictures of animals but we can also train the same algorithm to classify music.

 

If we write a tic-tac-toe agent made up of if statements, that program will never be able to do anything other than just play tic-tac-toe.

 

So we need something better, which is why we want to do reinforcement learning.

 

\---

 

One important aspect of this is that we have a model for how the game works. We know everything about tic-tac-toe.

 

We know what state leads to the highest reward. Or in other words, any state where you have 3 pieces in a row, you get a reward, which is winning the game, otherwise you lose or get nothing.

 

We know how to transition from one state to the next. In other words, by doing some action, we know exactly what the next state is given the current state. It seems trivial, but in some environments it’s not so trivial. In tic-tac-toe, we place a piece on the board, and the piece goes to the place that we chose, and we arrive in the expected next state. This isn’t always the case.

 

\---

 

These ideas will come into play later, but I would recommend you start to think about them now.

 

You’ll see that some of the algorithms we learn require us to have a model of the environment, like we do for tic-tac-toe.

 

Other algorithms won’t require us to know anything, we’ll just explore the world and take in the information as we go along.

 

 

## Components of a Reinforcement Learning System

 

In this section we are going to define the components of a reinforcement learning system.

 

It might seem a little redundant at first because we already did this in the intro section, but you’ll notice that as we progress further and further into the book, we’re going to look at the same concepts each time, but make them more rigorous.

 

We’ll also add more components each time, so each time you’ll learn a few more terms, building on what you knew before.

 

\---

 

So in this section we are going to again look at some concepts you already know a little bit about:

 

There’s the agent , that’s the thing playing the game and the thing you want to program a reinforcement learning algorithm into.

 

There’s the environment , that’s the thing the agent interacts with. It’s the agent’s world.

 

There’s the state , which is the specific configuration of the environment that the agent is sensing.

 

\---

 

Note that the state only involves what the agent can sense, not everything about the environment.

 

For example if I have a vacuum robot cleaning my house in Australia then what’s happening in someone else’s house in India won’t affect my vacuum robot’s state.

 

\---

 

Another example is if you have a self-driving car that has a 360 degree view of everything around it. If there’s a truck in front of you, and there’s a car in front of that truck, then that car is not part of your state, because you can’t see it.

 

So your state would be the same, whether that car is in front of the truck that’s in front of you, or not.

 

\---

 

And finally we have actions and rewards .

 

Actions are the things the agent can do that will affect its state. So in our tic-tac-toe game that’s placing a piece on the board.

 

Performing an action always brings us to the next state, which also comes with a possible reward.

 

\---

 

One aspect of rewards is that a reward just tells you “how good” your action was, not whether it was a correct/incorrect action. It doesn’t tell you whether it was the best/worst action. It’s just a number.

 

So if you’re an agent, the rewards you’ve gotten over the course of your existence don’t necessarily represent the possible rewards you could get in the future.

 

You could be searching a bad part of the state space and hit a local maximum of 10 points, when the global maximum is 1000 points.

 

But you would never know that if you were the agent. We’d know because we designed the game. That’s again an instance of God-mode knowledge.

 

\---

 

That’s a lot like the life of an animal or human being as well. You’re born into a specific environment, and you do your daily routine. You might find some things that make you happy, and you might consider that a sort of local maximum reward.

 

But what if that person is living in some place without modern medicine or technology, and then you compare that to modern life in modern civilizations, you realize that the local maximum is nowhere near the global maximum.

 

So everything is relative, rewards are kind of meaningless numbers that only make sense relative to each other.

 

In terms of reinforcement learning more reward is always better than less reward.

 

\---

 

Now here’s some funny notation.

 

We know that being in state S(t), and taking action A(t), will lead us to the reward R(t+1) and the state S(t+1).

 

But when we drop the time indexes, we represent this 4-tuple as (s, a, r, s’). We don’t prime the r as you might expect, which is odd but it’s the standard notation.

 

So the prime does not mean “at time=t+1”.

 

\---

 

Now we are going to define some new terms.

 

The first new term we want to discuss is “episode ”.

 

An episode represents one run of the game.

 

For example, we’ll start a game of tic-tac-toe with an empty board.

 

As soon as one player gets 3 of their pieces in a row, that’s the end of that episode.

 

As you can imagine, our reinforcement learning agent will be learning across many episodes.

 

So for example, after playing 1000 or 10,000 or 100,000 episodes we can possibly have trained an intelligent agent.

 

How long it will take is of course is a hyperparameter and that depends on the game being played, the number of states, how random the game is, and so on.

 

You should be used to hyperparameters if you’ve taken deep learning courses in the past.

 

\---

 

We call playing the game of tic-tac-toe an “episodic task” because you can play it again and again.

 

This is different from a “continuous task”, which never ends. So in a way you only play that game once.

 

We will not be looking at continuous tasks in this book.

 

\---

 

How do we know we’re at the “end” of an episode? There are certain states in the state space that tell you the game is over.

 

For tic-tac-toe this is when one of the 2 players has 3 of their pieces in a row or when the board is full.

 

These states are called “terminal states ”.

 

So a “terminal state” is a state from which you can take no more actions. It means the episode is over.

 

In terms of tic-tac-toe that means either player 1 has won, player 2 has won, or it’s a draw.

 

\---

 

Another famous problem in reinforcement learning and control systems is the problem of the inverted pendulum, as it’s called in control systems, or cart-pole, as it’s called in reinforcement learning. They are the same problem.

 

If you search “inverted pendulum” on Google you’ll see research papers in the control systems field, and if you search “cart-pole” on Google you’ll see research papers in the reinforcement learning field.

 

At the beginning of an episode, the cart is stationary and the pole is perpendicular to the ground. But since this is an unstable system, the pole starts to fall down, and the job of the agent is to move the cart so that the pole doesn’t fall.

 

When the pole falls so far that it’s impossible to get it back up, any angle past a certain threshold is a terminal state.

 

Note that because the angle in this system is a real number, this is a continuous state space and hence there are an infinite number of states.

 

We will note deal with continuous state spaces or state spaces of infinite size in this book.

 

\---

 

The idea of being able to learn from multiple “episodes” is kind of like the movie Groundhog Day.

 

In this movie the main character wakes up and lives through the same day, everyday.

 

So it allows him to get better and better at making the most out of that day.

 

That’s like what happens to an agent in reinforcement learning. Even though you may lose a lot of episodes at first, you learn from them.

 

Each episode is a fresh start. So eventually you get to a point where you are an expert because you’ve explored all the potential ways that an episode can proceed.

 

\---

 

Let’s summarize everything we know about the components of a reinforcement learning system so far.

 

We reviewed the agent, environment, states, actions and rewards. We learned about episodes and how an AI will learn across many episodes, and that the terminal state represents the end of an episode.

 

In the next couple of sections we’ll look at some subtleties concerning reward assignment and how to do the actual “learning”.

 

 

## Notes on Assigning Rewards

 

In this section we are going to take a deeper look at the concept of rewards.

 

One difficult part of reinforcement learning is how to define rewards. You can think of us, the programmers, as sort of coaches to the AI.

 

Maybe a pet owner is a good analogy too. So if you have a pet you can relate the material you learn in this course to real life.

 

The reward is something we give to the agent. We can define how we’re going to reward the agent, which in turn will drive how it learns.

 

For example, if we give it the same reward no matter what it does, then the agent will probably end up acting very randomly, since any action will lead to the same value.

 

That’s like giving your pet a treat even when it behaves badly. You don’t want to do that because it’s going to encourage bad behavior.

 

\---

 

One good example of how to define rewards is a maze. Imagine you’re a robot and you’ve never seen this maze before. So you kind of just randomly move along, trying to find your way out.

 

The goal, which is to exit the maze, gives you a reward of 1. Otherwise, you get nothing.

 

Now to most people that seems reasonable, and it is reasonable.

 

\---

 

However with this reward structure, the robot may never actually solve the maze. Remember that the robot only knows about what it’s experienced.

 

So if it’s only ever seen a reward of 0, then it will think, “that’s the best I can do”.

 

A better solution would be to give the robot a reward of -1 for every step it takes, and it that way it will be encouraged to solve the maze as quickly as possible.

 

\---

 

One point of caution is to not build in your own prior knowledge into the AI.

 

For example, in the game of chess, the agent should be only rewarded for winning, not for doing things like taking your opponent’s pieces or implementing some strategy that you read about in a chess book.

 

You want to leave the agent free to come up with its own solution.

 

The danger of rewarding the agent for achieving subgoals is that they might find a novel way to maximize the reward for the subgoals without actually winning the game.

 

For example, taking all but one of the opponent’s chess pieces and then losing.

 

To summarize that, we can say that the reward signal is your way of communicating to the agent what you want it to achieve, not how you want to be achieved.

 

 

## The Value Function and Your First Reinforcement Learning Algorithm

 

## Credit Assignment

 

Imagine this scenario.

 

You are thinking about studying for tomorrow’s exam. But you would rather hang out with your friends.

 

Your friends will make you feel happy, and so to you that’s a reward. You get a dopamine hit.

 

If you study tonight, you’re going to feel tired and bored, and maybe your dopamine will decrease, so that’s sort of like a negative reward.

 

So why do we study for exams?

 

Because we don’t just think about immediate rewards, we design a plan of action based on future rewards too.

 

If you study, you’ll do well on your exam, you’ll get good grades, and you’ll get a good job that pays well.

 

So we want to assign some value for being in the state: you staying at home studying for your exam.

 

We call this the value function, and that’s what we’re going to talk about in this section.

 

\---

 

Now let’s think of this in the reverse direction.

 

You receive a reward, let’s say that is, getting hired for your dream job.

 

Now if you look back at the various things you did in your career and at school, what would you attribute your success to?

 

What state of being in your past led you to get your dream job today?

 

The credit assignment problem is the problem of answering the question:

 

What did you do in the past that led you to get the reward you are receiving now? In other words, “what action gets the credit?”

 

\---

 

The credit assignment problem shows up in online advertising too, but in a bit of a different form. In online advertising it’s called “attribution”.

 

The idea is, if a user eventually converts, and buys your product, but 10 different ad networks showed your ad, who takes the credit for the conversion?

 

There are various schemes for distributing the credit, like assigning the credit linearly.

 

But you can see that for us it’s a much deeper problem. Maybe it was the act of showing the user the ad 10 times that made them want to buy your product.

 

So in that sense, all the ads deserve to get the same credit.

 

Perhaps the user didn’t see the ad the first 9 times, perhaps something else on the page was more interesting to look at. Maybe they only saw the 10th ad. So in that case only the 10th ad deserves the credit.

 

So in reinforcement learning we’re interested in the entire state sequence and how that particular sequence led to the final reward.

 

 

## Delayed Rewards

 

Closely related to the idea of the credit assignment problem is the idea of “delayed rewards”.

 

Keep in mind these are all just kind of different ways of saying the same thing, and the solution is also the same.

 

Delayed rewards are just looking at the problem from the other direction.

 

With credit assignment we’re looking into the past and asking, “what action caused the reward we’re getting now?”

 

With delayed rewards we’re asking, how is the action I’m doing now related to the potential reward I may receive in the future?

 

The idea of delayed rewards tells us that an AI needs to have the ability of foresight or planning. “Planning” is actually a field of study that crosses over with reinforcement learning.

 

\---

 

Imagine this scenario. You are in state A, which is the 2nd last state in the game. There are only 2 possible next states, B or C, both of them are terminal states.

 

`oA`

`0.5 / \ 0.5`

`/ \`

`oB oC`

`R=1 R=0`

 

B gives you a reward of 1, and C gives you a reward of 0. You have a 50% probability of going to either state, perhaps because your agent doesn’t yet know which one is best.

 

We can think of the value of state B as 1 and the value of state C as 0.

 

What is the value of state A?

 

We can think of it as 0.5, since it’s the expected value of your final reward given that you have a 50% chance of ending up in either terminal state.

 

\---

 

Let’s say you’re in state A, and state A can only lead to state B, and there’s no other possible next state.

 

If B gives you a reward of 1, then perhaps A’s value should also be 1, since the only possible place to end up is with a final reward of 1, once you reach A.

 

`oA`

`1 / \ 0`

`/ \`

`oB oC`

`R=1 R=0`

 

Thus, this value tell us about the “future goodness” of a state.

 

\---

 

To make this a little more formal, we actually call this value the value function .

 

It’s a measure of the future rewards we might get.

 

I think the term value function is a pretty horrible name since the term “value” is very ambiguous, but it’s part of the reinforcement learning nomenclature.

 

\---

 

It’s easy to get rewards and values intermixed.

 

The difference is, the value of a state is a measure of the possible future rewards we may get from being in this state.

 

Rewards are immediate. i.e. Jumping on a Goomba will immediately increase your score.

 

Standing in front of a Goomba will not increase your score, hence will not yield any reward.

 

However, being in this state has value because we can soon jump on the Goomba and get the reward in the future .

 

\---

 

So standing near the Goomba prepared to jump might have a higher value than standing on the other edge of the screen from a Goomba.

 

We therefore choose actions based on the value of the next state, rather than the reward we would get by going to that state.

 

The reward is the main goal, but we can’t use the reward to tell us how good a state is, since it doesn’t tell us anything about future rewards.

 

\---

 

One way to think about the value function is that it’s a fast or efficient way of determining “how good” it is to be in a state, without needing to search the rest of the game tree.

 

You could try to enumerate every possible state transition in a game, and determine all the state transition probabilities, but you can imagine that would be a time consuming task.

 

In fact, most games would be computationally infeasible. Tic-tac-toe is easy since it’s only a 3x3 board, so the number of states is approximately 3^9 = 19683. But that grows exponentially with the size of the board. For example, if you have a 4x4 board, like in connect 4, then you get 3^16 = 43 million. As you probably already know exponential growth is never good. Searching the state space is only possible in the simplest of cases. Hence a value function that can tell you how good you’ll do in the future given only your current state is extremely helpful.

 

At this point, I haven’t told you how we can actually find the value function, so we don’t even know if it’s possible yet, but what we’re saying here is if we did have it, then that’s the information it would tell us, and it would tell us that information instantly, without needing to create an entire model of the game tree and transition probabilities.

 

In fact, this is a constant time lookup because a state directly maps to a value. You would presumably store the values in an array which has constant time lookup.

 

This problem, by the way, is yet another instance of the curse of dimensionality, which we’ve seen in my other machine learning courses as well.

 

\---

 

Estimating the value function is a central task in reinforcement learning. But note that not all RL strategies require it. For instance, a genetic algorithm simply spawns offspring that have random genetic mutations, and the ones who survive the longest will go on to spawn offspring in the next generation. So by pure evolution or natural selection we can breed AIs that get iteratively better at a game.

 

This is however, not the type of algorithm we’re interested in for reinforcement learning most of the time.

 

\---

 

Let’s get to the math.

 

The value function, as we talked about, takes in one argument, the state. So we denote it as V(s).

 

It’s the expected value of all future rewards, given that the current state is s. Or in other words, the average value of all possible future rewards, given that the current state is s.

 

V(s) = E\[ all future rewards | s \]

 

Pretty simple.

 

We’ll define the concept of value more rigorously in a later section.

 

\---

 

Now let’s look at a generic algorithm we can use to find the value function.

 

In this section of the book, we’re going to introduce some unrealistic constraints so that the problem can actually be solved, but you’ll see in the later sections that we won’t need to do this.

 

The algorithm we’ll use is an iterative one, meaning we’ll run a loop and each time we go through the loop we’ll get closer and closer to the true value function.

 

The first thing we do is initialize the value function. For all the states where the agent wins, we say the value is 1. For all the states where the agent loses or it’s a draw, we say the value is 0. For all other states we say the value is 0.5.

 

`# init`

`V(s) = 1 if s = winning state`

`V(s) = 0 if s = losing state or draw`

`V(s) = 0.5 otherwise`

 

For the algorithms we look at in the future we won’t need to do such careful initialization.

 

One way you can interpret the value function, for only this game, but not in general, is it’s the probability of winning.

 

The value is always going to be between 0 and 1, so it makes sense.

 

\---

 

The update equation looks simple but there are some hidden details.

 

`V(s) = V(s) + alpha*(V(s’)-V(s))`

` `

`# s = current state, s’ = next state`

 

The first detail is that “s” here means all states that we encountered in an episode.

 

So that means for each iteration of the loop, we actually need to play the game and remember all the states we were in.

 

We then loop through each of the states in the state history and update the value using this equation.

 

Notice how the value of a terminal state will never get updated, because this equation updates a state’s value based on the next state value, which doesn’t exist if we’re in a terminal state.

 

\[i.e. if s = terminal, then s’ doesn’t exist\]

 

\---

 

In pseudocode it might look like this:

 

`for t in range(max_iterations):`

`state_history = play_game()`

`s = state_history[0]`

`for s’ in state_history[1:]:`

`V(s) = V(s) + learning_rate*(V(s’) - V(s))`

 

\---

 

The next detail we have to talk about is how to actually play the game.

 

Are we just going to take random actions?

 

In this case, we don’t have to, since we have the value function.

 

The value function tells us how good a state is based on how good the future states will be, so all we need to do is perform the action that leads to the best next state.

 

In pseudocode it might look like this:

 

`maxV = 0`

`maxA = None`

`for a, s’ in possible_next_states:`

`if V(s’) > maxV:`

`maxV = V(s’)`

`maxA = a`

`perform action maxA`

 

\---

 

Now what’s the problem with this strategy?

 

The problem is the value function isn’t accurate! If we already had an accurate value function, we wouldn’t need to do any of this work in the first place.

 

You might recognize this problem as a problem we already talked about. It’s the explore-exploit dilemma .

 

In particular, by taking random actions, we can learn about new states that we would have otherwise never gone to.

 

By doing so, we can improve our estimate of the value function for those states.

 

But in order to win , we need to do the action that yields the maximum value.

 

So we’ll be using the epsilon-greedy strategy to make a trade-off between exploration and exploitation.

 

\---

 

Let’s look at some intuition for why this iterative update works.

 

First, you’ll recognize this update equation from before. It should remind you both of the low-pass filter and the iterative average finding equation we saw earlier.

 

It should also look like gradient descent if you’ve encountered that in the past. V(s’) is like the target value, and we want to move V(s) toward that value.

 

However, with reinforcement learning there are multiple possible next states, so there are multiple s’.

 

So by doing this update equation multiple times we’re pulling V(s) in multiple different directions for each different s’.

 

The idea is that, by playing infinitely many episodes, the proportion of time we spend in s’ will approach the true next-state probabilities.

 

As the number of games approaches infinity, we achieve the exact expected value:

 

p(s1)\*V(s1) + p(s2)V(s2) + ...

 

\---

 

One extremely important detail that’s also extremely difficult to discern given only the update formula, is the order in which you have to update the values for any given state.

 

We know that for any particular episode, we’re only going to be updating the values for the states that were in that episode.

 

But the key with this equation is, we’re moving V(s) closer to V(s’).

 

That means we’re doing this update under the assumption that V(s’) is more accurate than V(s).

 

For the terminal state, this is true, since that’s always going to be 0 or 1 and will never change.

 

But if both V(s) and V(s’) are of the same accuracy, as in, they are both not accurate at all, then making one closer to the other won’t make anything better.

 

So the idea is we want to move backwards through the state history. Because the current state value is always updated using the next state value, then we want the next state value to be more accurate, so we should update the values in reverse order.

 

This is also consistent with the terminal state being precisely accurate with a value of 0 or 1 that never changes.

 

Therefore, we should modify our pseudocode as follows:

 

`for t in range(max_iterations):`

`state_history = play_game()`

`T = len(state_history)`

`s’ = state_history[T-1]`

`for t = T - 2 ... 0:`

`s = state_history[t]`

`V(s) = V(s) + learning_rate*(V(s’) - V(s))`

`s’ = s`

 

\---

 

Let’s summarize what we’ve just talked about.

 

First, we looked at the credit assignment problem and the concept of delayed rewards.

 

This is the idea that, an action you take now, doesn’t necessarily lead to a reward right now. In fact it might lead you to a reward many steps ahead.

 

A great example of this is studying. Studying right now will probably just make you feel tired and miss out on hanging out with your friends, so in fact it might even be a slightly negative reward.

 

But the future reward is that you do well on your test, get good grades, and get a high paying job.

 

We looked at the value function as a solution to this problem, because it tells you how valuable being in a state is, which makes considerations for future rewards as well. This entire course in fact is devoted to showing you algorithms for how to determine a value of a state.

 

We looked at the problem from a computational perspective - the fact that a tree of all the possible game states and transitions will grow exponentially means searching it to find the value of a state is infeasible.

 

We therefore use an iterative algorithm, which essentially brings the value of a current state closer to the value of a possible next state. Since there are multiple possible next states, the algorithm is stochastic, but in the long run it should approach the mean or expected value.

 

Throughout this course, we’ll see variations on this same idea over and over again.

 

One small warning: The value function we’re learning about in this lecture is not like the “formal” version we’ll learn about later and use throughout the rest of this course. Everything in the Tic-Tac-Toe section is informal just to get you used to the whole process of solving a RL problem.

 

Since this is so abstract, I think the most useful thing we can do is start looking at some code to see how we can implement this. Or in other words, how look at how a computer implements this algorithm and carries out this strategy.

 

# Tic Tac Toe in Code

 

In this chapter we are going to start looking at the code for tic-tac-toe.

 

Typically in machine learning we’re implementing self-contained algorithms, so it’s simple to look at the code line by line.

 

However, with reinforcement learning, there are multiple objects interacting, so we’ll want to take an object-oriented approach.

 

Because of that, we’ll first do an overview in this lecture of all the objects we need to represent and how they interact.

 

After that we’ll look at the details of each object.

 

Keep in mind that this solution is in no way unique, and in fact there is some poor coupling between objects that are probably not optimal.

 

So if you were to do this on your own chances are high that your solution might look way different, which is ok as long as it works.

 

If you don’t want to code along and you just want to run the code, the relevant file in the course repo is tic\_tac\_toe.py.

 

\---

 

At a high level, we’ll have 2 main objects, the Agent and the Environment.

 

`Agent <-----> Environment`

` `

`play_game(agent1, agent2, environment)`

 

During any game, there will be 2 instances of the agent object, and they’ll both interact with the same single instance of the environment.

 

In order to make these things interact, we can create a function called play\_game(), which accepts the agent for player 1, the agent for player 2, and the environment object.

 

\---

 

So what should go inside the play\_game() function?

 

First, the code. Then, discussion.

 

`def play_game(p1, p2, env, draw=False):`

`# loops until the game is over`

`current_player = None`

`while not env.game_over():`

`# alternate between players`

`# p1 always starts first`

`if current_player == p1:`

`current_player = p2`

`else:`

`current_player = p1`

` `

`# draw the board before the user who wants to see it makes a move`

`if draw:`

`if draw == 1 and current_player == p1:`

`env.draw_board()`

`if draw == 2 and current_player == p2:`

`env.draw_board()`

` `

`# current player makes a move`

`current_player.take_action(env)`

` `

`# update state histories`

`state = env.get_state()`

`p1.update_state_history(state)`

`p2.update_state_history(state)`

` `

`if draw:`

`env.draw_board()`

` `

`# do the value function update`

`p1.update(env)`

`p2.update(env)`

 

Inside this function, it’ll essentially be a single loop. We’ll alternate between the 2 players, and at each iteration of the loop, we need to do a few things.

 

First, we need to make the current player perform an action which updates the environment.

 

Second, we need to switch who the current player is, so that it alternates.

 

Third, we need to check if the game is over, since that’s when the loop will terminate.

 

So you see here we’ve created a partial API for some instance methods that our objects will need.

 

The environment will need a game\_over() function that returns a boolean, true if the game is over, false if not. You can imagine that this is going to have to scan the board to check if there is a winner or if the board is full and it’s a draw.

 

The agent will need a take\_action() function which accepts as a parameter the environment. This will update the environment and hence the state.

 

Another function we need on the agent is an update() function that updates that agent’s internal estimate of the value function. This is where the update equation we talked about is going to go. The update() function will need to accept the environment as well since it’ll have to query the most current reward from the environment.

 

Another function that will be extremely useful for us, but not strictly necessary, is a draw\_board() function that will display what positions are currently occupied and by what pieces.

 

\---

 

From this design alone, you can probably start coding your own tic-tac-toe. So if you had no idea where to start previously, hopefully this gave you a direction for where to start heading. So if you want to try to do the rest yourself, that would be highly encouraged.

 

## Representing States

 

In this lecture we are going to talk about how we’re going to represent states in our tic-tac-toe game.

 

Earlier I promised you that this would be an O(1) lookup.

 

One way to accomplish this would be to use a dictionary, since the keys to a dictionary can be any immutable object. So we could represent the game board with a 2-D tuple of size 3x3 and store the values inside as tuple elements.

 

However, we can do this so that each state maps to a number, and by doing that we can store the value function as a Numpy array.

 

\---

 

So how can we map each state to a number?

 

Recall that we talked about how to find an upper limit on the number of hidden states earlier.

 

We calculated it to be 3^9 = 19683 which is not too big of an array to store in memory.

 

Notice that this also encodes impossible states, for example, an “X” in all 9 locations, since you only need 3 in a row to win.

 

This overhead doesn’t affect the algorithm at all so we won’t worry about it. These states are never reachable anyway, since in every iteration of the loop we’re going to check if the game is over, and if it is, we’ll quit the loop.

 

So these values will never show up in the state history, which means their values will never be used or updated.

 

\---

 

The idea of having 9 locations, and 3 possible values per location, should remind you of binary numbers.

 

You know that N bits can store 2^N different integers, and we can enumerate those possibilities by finding all the permutations of a string of length N where each location can only contain 0 or 1.

 

To convert a binary number into decimal, you know that the equation can be represented like this.

 

D = 2 ^(N-1)  b [N-1]  +...+2 ¹  b [1]  +2 ⁰  b [o] 

 

So all we need to do is replace the 2 with 3. And instead of “b” representing only 0 or 1, it’ll have the values 0, 1, or 2.

 

D = 3 ^(N-1)  b [N-1]  +...+3 ¹  b [1]  +3 ⁰  b [o] 

 

\---

 

In code, it’s going to look like this:

 

`k = 0`

`h = 0`

`for i in xrange(LENGTH):`

`for j in xrange(LENGTH):`

`if self.board[i,j] == 0:`

`v = 0`

`elif self.board[i,j] == self.x:`

`v = 1`

`elif self.board[i,j] == self.o:`

`v = 2`

`h += (3**k) * v`

`k += 1`

`return h`

 

Notice how we loop through each location in the board, which requires a nested for loop, but that’s only because of the structure of the board.

 

We need to keep track of the power, which starts at 3^0 and gets multiplied by 3 on each new location, so we keep track of that with the variable k.

 

We use the variable h to accumulate the final result. We use the letter “h” because “h” stands for “hash”, and that’s essentially what we’re doing. We’re hashing an object and the output is an integer.

 

 

## Enumerating States Recursively

 

In this lecture we are going to talk about what work needs to be done in order to initialize the value function properly.

 

You’ll recall that for this particular algorithm, we need to initialize the value function to very specific values, but for the algorithms we’ll learn about later, which are considered the “real” reinforcement learning algorithms, you should be able to initialize the value functions randomly.

 

The initialization we need is V(s) = 1 for any state where the player wins, V(s) = 0 for any state where the player loses or it’s a draw, and V(s) = 0.5 for all other states.

 

In order to do this, we need to enumerate every possible state and assign the values.

 

\---

 

Here’s a question to think about.

 

Is it better to create a game tree, where you enumerate every possible sequence of moves, or is it better to permute all 3^9 configurations of the board, even though many of those configurations represent impossible game states?

 

Think about it, then come back to the book!

 

\---

 

So what happens if you do the game tree version?

 

The problem is this leads to redundant states, or in other words, we’ll see the same state more than once in the game tree.

 

For example, consider the case where X goes in the top-middle, and then O goes in the center.

 

Another path down the tree that leads to this exact same state is if O goes in the center, and then X goes in the top-middle.

 

`+---+---+---+`

`| | x | |`

`+---+---+---+`

`| | o | |`

`+---+---+---+`

`| | | |`

`+---+---+---+`

`2 ways to get to this state`

 

If you think about how many different tree nodes there will be in this game tree, you can see that at the root you have 9 different choices, then at the layer below that you have 8 different choices, and then 7 and so on.

 

So the total number of states you’ll see is 9! = 362 880.

 

This is an order of magnitude larger than 3^9 = 19683.

 

So the algorithm we want to use to enumerate all the states is definitely just generating the permutations.

 

\---

 

Ok, so how do we generate permutations?

 

Think of just a binary number again.

 

This is naturally a recursive problem, since a binary number of length N can start with 0 or 1, and then we can use all the permutations for a binary number of length N-1 appended to that.

 

`all permutations of length N =`

`[1] + all permutations of length N - 1`

`[0] + all permutations of length N - 1`

 

\---

 

In pseudocode, we can do it like this. First we get the recursive results, that is all the binary numbers of length N-1. We do this outside the loop since it would be redundant to do it more than once. On the outer loop we loop through all the possible prefixes, and on the inner loop we loop through all the child results. Inside the loops we create the new results by combining the prefix and the suffix and we append this to our results list.

 

For simplicity I’m not showing you the base case here.

 

`def generate_all_binary_numbers(N):`

`results = []`

`child_results = generate_all_binary_numbers(N-1)`

`for prefix in (‘0’, ‘1’):`

`for suffix in child_results:`

`new_result = prefix + suffix`

`results.append(new_result)`

`return results`

 

\---

 

So that was just an example for doing permutations in general. For us, it’s going to be slightly different.

 

We are going to have a recursive function called get\_state\_hash\_and\_winner, and this is going to return a list of triples. Each triple is going to contain the state as a hashed number, who the winner is, if there is one, and whether or not this state represents a finished game.

 

The 3 arguments to this function are the environment, which we really just need for the board matrix, and the (i, j) coordinates to place the next value, which can be 0 (empty), “X”, or “O”.

 

\---

 

`def get_state_hash_and_winner(env, i=0, j=0):`

`results = []`

` `

`for v in (0, env.x, env.o):`

`env.board[i,j] = v # if empty board it should already be 0`

`if j == 2:`

`# j goes back to 0, increase i, unless i = 2, then we are done`

`if i == 2:`

`# the board is full, collect results and return`

`state = env.get_state()`

`ended = env.game_over(force_recalculate=True)`

`winner = env.winner`

`results.append((state, winner, ended))`

`else:`

`results += get_state_hash_and_winner(env, i + 1, 0)`

`else:`

`# increment j, i stays the same`

`results += get_state_hash_and_winner(env, i, j + 1)`

` `

`return results`

 

In this function I am going to show you the base case. If i=2 and j=2, then we’re filling up the last location on the board, which means we should now check the game state, who the winner is, and whether or not the game is ended.

 

Notice how even though I’m talking about the board being “filled up” now, I mean it can be filled up by the 0 value also, which represents empty, so it doesn’t necessarily mean the game is over, it just means the permutation is done.

 

Now if it’s not a base case, we want to recursively call this function, but there are 2 numbers we can increase, i or j, but never both at the same time.

 

If we’re at the end of a row, which means j=2, then we want to go to the next row at the first column, so we set j=0 and we increment i.

 

If we’re not at the end of a row, we just increment j and leave i the same.

 

\---

 

Finally, I want to point out that the initial value functions for the 2 players won’t be equivalent.

 

Remember that one player has to be “X”, and one player has to be “O”.

 

So if the value function is 1 for “X” (X wins), it’s going to be 0 for “O” (O loses), and vice versa. But it’s not completely the opposite, since if there is a draw, both players get 0.

 

So we’ll have 2 functions which are almost the reverse of each other, initializeV\_x, and initializeV\_o.

 

`state_winner_triples = get_state_hash_and_winner(env)`

` `

`def initialV_x(env, state_winner_triples):`

`# initialize state values as follows`

`# if x wins, V(s) = 1`

`# if x loses or draw, V(s) = 0`

`# otherwise, V(s) = 0.5`

`V = np.zeros(env.num_states)`

`for state, winner, ended in state_winner_triples:`

`if ended:`

`if winner == env.x:`

`v = 1`

`else:`

`v = 0`

`else:`

`v = 0.5`

`V[state] = v`

`return V`

` `

` `

`def initialV_o(env, state_winner_triples):`

`# this is (almost) the opposite of initial V for player x`

`# since everywhere where x wins (1), o loses (0)`

`# but a draw is still 0 for o`

`V = np.zeros(env.num_states)`

`for state, winner, ended in state_winner_triples:`

`if ended:`

`if winner == env.o:`

`v = 1`

`else:`

`v = 0`

`else:`

`v = 0.5`

`V[state] = v`

`return V`

 

\---

 

Let’s summarize what we just did since that was pretty long.

 

We know in order to initialize the value function for all states, we need to first enumerate all the states.

 

We saw 2 ways of doing this, either searching the game tree, or doing permutations on the board.

 

We saw that searching the game tree would take more steps than doing permutations since there’s a lot of redundancy.

 

Note however they are both exponential or super-exponential so they’re both bad.

 

And lastly I showed you the recursive function that we’re going to use in order to enumerate all the states.

 

So we are slowly putting the pieces together for our tic-tac-toe game. As you can see many of the pieces are non-trivial.

 

## The Environment

 

In this lecture we are going to take an in-depth look at the environment class.

 

Remember that the environment is the thing that the agent interacts with.

 

Let’s start with an overview of all the methods we’re going to look at:

 

There’s the constructor, where we initialize important instance variables.

 

There’s is\_empty(i, j) which tells us if a location on the board is empty or not.

 

There’s reward(symbol) which gives us back a reward when we pass it the symbol representing a specific player.

 

There’s get\_state() which we looked at earlier, it takes the state of the board and returns a number.

 

There’s game\_over(), which checks if the game is over or not by looking at the state of the game, and returns true or false.

 

And there’s draw\_board(), which draws the current tic-tac-toe board. You can imagine that this would be pretty pointless if we could not see the tic-tac-toe board.

 

\---

 

Let’s start with the constructor since this will introduce is to all of the instance variables we’re interested in.

 

`class Environment:`

`def __init__(self):`

`self.board = np.zeros((LENGTH, LENGTH))`

`self.x = -1 # represents an x on the board, player 1`

`self.o = 1 # represents an o on the board, player 2`

`self.winner = None`

`self.ended = False`

`self.num_states = 3**(LENGTH*LENGTH)`

 

The first instance variable is the board, which is a square. We initialize it as 0s because 0 is going to be our symbol for empty.

 

Next we define the symbols for X and O. Note that these all have to be numbers since we’re going to store them in a Numpy array. You’ll see why assigning them to +1 and -1 is convenient for us later on.

 

Next we have the winner, which we initialize to None. None means there is no winner, or that there is no winner yet . Once we do have a winner, we’ll assign this to either +1 or -1.

 

Next we have a boolean variable “ended”. This is obviously going to start out as false, and will only become true at the end of a game.

 

Lastly we have a variable called num\_states which is just a convenience thing so we don’t have to write 3^(LENGTHxLENGTH) everywhere.

 

\---

 

Next we have the is\_empty function, which takes in 2 arguments which represent a position on the board.

 

`def is_empty(self, i, j):`

`return self.board[i,j] == 0`

 

This is a useful function for the agent because the agent needs to check if a location is valid before trying to put one of its own pieces there. So this returns true if that position on the board is 0, and false otherwise.

 

\---

 

Next we have the reward function.

 

As we stated before the reward is 1 if we win the game, otherwise the reward is 0.

 

`def reward(self, sym):`

`# no reward until game is over`

`if not self.game_over():`

`return 0`

` `

`# if we get here, game is over`

`# sym will be self.x or self.o`

`return 1 if self.winner == sym else 0`

 

Reinforcement learning is defined such that a reward is given as feedback on every state transition, so we need to have this function be able to return a valid result in every case, which is why we can’t just call it when the game is over.

 

When an agent calls this function it’ll need to pass in its own symbol, which tells us that each agent will need to know its own symbol.

 

\---

 

Now we get to the more complex functions.

 

We’ve actually already seen get\_state earlier in the course when we talked about enumerating states.

 

`def get_state(self):`

`k = 0`

`h = 0`

`for i in xrange(LENGTH):`

`for j in xrange(LENGTH):`

`if self.board[i,j] == 0:`

`v = 0`

`elif self.board[i,j] == self.x:`

`v = 1`

`elif self.board[i,j] == self.o:`

`v = 2`

`h += (3**k) * v`

`k += 1`

`return h`

 

The idea is that if we order the states as base-3 digits, then the entire thing is a base-3 number, and we can convert that into 1 decimal number.

 

\---

 

Next we have the game\_over() function. This is probably the most complex function in the environment class.

 

`def game_over(self, force_recalculate=False):`

`# returns true if game over (a player has won or it's a draw)`

`# otherwise returns false`

`# also sets 'winner' instance variable and 'ended' instance variable`

`if not force_recalculate and self.ended:`

`return self.ended`

`# check rows`

`for i in xrange(LENGTH):`

`for player in (self.x, self.o):`

`if self.board[i].sum() == player*LENGTH:`

`self.winner = player`

`self.ended = True`

`return True`

` `

`# check columns`

`for j in xrange(LENGTH):`

`for player in (self.x, self.o):`

`if self.board[:,j].sum() == player*LENGTH:`

`self.winner = player`

`self.ended = True`

`return True`

` `

`# check diagonals`

`for player in (self.x, self.o):`

`# top-left -> bottom-right diagonal`

`if self.board.trace() == player*LENGTH:`

`self.winner = player`

`self.ended = True`

`return True`

`# top-right -> bottom-left diagonal`

`if np.fliplr(self.board).trace() == player*LENGTH:`

`self.winner = player`

`self.ended = True`

`return True`

` `

`# check if draw`

`if np.all((self.board == 0) == False):`

`# winner stays None`

`self.winner = None`

`self.ended = True`

`return True`

` `

`# game is not over`

`self.winner = None`

`return False`

 

We have this force\_recalculate argument you might be wondering about.

 

First, you’ll notice that game\_over is called multiple times in this script. If a game has ended already we don’t want to do this complicated operation again and again, so we just use the fact that it’s already ended as a shortcut.

 

But if you recall in our earlier recursive function to enumerate the states, we recursively filled out each location on the board. This involves placing pieces on the board, taking them off, placing other pieces, and so on. So we are going to go back and forth between a game over state and a non-game over state, which means we can’t use that shortcut.

 

So force\_recalculate allows us to make sure the entire operation happens every time (if we need it to).

 

The next parts of the game\_over() function are as expected, we check if there’s a winner, and if there’s no winner, we check if the board is full which means it’s a draw.

 

We check for a winner by first checking all the rows, then all the columns, then the diagonals.

 

This is where assigning the values of X and O to be -1 and +1 really helps us. Since if we ever have 3X’s in a row, the sum will be -3, and if we have 3O’s in a row, the sum will be +3.

 

If we do find a winner, we then set the winner instance variable to the player that won, and we set the ended instance variable to true. We also return true since the game\_over() function needs to return a boolean.

 

The only place where this is slightly non-trivial is when we check the diagonals.

 

We know that the trace of a matrix is the sum of all the elements along the main diagonal, so doing the trace will give us the sum from the top left to bottom right.

 

But what about the sum from the top right to bottom left? In order to use trace here, we need to first flip the matrix and then do the trace.

 

For checking if there’s a draw, this is a function that checks if all the elements on the board are simultaneously non-zero.

 

In this case we explicitly set the winner to None, even though the winner might already be None since that’s what we set it as in the constructor.

 

The reason we want to set the winner explicitly is that when we call this function, it’s possible that this is a recalculation, so winner might have been previously set to something else first, in which case, we want to set it to its true current value.

 

Finally at the end, if none of the above conditions are true, we return false.

 

\---

 

Lastly we have a function called draw\_board, which will help us visualize the tic-tac-toe game.

 

`def draw_board(self):`

`for i in xrange(LENGTH):`

`print "-------------"`

`for j in xrange(LENGTH):`

`print " ",`

`if self.board[i,j] == self.x:`

`print "x",`

`elif self.board[i,j] == self.o:`

`print "o",`

`else:`

`print " ",`

`print ""`

`print "-------------"`

 

In fact it would probably be very hard to play tic-tac-toe if you couldn’t see it.

 

So this just loops through every position on the board and places the correct symbol in the correct position.

 

 

## The Agent

 

In this section we are going to talk about the other major class in the tic tac toe file, the Agent.

 

What we know so far is that this is the AI, or the thing that contains the AI.

 

This is different from regular machine learning because in this situation, we’re not just feeding this thing data.

 

Instead, the agent has to interact with the environment, which we just discussed. Our little one-line learning algorithm will be a very small part of the agent, yet at the same time it’s responsible for 100% of its intelligence.

 

\---

 

Let’s start with an overview of all the instance methods we’re going to look at.

 

First there’s setV(V) which allows us to initialize the value function. You know since we discussed it already that the value function is going to be initialized in a very specific way.

 

There’s set\_symbol(sym) which allows us to give this agent a symbol that it’ll use to play on the board.

 

There’s set\_verbose(b) which takes in a boolean. This does exactly what it sounds like it does, it prints more information if verbose is set to true. So for example it’ll print the board along with the values for each next possible move before the agent takes a turn.

 

There’s reset\_history(). We need this because we want to keep track of the state history for every episode, but once the episode is finished and we’re done learning, we don’t need that state history anymore and we can start a new episode.

 

There’s take\_action(env) which takes in the environment as an input. This is going to check the board for valid moves and make a move based on a strategy, and if you remember we are using the epsilon-greedy strategy for this game.

 

We have update\_state\_history(s) which adds a state to the state history. We don’t want to include this in the take\_action function because we only call take\_action during every other turn, whereas the state history needs to be updated whenever any player takes a turn.

 

Finally there’s the update(env) function, which also takes in the environment as an input. It queries the environment for the latest reward, which will correspond to the end of an episode because we’re only going to call update() at the end of an episode. This is where all the learning will happen.

 

\---

 

The first 5 of these functions are pretty trivial.

 

`class Agent:`

`def __init__(self, eps=0.1, alpha=0.5):`

`self.eps = eps # probability of choosing random action instead of greedy`

`self.alpha = alpha # learning rate`

`self.verbose = False`

`self.state_history = []`

`def setV(self, V):`

`self.V = V`

` `

`def set_symbol(self, sym):`

`self.sym = sym`

` `

`def set_verbose(self, v):`

`# if true, will print values for each position on the board`

`self.verbose = v`

` `

`def reset_history(self):`

`self.state_history = []`

 

The constructor sets epsilon, which is needed to implement epsilon greedy. It sets alpha, which is the learning rate for our update equation. It sets verbose which is False by default, and it sets the state history to an empty list as you would expect.

 

SetV, set\_symbol, and set\_verbose are simple setters.

 

reset\_history() just sets state history back to an empty list.

 

\---

 

Next we have the take\_action function.

 

`def take_action(self, env):`

`# choose an action based on epsilon-greedy strategy`

`r = np.random.rand()`

`best_state = None`

`if r < self.eps:`

`# take a random action`

`if self.verbose:`

`print "Taking a random action"`

` `

`possible_moves = []`

`for i in xrange(LENGTH):`

`for j in xrange(LENGTH):`

`if env.is_empty(i, j):`

`possible_moves.append((i, j))`

`idx = np.random.choice(len(possible_moves))`

`next_move = possible_moves[idx]`

`else:`

`# choose the best action based on current values of states`

`# loop through all possible moves, get their values`

`# keep track of the best value`

`pos2value = {} # for debugging`

`next_move = None`

`best_value = -1`

`for i in xrange(LENGTH):`

`for j in xrange(LENGTH):`

`if env.is_empty(i, j):`

`# what is the state if we made this move?`

`env.board[i,j] = self.sym`

`state = env.get_state()`

`env.board[i,j] = 0 # don't forget to change it back!`

`pos2value[(i,j)] = self.V[state]`

`if self.V[state] > best_value:`

`best_value = self.V[state]`

`best_state = state`

`next_move = (i, j)`

` `

`# if verbose, draw the board w/ the values`

`if self.verbose:`

`print "Taking a greedy action"`

`for i in xrange(LENGTH):`

`print "-----------------"`

`for j in xrange(LENGTH):`

`if env.is_empty(i, j):`

`# print the value`

`print "%.2f|" % pos2value[(i,j)],`

`else:`

`print " ",`

`if env.board[i,j] == env.x:`

`print "x |",`

`elif env.board[i,j] == env.o:`

`print "o |",`

`else:`

`print " |",`

`print ""`

`print "-----------------"`

` `

`# make the move`

`env.board[next_move[0], next_move[1]] = self.sym`

 

Remember that we are doing epsilon-greedy. So with probability epsilon, we’ll just do a random action.

 

Now in order to take a random action, we need to make a list of all the possible moves. This is equivalent to all the positions on the board where is\_empty returns true, which we can call because we’ve passed in the environment.

 

Once we have a list of possible moves, we choose one with uniform probability.

 

\---

 

Next we have the greedy part of epsilon-greedy.

 

In its simplest form, what we need to do is very similar to the random strategy. We’re going to loop through all the positions on the board, check if it’s empty, and if it’s empty, check its value.

 

If its value is greater than our current greatest value, we keep track this value and this position by making this the new greatest value.

 

Once we’ve done that we can put our own symbol on the chosen location.

 

\---

 

The greedy part gets a little more complicated when you consider printing out the verbose information.

 

What we want to print out is the board, along with all the values that the agent sees, because that’s what it’s using to make a decision.

 

So in the first loop we want to create a mapping from the (i,j) coordinate to the value.

 

Then if verbose is true, we print the entire board, and if the position is empty, we print the value, otherwise we print the symbol that’s placed on that part of the board.

 

\---

 

Next we have update\_state\_history, which is pretty trivial. You already know state\_history is stored as a list, so we just need to append to the list.

 

`def update_state_history(self, s):`

`# cannot put this in take_action, because take_action only happens`

`# once every other iteration for each player`

`# state history needs to be updated every iteration`

`# s = env.get_state() # don't want to do this twice so pass it in`

`self.state_history.append(s)`

 

We could pass in the environment here and call get\_state(), but recall that that requires some calculation, and that we need to update the state history for both agents on each round.

 

So it’s faster just to calculate it once and pass it in.

 

\---

 

Finally we have the update function.

 

`def update(self, env):`

`# we want to BACKTRACK over the states, so that:`

`# V(prev_state) = V(prev_state) + alpha*(V(next_state) - V(prev_state))`

`# where V(next_state) = reward if it's the most current state`

`#`

`# NOTE: we ONLY do this at the end of an episode`

`# not so for all the algorithms we will study`

`reward = env.reward(self.sym)`

`target = reward`

`for prev in reversed(self.state_history):`

`value = self.V[prev] + self.alpha*(target - self.V[prev])`

`self.V[prev] = value`

`target = value`

`self.reset_history()`

 

Recall that we only want to do this at the end of an episode, which is not true for all the algorithms we’ll study.

 

That means when we get the reward from the environment, it’ll be 1 if we won, or 0 if we lost or it’s a draw.

 

Then we need to look at the state history in reverse, since the update for a value of a state depends on the value of the next state.

 

You can see that the first target is exactly equal to the final reward in the game, but after that the targets are all just value estimates. The hope is that those value estimates will converge over time.

 

Once this is done we reset the state history since we don’t need it anymore and we don’t want it showing up in future calculations.

 

 

## Main Loop + Other

 

In this lecture we are going to go through the rest of our tic-tac-toe game. We’ve already seen the 2 main pieces: the Agent and the Environment, so now all that’s left is the code that makes them interact and other miscellaneous things.

 

\---

 

Let’s first look at the Human class.

 

`class Human:`

`def __init__(self):`

`pass`

` `

`def set_symbol(self, sym):`

`self.sym = sym`

` `

`def take_action(self, env):`

`while True:`

`# break if we make a legal move`

`move = raw_input("Enter coordinates i,j for your next move (i,j=0..2): ")`

`i, j = move.split(',')`

`i = int(i)`

`j = int(j)`

`if env.is_empty(i, j):`

`env.board[i,j] = self.sym`

`break`

` `

`def update(self, env):`

`pass`

` `

`def update_state_history(self, s):`

`pass`

 

It wouldn’t make much sense to just train an AI to play tic-tac-toe and not give you a feel for how good it got.

 

So in order for you to gain intuition for what your AI is thinking, we’ve created the Human class so that you can play against the AI. We’ll be setting verbose to True, so that you can see the “value” of each position every time the AI takes a turn.

 

Notice that you probably do this internally in your head too. You look at each of the available positions, and really quickly do a quick calculation to determine which one is best.

 

Notice how the human class has some dummy functions, that’s because the game playing function we’ll see later doesn’t discriminate between the type of agent, it always calls the same functions. So we need some placeholders.

 

\---

 

Next let’s look at the play\_game function. It takes in 3 required arguments, which are the 2 players and the environment. It takes a boolean draw, which will draw the board for you if it’s True.

 

This will obviously be required if a human is playing the game.

 

`def play_game(p1, p2, env, draw=False):`

`# loops until the game is over`

`current_player = None`

`while not env.game_over():`

`# alternate between players`

`# p1 always starts first`

`if current_player == p1:`

`current_player = p2`

`else:`

`current_player = p1`

` `

`# draw the board before the user who wants to see it makes a move`

`if draw:`

`if draw == 1 and current_player == p1:`

`env.draw_board()`

`if draw == 2 and current_player == p2:`

`env.draw_board()`

` `

`# current player makes a move`

`current_player.take_action(env)`

` `

`# update state histories`

`state = env.get_state()`

`p1.update_state_history(state)`

`p2.update_state_history(state)`

` `

`if draw:`

`env.draw_board()`

` `

`# do the value function update`

`p1.update(env)`

`p2.update(env)`

 

Inside the play game function, we keep track of who the current player is. The first player is always player 1.

 

We enter the loop, which exists when the game is over.

 

The first part of the loop allows us to alternate between players, and it makes player 1 go first.

 

Since we DON’T want to draw the board before the AI takes a turn, we allow draw to take on the values 1 and 2, 1 for player 1, and 2 for player 2. That way, the board only gets drawn once every other turn, and for the correct player.

 

The next step is for the agent to take an action, and the step after is to update the state histories of all the agents.

 

When the loop is done we can draw the board one last time so you can see who won.

 

After that, we can do the value function update since the episode is now over.

 

\---

 

In the main section of the script, we’ll see how the play\_game function is used, since we’ll need to run through many episodes in order for the agent to learn the game to a significant degree.

 

`if __name__ == '__main__':`

`# train the agent`

`p1 = Agent()`

`p2 = Agent()`

` `

`# set initial V for p1 and p2`

`env = Environment()`

`state_winner_triples = get_state_hash_and_winner(env)`

` `

` `

`Vx = initialV_x(env, state_winner_triples)`

`p1.setV(Vx)`

`Vo = initialV_o(env, state_winner_triples)`

`p2.setV(Vo)`

` `

`# give each player their symbol`

`p1.set_symbol(env.x)`

`p2.set_symbol(env.o)`

` `

`T = 10000`

`for t in xrange(T):`

`if t % 200 == 0:`

`print t`

`play_game(p1, p2, Environment())`

` `

`# play human vs. agent`

`# do you think the agent learned to play the game well?`

`human = Human()`

`human.set_symbol(env.o)`

`while True:`

`p1.set_verbose(True)`

`play_game(p1, human, Environment(), draw=2)`

`# I made the agent player 1 because I wanted to see if it would`

`# select the center as its starting move. If you want the agent`

`# to go second you can switch the human and AI.`

`answer = raw_input("Play again? [Y/n]: ")`

`if answer and answer.lower()[0] == 'n':`

`break`

 

The first step is we create 2 AIs.

 

The next few steps are all devoted to initializing the AIs.

 

First we initialize their value functions, and remember they are different for the 2 agents depending on which one is X and which one is O.

 

We also set their symbols.

 

Next, we play 10 000 games of AI vs AI.

 

We technically could have created a method to reset the environment here but I just haven’t done it. So instead we just create a new Environment on every iteration.

 

Finally, when the AI is done training, you can play against it yourself, so we create a Human object and set its symbol to O.

 

We set verbose to True so that you can see the value function that the AI uses to make decisions.

 

I’ve chosen the agent to be player 1 here because I wanted to see if it would select a good starting position on the tic-tac-toe board, but you are free to experiment with other configurations of this script.

 

Run this yourself and:

\* see if AI starts in the center

\* make a mistake on purpose so AI can win

\* show that AI blocks me if I try to win

 

## Summary

 

In this section we are going to summarize this chapter section since it was extremely long.

 

It’s amazing to think that we did all that just to play tic-tac-toe, and we haven’t even yet seen the main reinforcement learning algorithms in this course yet.

 

\---

 

First, I asked you to think about how you would solve tic-tac-toe as a naive first year computer science student. The answer was that we would end up building an agent with a bunch of if statements. It wouldn’t adapt to its environment or get better as it played more games.

 

So even if it seemed intelligent at first, it would never be able to increase its intelligence.

 

Moreover, the algorithm would not be generalizable to new games, it would only work for tic-tac-toe.

 

So we’ve set out on this course to find algorithms that are intelligent, and that allow an AI to solve anything given the right rewards.

 

\---

 

Next, we took a deeper look at the components of a reinforcement learning system.

 

We defined the agent, environment, state, actions, and rewards.

 

We talked about how specific reward structures can lead to poor results, so we need to choose them carefully. This is like you choosing how to reward your dog in order to train it to behave well.

 

We looked at new terms, like episode and terminal state, which we needed to fully understand the algorithm we used for tic-tac-toe.

 

\---

 

Next, we looked at the credit assignment problem and closely related to that, the idea of delayed reward.

 

The idea was that an action you take now may not lead to a good immediate reward, but it may maximize your future rewards. So you want to be able to plan intelligently.

 

We used these to motivate the idea behind the value function.

 

We saw that, based on how the value function is updated, if we initialize it in the correct way, such that the value of the terminal state is 1 if we win and 0 otherwise, then the values will propagate backward along the state history.

 

We do this iterative update in small steps at the end of each episode, so only the possible next states can influence the previous state.

 

\---

 

Finally, we put this all together in code, and you saw that the algorithm does indeed work, and that the tic-tac-toe agent, once it’s trained to play tic-tac-toe, makes intelligent moves.

 

\---

 

Now that you’ve had some experience with reinforcement learning, it’s interesting to look back and try to compare it with supervised learning.

 

A common question is - why can’t we just create a supervised learning problem that maps states to actions directly?

 

\---

 

The first problem with this is how we would come up with labels. As you’ve already seen, it’s extremely easy for the state-space to grow too large to enumerate. Tic-tac-toe or connect-4 is probably the limit.

 

Imagine a video game with HD graphics and 60 frames per second. Now you have millions of pixels, with hundreds of values per pixel, and 60 of those every second. The number of possible states in a game like this is so large you probably can’t even conceptualize it.

 

So there’s no way you can create proper labels.

 

\--

 

There’s also the fact that labels only tell us if we’re right or wrong. In a way, a reward is more flexible and gives us more information because it tells us “how right” or “how wrong”. Rewards tell us how good we’re doing.

 

\---

 

Rewards are delayed, but the value function has this information built-in.

 

If you’re trying to choose the best action for a particular state, assuming somehow you get around the problem that you need to label an exponentially large dataset, you still need to choose the best action based on all possible future rewards.

 

That means you would need to be the one calculating the value of each state and choosing the best action based on those values.

 

In other words, instead of letting an algorithm calculate values in a way that automatically accounts for delayed rewards, you would need to somehow keep track of all that yourself.

 

\---

 

Rewards can also have a component of randomness.

 

So sometimes when you go to a state you get a reward of 1, but other times you get 0.

 

This could be like, you study for your exam tomorrow, but then tomorrow there’s a snow storm and your exam is canceled.

 

Next states can likewise also be random.

 

\---

 

In reinforcement learning we are never told externally if an action / state pair is good or not.

 

The only way we can find out is by “discovering” it ourselves by performing the action.

 

\---

 

Finally, reinforcement learning is completely online. We learn as we play. Every time the tic-tac-toe agent plays an episode of tic-tac-toe, it gets better.

 

Compare this to a decision tree. It takes all its training data in at once and creates a tree based on that.

 

If you want to incorporate new data into the tree, you need to start all over again.

 

I hope this gives you some further insight into why it might seem like supervised learning can be used for reinforcement learning tasks, when in fact this would be an infeasible task.

 

# Markov Decision Processes

 

## Gridworld

 

In this chapter, we are going to formalize some of the concepts we’ve already learned about in reinforcement learning. We’ve learned about the terms agent, environment, action, state, reward, and episode.

 

This section is all about putting all these concepts into a formal framework called Markov Decision Processes.

 

\---

 

In this section we are going to describe the game that we are going to use for the rest of the book.

 

In many ways this is actually a simpler game than tic-tac-toe, but it has some properties that allows us to explore some more of the features of reinforcement learning.

 

In Gridworld your agent is a robot, and the environment, as you probably would guess, is a grid.

 

The agent is allowed to move in 4 directions: up, down, left, or right. That is its entire set of actions.

 

The grid is usually built in this way.

 

`0 1 2 3`

`+-----+-----+-----+-----+`

`0| | | | win |`

`+-----+-----+-----+-----+`

`1| | wall| | lose|`

`+-----+-----+-----+-----+`

`2|start| | | |`

`+-----+-----+-----+-----+`

 

At position (1, 1) there is a wall, so the robot can’t go there. If it tries to go there, it just bumps into the wall.

 

At position (0, 3) and position (1, 3) we have 2 terminal states. Position (0, 3) is the goal state. You want to end up here because this is where you get the maximum reward. Position (1, 3) is a losing state. If you end up here you lose. I use the term “lose” loosely because we are more concerned with well-defined concepts like total reward. In any case, at this position you will receive a large negative reward. So you don’t want to end up there.

 

\---

 

One thing you’ll notice about Gridworld is that it has a much smaller number of states than tic-tac-toe. The state can be defined as the position of the robot. So there are only 11 states, because the grid is of size 12 and the robot can’t go to one of the squares.

 

As you’ve already seen, there are only 4 actions.

 

So this is a pretty small game - 11 states and 4 actions. And from this we will derive the rest of the concepts in this course.

 

 

## The Markov Property

 

In this lecture we are going to discuss the Markov property. As you can tell from the name, the Markov property is a central component of the Markov Decision Process.

 

The reason we’re devoting an entire lecture to the Markov property is because in the context of reinforcement learning, the Markov property looks a little different than what we’ve seen in the past.

 

\---

 

Let’s review the Markov property in the strict mathematical sense.

 

Suppose we have a sequence x(1) up to x(t).

 

{x(1), x(2), ..., x(t)}

 

We can define a conditional probability on x(t) given all the previous x’s.

 

p{x(t) | x(t-1),x(t-2),...,x(1)}

 

Generally speaking, this can’t be simplified.

 

But if we assume that the Markov property is true , then it can be simplified.

 

First-order Markov:

p{x(t) | x(t-1),x(t-2),...,x(1)} = p{x(t) | x(t-1)}

 

Second-order Markov:

p{x(t) | x(t-1),x(t-2),...,x(1)} = p{x(t) | x(t-1), x(t-2)}

 

The Markov property (order) specifies how many previous x’s the current x depends on.

 

So first-order Markov means that x(t) depends only on x(t-1).

 

Second-order Markov means that x(t) depends only on x(t-1) and x(t-2).

 

In this course, we will be working with first-order Markov only, and we typically just refer to this as the Markov property.

 

\---

 

Let’s do a simple example of the Markov property.

 

Let’s consider the sentence, “Let’s do a simple example”.

 

If I were to tell you: “here are the previous words in my sentence, now predict the next word”.

 

And the previous words are “Let’s do a simple...”.

 

You could probably guess that the next word is “example”.

 

Now I say, the “the previous word is just ‘simple’”. Can you predict the next word? Probably, but it’s harder.

 

What if the previous word is just “a”? Can you predict the next word? Probably not.

 

But that’s what the Markov assumption is.

 

So you see that the Markov assumption can be quite limiting, but you can also define your problem such that it’s not.

 

\---

 

So what does the Markov property look like in reinforcement learning?

 

Recall that doing an action A(t) while in state S(t) produces 2 things.

 

It produces the next state, S(t+1), and a reward, R(t+1).

 

What the Markov property in this case says, is that S(t+1) and R(t+1) depend ONLY on A(t) and S(t), but not any A or S before that.

 

p{S(t+1),R(t+1) | S(t),A(t),S(t-1),A(t-1),...,S(1),A(1)} = p{S(t+1),R(t+1) | S(t),A(t)}

 

For convenience, we can also use our shorthand symbols, s, a, r, and s’.

 

p(s',r | s,a) = p{S(t+1)=s’,R(t+1)=r | S(t)=s,A(t)=a}

 

So how is this different from the “usual” way we write the Markov property?

 

Well notice how this is a joint distribution on s’ and r. So it’s telling us the joint distribution of 2 variables, conditioned on 2 other variables.

 

This is different from the “usual” Markov from where we only have 1 variable on the left and 1 variable on the right.

 

\---

 

Given this joint conditional distribution, it is of course just a matter of using the rules of probability to find the marginal conditional distributions. For example if we just want to know s’ given s and a, or we just want to know r, we can use these equations:

 

p(s' | s,a) = integral\[r\]{ p(s’,r | s,a)dr }

p(r | s,a) = sum\[s’\]{ p(s’,r | s,a) }

 

(Assuming r is continuous and s is discrete).

 

Also note that for pretty much all cases we’ll consider, these probabilities will be deterministic.

 

That means, the reward you get for going to the state will always be the same reward.

 

And doing an action in a state will always bring you to the same next state.

 

But it’s good to know that these probabilities are defined if you need them, and they are also part of the core theory.

 

\---

 

As an example of how the Markov assumption is not necessarily limiting, we can look at a recent application of reinforcement learning.

 

DeepMind (Mnih et al. 2013) used the concatenation of the 4 most recent frames in order to represent the current state.

 

Strictly speaking, the state can be made up of anything from anytime from past to current. We just typically think of the state right now to be something we are measuring right now, but that need not be the case.

 

Note that we also need not use raw data to represent the state. The state can also be made up of data derived from the raw data. You might think of that as a feature transformation on the raw data.

 

Essentially any input from the agent’s sensors can be used to form the state.

 

 

 

## Formalizing the Markov Decision Process

 

In this lecture we are going to look at the Markov Decision Process more formally.

 

We’ve essentially been looking at Markov Decision Processes this whole time, just never calling it by name.

 

Any reinforcement learning task with a set of states, actions, and rewards, that follows the Markov property, is a Markov Decision Process.

 

Formally speaking, a Markov Decision Process is a 5-tuple, made up of the set of states, set of rewards, set of actions, the state-transition probabilities and the reward probabilities, which we previously discussed as a joint distribution, and the discount factor, which we’ll define in a later lecture.

 

\---

 

There is however, one more piece we need to complete the puzzle.

 

The other key term in “Markov Decision Process” is “decision”.

 

The way we make decisions for what actions to do in what states, is called a policy .

 

We usually denote a policy with the symbol pi.

 

Technically the policy is not part of the MDP itself, but it’s part of the solution along with the value function (which we’ll define more formally soon).

 

The reason I’ve left the policy out until now is because it’s kind of a weird symbol.

 

We write down pi as a mathematical symbol, but there’s no equation for pi.

 

For example, if pi is epsilon-greedy, how do write that as an equation? It’s more like an algorithm.

 

E.g. pi = epsilon-greedy? This is not an equation.

 

The only exception to this is when you want to write down the optimal policy, which can be defined mathematically in terms of the value function.

 

We’ll talk about optimal policies and what that means in a later lecture.

 

So for now, pi is more like a short-hand notation for the algorithm the agent is using to navigate the environment.

 

\---

 

Because a Markov Decision Process satisfies the Markov property, you can imagine we can also draw state-transition diagrams for MDPs just like we do for Markov Models and Hidden Markov Models.

 

I don’t do this often but you may find it useful for yourself.

 

\---

 

Let’s look at the state-transition probability again, p(s’ | s, a).

 

Recall that I said this is typically deterministic but that’s not always the case.

 

Why might that be so?

 

Remember that the state is only something derived from what the agent senses from the environment.

 

It’s not the environment itself. The state can be an imperfect representation of the environment.

 

In which case you would expect the state transition to be probabilistic. For example, the state you measure can represent multiple configurations of the environment.

 

As an example of an imperfect representation of the environment, think about Blackjack. You might think of the dealer’s next card as part of the state. But if you’re the agent, you can’t see the next card. So it’s not part of your state. It is part of the environment.

 

\---

 

Sometimes, there’s confusion about what constitutes the agent and the environment.

 

Think of yourself navigating your environment. You might think you are the agent, but what constitutes “you”?

 

Are you your body?

 

Your body is more correctly part of the environment. Your body isn’t making decisions or learning.

 

Your body has sensors which pass on signals to your brain, but it’s your brain or your mind that does all the learning and decision making.

 

So you want to be mindful of where you draw that boundary that differentiates between agent and environment.

 

 

## Future Rewards

 

In this section we are going to formalize the idea of total reward.

 

In particular, what we are interested in measuring is total future reward.

 

So everything from t+1 and onward.

 

We call this the “return”, and use the symbol G(t) to represent it.

 

G(t) = R(t+1) + R(t+2) + ... + R(t+infinity)

 

Notice how it doesn’t depend on the reward at the current time.

 

This is because, strictly speaking, when I arrive at a state, I receive the reward for that state. There’s nothing I can predict about it, since it already happened.

 

\---

 

Now think of a very long task. A task containing a sequence that is thousands of steps long.

 

Your goal is to maximize your total reward.

 

But is there a difference between getting a reward now, and getting that same reward 10 years from now?

 

Think about finance. You know that $1000 today is worth less than $1000 was 10 years ago.

 

If I were to ask you, would you rather get $1000 today, or would you rather get $1000 10 years later, you would of course choose today.

 

\---

 

And so we introduce what is called a discount factor on the future rewards.

 

We call the discount factor gamma and we use a number between 0 and 1 to represent it.

 

G(t) = sum\[t’=0...inf\]{ gamma^t’ R(t+t’+1) }

 

It should be clear that a gamma of 1 means we don’t care about how far in the future a reward is, all future rewards should be weighted equally.

 

If gamma is 0, that means we don’t care about the future at all. Doing that would be a truly greedy algorithm, since the agent would only try to maximize its immediate reward.

 

Usually we choose something in between, like gamma = 0.9.

 

If we have a very short episodic task, it may not be worth discounting at all.

 

An intuitive reason you might want to discount future rewards, is because the further you go in the future, the harder it is to predict. So there’s not a lot of sense in putting all your effort into getting something 10 years from now, unless you’re sure you can make it happen and that your circumstances won’t change.

 

\---

 

You’ll notice that the sum for the return goes from t’ = 0 to infinity.

 

But recall that this suggests we’re looking at a continuous task, when in reality the games we’ve seen, tic-tac-toe and Gridworld, are both episodic tasks.

 

This is a mathematical subtly, but we actually want to write all of our equations in continuous form. Simply put, it makes the math easier.

 

There is a way to “merge” episodic and continuous tasks so that they are equivalent.

 

The way you do it is this.

 

The episodic task has a terminal state. What you can do is, pretend that there is a state transition from the terminal state to itself, that always happens with probability 1, and always yields the reward 0.

 

In this way, the episodic task remains the same, but since it technically goes on forever it’s also a continuous task.

 

 

## Value Functions

 

In this section we are finally ready to start formally discussing value functions.

 

We saw value functions earlier when we discussed tic-tac-toe, but that was informal and only for the purpose of gaining intuition.

 

So if you see any discrepancies between how we defined the value function before, and how we’re defining it now, you should consider everything we do from here onward to be more correct.

 

The value function, given a policy and a state “s”, is equal to the expected value of the return, given that you are currently in state “s”.

 

V(s) = E\[G(t) | S(t)=s\] = E\[ sum\[t’=0...inf\]{ gamma^t’ R(t+t’+1) } | S(t)=s\]

 

Note that because of how it’s defined, the value function is dependent on the policy. This is because any future state transitions depend on what your policy is.

 

Also notice that the value function depends only on future rewards.

 

That means the value of any terminal state is 0, because by definition, you won’t be doing anymore state transitions and hence you won’t be receiving any future rewards.

 

\---

 

Let’s now do some algebra.

 

Notice that the return is recursive. We can separate out R(t+1) from R(t+2) and so on.

 

V(s) = E\[R(t+1) + gamma\*G(t+1) | S(t)=s\]

 

\---

 

Because this is the expected value over pi, that means we can express pi as a probability distribution.

 

In particular, we can express it as the probability of doing an action “a” given that we’re in state “s”.

 

pi = pi(a | s)

 

Since expected values are linear operators, we can do the 2 terms in the expected value separately, so let’s first consider just the expected value of R(t+1) given “s”.

 

Because everything is stochastic, this is governed by 2 probability distributions. First, there’s the policy, pi(a | s), that determines what action we’ll do.

 

Once we have the state-action pair “s” and “a”, there’s also the probability distribution p(s’, r | s, a), which we can marginalize to get p(r | s, a).

 

So both of these probability distributions are needed to find the expected value.

 

E\[R(t+1) | S(t)=s\] = sum\[a\]{ pi(a | s) sum\[r\]{ rp(r | s,a) }}

 

And of course we can write this in terms of the full joint state-transition probability as well, by summing over s’.

 

E\[R(t+1) | S(t)=s\] = sum\[a\]{ pi(a | s) sum\[s’, r\]{ rp(s’,r | s,a) }}

 

In fact, we can use this to calculate the expected value of anything given the policy and the current state.

 

E\[ANY | S(t)=s\] = sum\[a\]{ pi(a | s) sum\[s’, r\]{ ANYp(s’,r | s,a) }}

 

Therefore, we can also use this to calculate the 2nd part of the expected value we saw earlier.

 

V(s) = E\[R(t+1)+gamma\*G(t+1) | S(t)=s\]

 

V(s) = sum\[a\]{ pi(a | s) sum\[s’, r\]{ p(s’,r | s,a)(r + gamma\*E\[G(t+1) | S(t+1)=s’\]) }}

 

V(s) = sum\[a\]{ pi(a | s) sum\[s’, r\]{ p(s’,r | s,a)r+V(s’) }

 

This recursive equation has a special place in reinforcement learning, and it’s the equation from which all the algorithms we learn are based.

 

It’s called the Bellman equation, named after the famous mathematician Richard Bellman.

 

Bellmen pioneered the technique known as “dynamic programming”, which you may have learned about in your algorithms class. It’s related to recursion but it’s efficient since it builds up the solution using a bottom-up approach.

 

In fact, one of the techniques we’ll learn about for solving MDPs is called “dynamic programming”.

 

\---

 

There is one more value function we’ll need to learn about in our discussion of value functions.

 

What we just learned about, V(s), is called the state-value function.

 

There is another value function Q(s, a), called the action-value function. It’s called this because the action “a” is also a parameter of the function.

 

Note that because Q has 2 inputs, the amount of space we need to store it is quadratic. In particular, the amount of space we need is the the size of the set of states times the size of the set of actions (|S|x|A|).

 

Q(s,a)=E\[G(t) | S(t)=s, A(t)=a\]

 

In later sections of the course, you’ll see that the value function we use depends on what algorithm we’re using. There are some algorithms that specifically apply to only the state-value function or the action-value function.

 

 

## Optimal Policies and Optimal Value Functions

 

In this section we are going to discuss optimal policies and optimal value functions.

 

As you’ll see, they are interdependent, so we’ll need to discuss them together.

 

This is a key concept in this course, and as you go through the course you’ll realize how much depth there is to this idea.

 

We can talk about the relative “goodness” of policies.

 

Let’s say we have 2 policies, pi1 and pi2.

 

We can say pi1 is “better than” pi2, if the expected return of pi1 is greater than or equal to the expected return of pi2, for all states.

 

pi1 > pi2 if V1(s) > V2(s) for all s in S

 

Where S denotes the set of all states.

 

\---

 

Because we can talk about the relative “goodness” of policies, and one policy can be “better than” another policy, then we also have the notion of the “best” policy.

 

In reinforcement learning, we call this the optimal policy. We use the symbol pi\* to represent it.

 

The optimal policy is the policy for which there is no greater value function.

 

We can write the optimal value function as the max of the value function over all policies.

 

V\*(s) = max\[pi\]{ V(s | pi) } for all s in S

 

Note that optimal policies are not necessarily unique, but optimal value functions are.

 

You can imagine how 2 policies can lead to the same rewards, and hence lead to the same value functions.

 

But if you have one value function that’s greater than another value function, then the optimal policy will be the one that leads to the greater value function.

 

\---

 

We can similarly define the optimal action-value function as the max of the action-value function over all policies.

 

Q\*(s,a) = max\[pi\]{ Q(s,a | pi) } for all s in S,a in A

 

\---

 

Because the optimal action-value function is with respect to the optimal policy, we can define it recursively in terms of the optimal state-value function.

 

Q\*(s,a)=E\[R(t+1)+V\*(S(t+1)) | S(t)=s,A(t)=a\]

 

\---

 

The state-value function and the action-value function can be related in this way. The state-value function means we are always choosing the best actions, and therefore choosing the max over all actions from Q.

 

V\*(s) = max\[a\]{ Q\*(s,a) }

 

Notice how Q leads to some practical advantages during implementation. If we only have V(s), then what we have to do is try all possible actions “a”, to take us to the next states, so we can get the values for those states.

 

But if we have Q, we can directly choose the best action over all actions “a”, from Q.

 

\---

 

Let’s continue manipulating our equation for V\*.

 

V\*(s) = E\[R(t+1)+V\*(S(t+1)) | S(t)=s,A(t)=a\]

V\*(s) = max\[a\]{ sum\[s’,r\]{ p(s’,r | s,a)(r+V\*(s’)) }}

 

We call this the “Bellman Optimality Equation” for the state-value function.

 

\---

 

We can do a similar thing to get the “Bellman Optimality Equation” for the action-value function.

 

Q\*(s,a) = E\[R(t+1)+max\[a’\]{ Q\*(St+1,a’) } | S(t)=s,A(t)=a\]

Q\*(s,a) = sum\[s’,r\]{ p(s’,r | s,a)(r+max\[a’\]{ Q\*(s’,a) }}

 

\---

 

One last thing to talk about is, once we have the optimal value function, how do we implement the optimal policy?

 

The key point is the value function already takes into account future rewards, so nothing extra needs to be done in order to optimize the total expected future reward.

 

All we need to do is choose the action that yields the best value for the next state.

 

Notice how for the state-value function V, we need to do a look-ahead search, because V itself does not depend on a.

 

So implementation-wise, we need to do all the possible actions “a”, look at what state we arrive in, s’, and choose the one that gives us the largest V(s’).

 

If we have Q(s,a), we can do this lookup directly.

 

What Q(s,a) does then, is it effectively caches the results of all one-step ahead searches.

 

 

## Summary

 

In this lecture, we are going to summarize this section of the course.

 

You’ll notice that it was purely theoretical.

 

This was so we could setup all the prerequisites we need for the later sections.

 

In particular, we formalized the Markov Decision Process framework.

 

We talked about policies.

 

We talked about returns, which is the total future reward.

 

We talked about how to discount future rewards using the discount rate, gamma.

 

We more rigorously defined value function and looked at 2 different types of value functions. The state-value function and the action-value function.

 

We looked at the Bellman equation, which recursively defines the value function in terms of the value function at the next state.

 

We looked at the notion of optimality, and defined the optimal policy, optimal state-value function, and optimal action-value function.

 

Through these we were able to also recursively define the optimal value functions in terms of optimal value function at the next state.

 

These are called the “Bellman Optimality Equations”.

 

In the next section, we are going to begin looking at algorithms to compute the value functions for a given policy, and the optimal value functions and optimal policy.

 

# Dynamic Programming

 

## Iterative Policy Evaluation

 

In this section of the book, we are going to start looking at solutions to MDPs.

 

The entire last section was just to set the problem up and define terms.

 

As you saw, the centerpiece of the last section was the Bellman Equation.

 

In fact the Bellman equation can be used directly to solve for the value function.

 

V(s) = sum\[a\]{ pi(a | s) sum\[s’, r\]{ p(s’,r | s,a)(r+V(s’)) }}

 

If you look carefully, you’ll see that this is actually a set of |S| equations, with |S| unknowns, where S = set of all states.

 

In fact, it is a linear equation, which means it’s not that hard to solve.

 

In addition, a lot of the matrix entries will be 0, since probably the state transitions will be sparse.

 

However, this is not the approach we’ll take.

 

Instead, we’ll do what is called iterative policy evaluation .

 

\---

 

What is iterative policy evaluation?

 

Essentially, it means we apply the Bellman equation again and again and eventually it will just converge.

 

This makes sense, since, at the point we’ve found the solution - the left hand side will equal the right hand side, so any further iteration won’t change anything.

 

We can write down the algorithm as follows:

 

`def iterative_policy_evaluation(𝜋):`

`initialize V(s) = 0 for all s ∈ S`

`while True:`

`𝛥 = 0`

`for each s ∈ S:`

`old_v = V(s)`

`V(s)=sum[a]{pi(a | s)sum[s’,r]{p(s’,r | s,a)(r+V(s’))}}`

`𝛥 = max(𝛥, |V(s) - old_v|)`

`if 𝛥 < threshold: break`

`return V(s)`

 

The input into iterative policy evaluation is a policy pi, and the output is the value function for this policy.

 

We start out initializing V(s) to 0 for all states. Then in an infinite loop, we initialize a variable called 𝛥. 𝛥 represents the maximum change during the current iteration. We’ll use 𝛥 to determine when to quit. When 𝛥 is small enough, that’s when we’ll break out of the loop.

 

Then for every state in the state space, we keep a copy of the old V(s), and then we use Bellman’s equation to update V(s).

 

We set 𝛥 to be the maximum change in V(s) for that iteration.

 

Once this converges, we return V(s).

 

\---

 

The main point of interest in the algorithm is of course the part that contains the Bellman equation.

 

V [k+1]  (s) = sum\[a\]{ pi(a | s) sum\[s’, r\]{ p(s’,r | s,a)(r+V [k]  (s’)) }}

 

Notice how, strictly speaking, the values at iteration k+1 depend only on the values at iteration k.

 

However, this need not be the case.

 

In fact, we can always just use our most up-to-date versions of the value function for any state by doing an in-place update.

 

This actually ends up converging faster.

 

\---

 

One last note:

 

We usually call the act of finding the value function for a given policy, the prediction problem .

 

Later in this section, we’ll learn an algorithm for finding the optimal policy. This is called the control problem .

 

So this will be the pattern we’ll follow in all of the remaining sections of the book.

 

We’ll first look at the prediction problem to find the value function for a given policy, and then we’ll look at the control problem to find the optimal policy.

 

 

## Gridworld in Code

 

In this section we are going to implement Gridworld in code. This is required for all the subsequent scripts in this course, so you’ll need to understand it now.

 

The relevant file for this section is grid\_world.py

 

`import numpy as np`

` `

` `

`class Grid: # Environment`

`def __init__(self, width, height, start):`

`self.width = width`

`self.height = height`

`self.i = start[0]`

`self.j = start[1]`

` `

`def set(self, rewards, actions):`

`# rewards should be a dict of: (i, j): r (row, col): reward`

`# actions should be a dict of: (i, j): A (row, col): list of possible actions`

`self.rewards = rewards`

`self.actions = actions`

` `

` `

` `

` `

` `

` `

` `

` `

` `

` `

` `

` `

` `

` `

` `

` `

` `

` `

` `

` `

 

The constructor takes in the width, height, and start position. The start position should be a tuple of 2 integers, and the current location will be stored in the instance variables “i” and “j”.

 

Next we have a setter that can set the rewards and the actions of the environment simultaneously.

 

The actions, to be clear, enumerate all the possible actions that take you to a new state.

 

So for example, if there is a wall above you, you could do the action “up”, but you wouldn’t actually go “up”, since that wouldn’t be in this actions dictionary. The Grid class will simply ignore it.

 

So both rewards and actions will be dictionaries, where the key is the (i, j) coordinate representing the state, and the value (dictionary value, not MDP value - see why “value” is a bad name?) is either a numerical reward or a list of possible actions. You’ll see later that the actions will be represented by the strings “U”, “D”, “L”, and “R”.

 

`def set_state(self, s):`

`self.i = s[0]`

`self.j = s[1]`

 

Next we have the set\_state function. This function will be useful for the various algorithms we’ll be using. For example, iterative policy evaluation requires us to loop through all the states and then do an action to get to the next state.

 

In order to know what the next state is, we have to actually put the agent into that state, do the action, and then determine the next state.

 

We don’t automatically have a master list of state transitions, we just need to figure them out by playing the game.

 

`def current_state(self):`

`return (self.i, self.j)`

 

Next we have the current\_state() function. This tells us the current (i, j) position of the agent.

 

`def is_terminal(self, s):`

`return s not in self.actions`

 

Next we have the is\_terminal() function. This returns a boolean - true if the argument “s” is a terminal state, false if not.

 

An easy way to determine if we’re in a terminal state is to check if the state is in the actions dictionary. If you can do an action from the state, then you can transition to a different state, and if that’s the case then your state is not terminal.

 

\---

 

Next we have the move() function. This takes in the action as an argument.

 

`def move(self, action):`

`# check if legal move first`

`if action in self.actions[(self.i, self.j)]:`

`if action == 'U':`

`self.i -= 1`

`elif action == 'D':`

`self.i += 1`

`elif action == 'R':`

`self.j += 1`

`elif action == 'L':`

`self.j -= 1`

`# return a reward (if any)`

`return self.rewards.get((self.i, self.j), 0)`

 

The first thing the function does is check if the action is in the actions dictionary. If it’s not, then we can’t do this movement on the grid, so we simply stay in the same position.

 

Otherwise, we do the action. Note that we follow array conventions here, so “i” is 0 at the top, and increases downward. “j” is 0 at the left and increases going right.

 

At the end, we return the reward for the current position from the rewards dictionary. The current position can be a new position after taking the action, or it can simply be the same position, if the action that was passed in, did not result in any movement. Note that if there is no reward defined for this position, the default is just 0.

 

\---

 

Next, we have the undo\_move() function. The idea is, you would pass in the action you just did, and the environment will undo it. So if you just did “Up”, it’ll move you back down.

 

`def undo_move(self, action):`

`# these are the opposite of what U/D/L/R should normally do`

`if action == 'U':`

`self.i += 1`

`elif action == 'D':`

`self.i -= 1`

`elif action == 'R':`

`self.j -= 1`

`elif action == 'L':`

`self.j += 1`

`# raise an exception if we arrive somewhere we shouldn't be`

`# should never happen`

`assert(self.current_state() in self.all_states())`

 

At the end, there’s a sanity check, to ensure that the current state is in the set of all allowed states. The code should never reach this point which is why we put an assert there.

 

\---

 

Next, similar to the tic-tac-toe game, we have the game\_over function, which returns true if the game is over and false if not.

 

`def game_over(self):`

`# returns true if game is over, else false`

`# true if we are in a state where no actions are possible`

`return (self.i, self.j) not in self.actions`

 

In this scenario, game over is much easier since all we need to do is check if we’re in a terminal state.

 

\---

 

Lastly, we have the all\_states function, which we used earlier in undo\_move. We can calculate all the states simply by enumerating all the states from which we can take an action, which don’t include the terminal states, and all the states that return a reward, which do include the terminal states.

 

`def all_states(self):`

`# possibly buggy but simple way to get all states`

`# either a position that has possible next actions`

`# or a position that yields a reward`

`return set(self.actions.keys() + self.rewards.keys())`

 

Since there might be some states in both the actions keys and the rewards keys, we cast it to a set. This also makes the data structure O(1) search.

 

\---

 

Next we have the standard grid function, which returns what I’ll refer to as the standard grid.

 

`def standard_grid():`

`# define a grid that describes the reward for arriving at each state`

`# and possible actions at each state`

`# the grid looks like this`

`# x means you can't go there`

`# s means start position`

`# number means reward at that state`

`# . . . 1`

`# . x . -1`

`# s . . .`

`g = Grid(3, 4, (2, 0))`

`rewards = {(0, 3): 1, (1, 3): -1}`

`actions = {`

`(0, 0): ('D', 'R'),`

`(0, 1): ('L', 'R'),`

`(0, 2): ('L', 'D', 'R'),`

`(1, 0): ('U', 'D'),`

`(1, 2): ('U', 'D', 'R'),`

`(2, 0): ('U', 'R'),`

`(2, 1): ('L', 'R'),`

`(2, 2): ('L', 'R', 'U'),`

`(2, 3): ('L', 'U'),`

`}`

`g.set(rewards, actions)`

`return g`

 

This is a grid that has the reward structure I showed you earlier, with +1 reward at the top right and -1 reward underneath it, and both of those are terminal states.

 

All the actions are defined such that we can move within the grid, but never off it. We also can’t walk into the wall, nor can we walk out of a terminal state.

 

\---

 

Next we have the negative\_grid function. The idea behind this is that we want to penalize each move.

 

`def negative_grid(step_cost=-0.1):`

`# in this game we want to try to minimize the number of moves`

`# so we will penalize every move`

`g = standard_grid()`

`g.rewards.update({`

`(0, 0): step_cost,`

`(0, 1): step_cost,`

`(0, 2): step_cost,`

`(1, 0): step_cost,`

`(1, 2): step_cost,`

`(2, 0): step_cost,`

`(2, 1): step_cost,`

`(2, 2): step_cost,`

`(2, 3): step_cost,`

`})`

`return g`

 

Recall earlier when we talked about solving a maze. We said that a robot that just moved randomly would eventually solve the maze, and if you only gave it a reward for solving the maze, then it would never learn anything beyond a random strategy.

 

We learned that we could incentivize the robot to solve the maze more efficiently by giving it a negative reward for each step taken.

 

And so that’s what we’re doing here. We’re incentivizing the robot to solve the maze efficiently, rather than moving randomly until it hits the goal.

 

You’ll see in the code samples how these 2 reward structures can affect the policy that the agent eventually learns.

 

 

## Iterative Policy Evaluation in Code

 

In this section, we are going to implement iterative policy evaluation in code.

 

To demonstrate how we can find the value function for different policies, we’re going to do iterative policy evaluation on 2 different policies.

 

The first policy we’ll look at is a completely random policy.

 

Remember, there are 2 probability distributions involved in Bellman’s equation, there’s pi(a | s), and there’s the Markov state-transition probability, p(s’, r | s, a).

 

Which one do you think is relevant for implementing Bellman’s equation?

 

\---

 

The answer is, pi(a | s). This is the probability that I do an action a, given I’m in a state s.

 

For a uniformly random policy, this probability will be 1 / number of possible actions from the state s.

 

The other probability, p(s’, r | s, a), is only relevant when the state transitions themselves are random.

 

That’s a scenario where, you try to move left, but instead you end up going right.

 

\---

 

The second policy we’ll look at is a completely deterministic policy. I’ve pasted it here for your convenience.

 

`---------------------------`

`R | R | R | |`

`---------------------------`

`U | | R | |`

`---------------------------`

`U | R | R | U |`

`---------------------------`

 

From the start position, you go directly to the goal state. That’s U/U/R/R/R.

 

However, if you’re starting from ANY other state, the policy is to go directly to the losing state.

 

So we should expect the values along the upper-left path to be positive, and the values of the other states to be negative.

 

Let’s now get to the code.

 

\---

 

`import numpy as np`

`from grid_world import standard_grid`

` `

`SMALL_ENOUGH = 10e-4 # threshold for convergence`

 

We start out with our usual imports, and from grid\_world we import the standard grid.

 

We define a threshold for convergence, called “small enough” and we set that to 10^-4.

 

Next we have 2 functions to help us visualize policies and values.

 

`def print_values(V, g):`

`for i in xrange(g.width):`

`print "---------------------------"`

`for j in xrange(g.height):`

`v = V.get((i,j), 0)`

`if v >= 0:`

`print " %.2f|" % v,`

`else:`

`print "%.2f|" % v, # -ve sign takes up an extra space`

`print ""`

` `

` `

`def print_policy(P, g):`

`for i in xrange(g.width):`

`print "---------------------------"`

`for j in xrange(g.height):`

`a = P.get((i,j), ' ')`

`print " %s |" % a,`

`print ""`

 

The first function is print\_values. It takes in a values dictionary V and a grid g.

 

It draws the grid, and in each position, it prints the value.

 

Print\_policy is pretty much the same, except it takes in a policy P instead of a value function V.

 

Similar to V, it’s keyed by the (i, j) coordinate representing the state, but the value is an action.

 

Note that this will only work for deterministic policies, since we can’t print more than one thing per location.

 

\---

 

Next we have the main section of the script.

 

`if __name__ == '__main__':`

`grid = standard_grid()`

`states = grid.all_states()`

` `

`### uniformly random actions ###`

`# initialize V(s) = 0`

`V = {}`

`for s in states:`

`V[s] = 0`

`gamma = 1.0 # discount factor`

 

As we stated earlier, we are using the standard grid.

 

We get the set of all states from the grid, since these will be the keys to the value function dictionary.

 

Next, we do iterative policy evaluation for uniformly random actions.

 

The first step is to initialize all V(s) to 0.

 

We then set the discount factor to 1.

 

Then we enter an infinite loop, and inside the loop, we loop through all the states.

 

`while True:`

`biggest_change = 0`

`for s in states:`

`old_v = V[s]`

` `

`# V(s) only has value if it's not a terminal state`

`if s in grid.actions:`

` `

`new_v = 0 # we will accumulate the answer`

`p_a = 1.0 / len(grid.actions[s]) # each action has equal probability`

`for a in grid.actions[s]:`

`grid.set_state(s)`

`r = grid.move(a)`

`new_v += p_a * (r + gamma * V[grid.current_state()])`

`V[s] = new_v`

`biggest_change = max(biggest_change, np.abs(old_v - V[s]))`

` `

`if biggest_change < SMALL_ENOUGH:`

`break`

 

We keep a copy of the old V(s) so that we can keep track of the magnitude of each change.

 

Next, we loop through all the possible actions from this state.

 

We use the variable new\_v to accumulate the answer, since it’ll be the sum over different actions.

 

The probability of any action is 1 / # of possible actions.

 

And this is where the look-ahead operation we talked about earlier comes into play.

 

We have to first set the state to “s”, and then do the action, so that we can determine the next state s’, since that is required to use Bellman’s equation.

 

Then, we add the term from Bellman’s equation to the variable new\_v.

 

Once the loop is done, we set V(s) to new\_v, and we update biggest\_change to be the max between all previous biggest changes and the new change.

 

Now that loop is done, so we can check if the biggest change is less than our threshold. If it is, we break out of the loop.

 

`print "values for uniformly random actions:"`

`print_values(V, grid)`

 

Once we’re done, we call the print\_values function for the values we just found.

 

\---

 

Next, we move on to our fixed policy.

 

We first print the policy so that you know what it looks like.

 

`### fixed policy ###`

`policy = {`

`(2, 0): 'U',`

`(1, 0): 'U',`

`(0, 0): 'R',`

`(0, 1): 'R',`

`(0, 2): 'R',`

`(1, 2): 'R',`

`(2, 1): 'R',`

`(2, 2): 'R',`

`(2, 3): 'U',`

`}`

`print_policy(policy, grid)`

 

Next, we re-initialize all V(s) to 0.

 

`# initialize V(s) = 0`

`V = {}`

`for s in states:`

`V[s] = 0`

 

This time, we’re going to set our discount factor to 0.9, so the value is going to decrease the further away we get from the goal state.

 

`# let's see how V(s) changes as we get further away from the reward`

`gamma = 0.9 # discount factor`

 

And then we enter the same loop as before. Notice how it’s a simpler loop. We don’t need to loop through any actions because there’s only ONE action per state.

 

Because there’s only ONE action per state, the probability of that action in that state is 1.

 

`# repeat until convergence`

`while True:`

`biggest_change = 0`

`for s in states:`

`old_v = V[s]`

` `

`# V(s) only has value if it's not a terminal state`

`if s in policy:`

`a = policy[s]`

`grid.set_state(s)`

`r = grid.move(a)`

`V[s] = r + gamma * V[grid.current_state()]`

`biggest_change = max(biggest_change, np.abs(old_v - V[s]))`

` `

`if biggest_change < SMALL_ENOUGH:`

`break`

`print "values for fixed policy:"`

`print_values(V, grid)`

 

The rest of the loop is the same, and when it’s done we print the values again.

 

\---

 

Results:

 

`values for uniformly random actions:`

`---------------------------`

`-0.03| 0.09| 0.22| 0.00|`

`---------------------------`

`-0.16| 0.00| -0.44| 0.00|`

`---------------------------`

`-0.29| -0.41| -0.54| -0.77|`

` `

` `

` `

`---------------------------`

`R | R | R | |`

`---------------------------`

`U | | R | |`

`---------------------------`

`U | R | R | U |`

`values for fixed policy:`

`---------------------------`

`0.81| 0.90| 1.00| 0.00|`

`---------------------------`

`0.73| 0.00| -1.00| 0.00|`

`---------------------------`

`0.66| -0.81| -0.90| -1.00|`

 

So you can see that most of the values for the uniform random policy are negative. That’s because if you’re moving randomly, there’s a good change you can end up in the losing state.

 

Remember that there are two ways you can enter the losing state, but only one way you can enter the goal state.

 

The most negative value is for the state right underneath the losing state, which makes sense.

 

Now for the fixed policy and discount factor 0.9, we see what we expect to see. The further away we get from the terminal state, the more the value decreases, and each time it decreases by exactly 10%. So 0.81 is 0.9\*0.9, 0.73 is 0.81\*0.9, and so on.

 

 

## Policy Improvement

 

In this lecture, we are going to start discussing the control problem , or in other words, how to find better policies and eventually get to the optimal policy.

 

What we know so far is how to find the value function given a fixed policy.

 

Let’s look at our recursive definition of Q again.

 

Q(s,a) = sum\[s’,r\]{ p(s’,r | s,a)(r+V(s’)) }

 

This tells us the value of doing action a while in state s, using the policy pi.

 

\---

 

Using the current policy, we simply get the current state-value function.

 

V(s) = Q(s, pi(s)) = sum\[s’,r\]{ p(s’,r | s, pi(s))(r+V(s’)) }

 

But let’s say we want to change just one of the actions in the policy. Can we do this?

 

Of course we can!

 

\---

 

We have a finite set of actions, so all we need to do is pick one that gives us a bigger Q than pi(s) does.

 

find a in A s.t. Q(s,a) > Q(s,pi(s))

 

This is where doing all the programming exercises becomes really useful. This looks like a really abstract equation, but all it’s saying is, if the policy is current to go “Up”, let’s look at if “Left”, “Right”, or “Down” give us a bigger Q.

 

And if it does, let’s change our policy for that state to this new action.

 

\---

 

Formally speaking, what we’re doing when we choose a new action for this state, is finding a new policy pi’, that has a bigger value for this state than pi.

 

pi <= pi’ <--> V(s | pi) <= V’(s | pi’)

pi’(s) = argmax\[a\]{ Q(s,a) }

pi’(s) = argmax\[a\]{ sum\[s’,r\]{ p(s’,r | s,a)(r+V(s’)) }}

 

And all we need to do this, is to pick an action that gives us maximum Q.

 

Notice how we can write this in the form where we’re using Q, or in the form where we’re doing a lookahead search on V.

 

\---

 

There are 2 things about policy improvement you should notice.

 

First, notice that it’s greedy. We’re never considering globally the value function at all states. We’re only looking at the current state, and picking the best action based on the value function at that state.

 

Second, notice that it uses an imperfect version of the value function.

 

Once we change pi, V(s) is different.

 

You’ll see in later sections, why this is not a problem.

 

One question you might have is - how do we know when we are finished improving the policy? When we’ve found the optimal policy, the policy won’t change with respect to the value function.

 

In addition, the value function will no longer improve, it’ll stay constant.

 

Notice how the inequality we had earlier was “less than or equal to”. So in the case where it’s strictly less than, then we are improving the policy. In the case where it’s equal to, then there’s no more improvement to be made, and we’ve found the optimal policy.

 

 

 

## Policy Iteration

 

In this section we are going to discuss the algorithm we’ll use to find the optimal policy.

 

It’ll solve the problem we encountered in the previous lecture. Specifically, when we change the policy, the value also changes and becomes out of date.

 

In this section we’ll see how we can rectify that problem.

 

\---

 

What do we do when we change the policy and the value function becomes out of date?

 

Well we can simply re-calculate the value function.

 

Luckily, we already know how to do this, because we wrote code to do it, and the algorithm we used is called “iterative policy evaluation”.

 

At a high-level, the algorithm is very simple.

 

We just alternate between policy evaluation, and policy improvement.

 

We keep doing this until the policy doesn’t change anymore.

 

Note that what we are not checking for is the value function converging, although it will anyway because once the policy stops changing, we only need to do one more iteration of policy evaluation.

 

\---

 

In pseudocode, policy iteration looks like this.

 

Step 1 is to randomly initialize V(s) and the policy pi(s).

 

`V(s) = random, pi(s) = random`

 

Step 2 is to do iterative policy evaluation to find the current V(s).

 

`V(s) = iterative_policy_evaluation(pi) # we wrote this already in the last section`

 

Step 3 is to do policy improvement, which we’ll write out more elaborately here since you haven’t seen this before.

` `

`policy_changed = False`

`for s in all_states:`

`old_a = policy(s)`

`policy(s) = argmax[a]{ sum[s’,r]{ p(s’,r | s,a)[r + gamma*V(s’) } }`

`if policy(s) != old_a: policy_changed = True`

`if policy_changed: go back to step 2`

 

We initialize a flag that tells us if the policy has changed to False. Then we loop through all the states.

 

We keep a copy of the old policy for state s. Then we choose a new action based on the argmax of the lookahead value.

 

If the policy changes at any time during the loop, we go back to step 2, otherwise, we’re done.

 

 

## Policy Iteration in Code

 

In this section we are going to implement policy iteration in code.

 

If you don’t want to try to code this yourself, although I highly recommend you do, the relevant file in the course repo is policy\_iteration.py

 

We start out with our usual imports. From grid\_world we import both standard grid and negative grid.

 

`import numpy as np`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

 

We are going to use the negative grid, but you’re encouraged to try the standard grid to see if the agent will still find a good policy.

 

Next we define some constants. We again have our threshold for finding V(s) called SMALL\_ENOUGH, we have GAMMA which is our discount factor, and we have ALL\_POSSIBLE\_ACTIONS which are the 4 directions on the grid.

 

`SMALL_ENOUGH = 10e-4`

`GAMMA = 0.9`

`ALL_POSSIBLE_ACTIONS = ('U', 'D', 'L', 'R')`

 

Next I’ve written a little comment so that you remember that this world is deterministic, when you try to go up, you go up. So the transition probability is always 1 or 0.

 

`# this is deterministic`

`# all p(s',r|s,a) = 1 or 0`

 

Next we go to the main section.

 

First we get the negative\_grid, with the default step cost of -0.1.

 

`if __name__ == '__main__':`

`# this grid gives you a reward of -0.1 for every non-terminal state`

`# we want to see if this will encourage finding a shorter path to the goal`

`grid = negative_grid()`

 

Next we print the rewards, so you remember what they look like. Notice how we can just use the print\_values function for this, since it will print any dictionary with the location as the key and a number of as the value.

 

`print "rewards:"`

`print_values(grid.rewards, grid)`

 

Next, we create a deterministic random policy. We just randomly choose an action out of the possible actions for every state.

 

`policy = {}`

`for s in grid.actions.keys():`

`policy[s] = np.random.choice(ALL_POSSIBLE_ACTIONS)`

 

We then print the initial policy so you know what it looks like.

 

`# initial policy`

`print "initial policy:"`

`print_policy(policy, grid)`

 

Next, we initialize V(s) randomly. We know that the value of any terminal state is 0, so we initialize these to 0.

 

`# initialize V(s)`

`V = {}`

`states = grid.all_states()`

`for s in states:`

`# V[s] = 0`

`if s in grid.actions:`

`V[s] = np.random.random()`

`else:`

`# terminal state`

`V[s] = 0`

 

Next, we enter the main loop, which alternates between policy evaluation and policy improvement.

 

`# repeat until convergence - will break out when policy does not change`

`while True:`

` `

`# policy evaluation step - we already know how to do this!`

`while True:`

`biggest_change = 0`

`for s in states:`

`old_v = V[s]`

` `

`# V(s) only has value if it's not a terminal state`

`if s in policy:`

`a = policy[s]`

`grid.set_state(s)`

`r = grid.move(a)`

`V[s] = r + GAMMA * V[grid.current_state()]`

`biggest_change = max(biggest_change, np.abs(old_v - V[s]))`

` `

`if biggest_change < SMALL_ENOUGH:`

`break`

` `

`# policy improvement step`

`is_policy_converged = True`

`for s in states:`

`if s in policy:`

`old_a = policy[s]`

`new_a = None`

`best_value = float('-inf')`

`# loop through all possible actions to find the best current action`

`for a in ALL_POSSIBLE_ACTIONS:`

`grid.set_state(s)`

`r = grid.move(a)`

`v = r + GAMMA * V[grid.current_state()]`

`if v > best_value:`

`best_value = v`

`new_a = a`

`policy[s] = new_a`

`if new_a != old_a:`

`is_policy_converged = False`

` `

`if is_policy_converged:`

`break`

 

The first step is of course policy evaluation.

 

This is just the same code from before, but notice how it’s the “easy” version since all of the actions, next states, and rewards are deterministic.

 

Next, we have the policy improvement step.

 

We have a flag called is\_policy\_converged which we initialize to True.

 

We then loop through all the states and grab the existing action and assign that to old\_a.

 

We then loop through all the possible actions, to search for the best new lookahead value.

 

We choose the action that gives us the best value, and then we update our policy.

 

If new\_a is != old\_a, we set is\_policy\_converged to False.

 

Once we’re out of the policy improvement loop, we check if the policy has changed, and if it hasn’t, we break out of the main loop.

 

At the end, we print the final values and the final policy.

 

`print "values:"`

`print_values(V, grid)`

`print "policy:"`

`print_policy(policy, grid)`

 

\---

 

Results:

 

`rewards:`

`---------------------------`

`-0.10| -0.10| -0.10| 1.00|`

`---------------------------`

`-0.10| 0.00| -0.10| -1.00|`

`---------------------------`

`-0.10| -0.10| -0.10| -0.10|`

`initial policy:`

`---------------------------`

`L | U | L | |`

`---------------------------`

`U | | U | |`

`---------------------------`

`R | R | L | D |`

`values:`

`---------------------------`

`0.62| 0.80| 1.00| 0.00|`

`---------------------------`

`0.46| 0.00| 0.80| 0.00|`

`---------------------------`

`0.31| 0.46| 0.62| 0.46|`

`policy:`

`---------------------------`

`R | R | R | |`

`---------------------------`

`U | | U | |`

`---------------------------`

`U | R | U | L |`

 

Notice how, if we find ourselves in the position below the wall, the agent decides to go right rather than left and around the top-left corner.

 

This is because each step costs a little bit of reward, and future rewards are discounted, so we want to try to get to the goal state in as few steps of possible.

 

In later lectures, we will encounter solutions where the agent decides to go left instead of right.

 

 

## Policy Iteration for Windy Gridworld

 

In this lecture, I’m going to describe to you a modification of our environment called “Windy Gridworld”.

 

Recall that we have 2 probability distributions to deal with.

 

First there’s pi(a | s), which is the probability of doing action a when in state s.

 

And then there’s the state transition probability p(s’,r | s,a). So far this has been deterministic. When we do action a in state s, we always end up in the same state s’.

 

This is also tied to the reward, since Gridworld gives you a reward based on the state you land in.

 

In this lecture, we’re going to consider the case where this probability distribution is not deterministic, or in other words, the probability will have a value between 0 and 1.

 

\---

 

This is where Windy Gridworld comes into play.

 

Imagine you’re walking through a windy street. You try to walk straight but the wind pushes you backwards or to the left.

 

The same thing is going to happen to our agent. The agent will try to go “up”, but sometimes, the environment will push it in some other direction instead.

 

In our case, we’ll set the probability of doing the intended action to be 0.5, and the probability of the other 3 actions to be 0.5/3.

 

We will again be looking at code for policy iteration, which also covers policy evaluation since it’s already part of the main loop.

 

If you don’t want to code this yourself, although I highly recommend you do, the relevant file for this lecture is policy\_iteration\_random.py

 

\---

 

At the top most of the stuff was just copied and pasted from the initial policy\_iteration script.

 

`import numpy as np`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

` `

`SMALL_ENOUGH = 10e-4`

`GAMMA = 0.9`

`ALL_POSSIBLE_ACTIONS = ('U', 'D', 'L', 'R')`

` `

`# next state and reward will now have some randomness`

`# you'll go in your desired direction with probability 0.5`

`# you'll go in a random direction a' != a with probability 0.5/3`

` `

`if __name__ == '__main__':`

`grid = negative_grid(step_cost=-1.0)`

 

One of the main differences with this script, other than the fact that we’re now in probabilistic windy Gridworld, is I’ve changed the step cost.

 

What happens when we set the step cost to -1?

 

Since the goal only gives you +1 reward, and the losing state gives you a -1 reward, you’ll see that the agent actually wants to end the game as soon as possible, even if this means ending up in the losing state.

 

For example, if you’re 3 steps away from the goal, you’d get -3 reward before you have a chance to get to the goal. But if you’re only 1 step away from the losing state, then you only get -1 reward.

 

Remember that the goal of the agent isn’t to get to what we’ve defined as the winning or losing states. All it does is try to maximize its reward.

 

So I’d recommend trying different grids with different step costs to observe what happens.

 

Next we print the rewards so you know what they look like.

 

`print "rewards:"`

`print_values(grid.rewards, grid)`

 

Then we generate a random policy and a random value function. Same stuff from the deterministic script.

 

`# state -> action`

`# we'll randomly choose an action and update as we learn`

`policy = {}`

`for s in grid.actions.keys():`

`policy[s] = np.random.choice(ALL_POSSIBLE_ACTIONS)`

` `

`# initial policy`

`print "initial policy:"`

`print_policy(policy, grid)`

` `

`# initialize V(s)`

`V = {}`

`states = grid.all_states()`

`for s in states:`

`# V[s] = 0`

`if s in grid.actions:`

`V[s] = np.random.random()`

`else:`

`# terminal state`

`V[s] = 0`

 

Next comes the main loop.

 

The first step is policy evaluation. Notice how we now have to add in the state transition probability.

 

`# repeat until convergence - will break out when policy does not change`

`while True:`

` `

`# policy evaluation step - we already know how to do this!`

`while True:`

`biggest_change = 0`

`for s in states:`

`old_v = V[s]`

` `

`# V(s) only has value if it's not a terminal state`

`new_v = 0`

`if s in policy:`

`for a in ALL_POSSIBLE_ACTIONS:`

`if a == policy[s]:`

`p = 0.5`

`else:`

`p = 0.5/3`

`grid.set_state(s)`

`r = grid.move(a)`

`new_v += p*(r + GAMMA * V[grid.current_state()])`

`V[s] = new_v`

`biggest_change = max(biggest_change, np.abs(old_v - V[s]))`

` `

`if biggest_change < SMALL_ENOUGH:`

`break`

 

Keep in mind, the policy itself is deterministic. There are 2 probabilities we can play with here, but we’re only playing with state transitions at this time.

 

So we loop through all the possible actions. If the action is the one from the policy, the probability of that actually happening is 0.5 Otherwise, it’s 0.5/3.

 

Next we have the policy improvement step. This is again very similar to the deterministic policy iteration script, except now we have an extra loop over the action space.

 

`# policy improvement step`

`is_policy_converged = True`

`for s in states:`

`if s in policy:`

`old_a = policy[s]`

`new_a = None`

`best_value = float('-inf')`

`# loop through all possible actions to find the best current action`

`for a in ALL_POSSIBLE_ACTIONS: # chosen action`

`v = 0`

`for a2 in ALL_POSSIBLE_ACTIONS: # resulting action`

`if a == a2:`

`p = 0.5`

`else:`

`p = 0.5/3`

`grid.set_state(s)`

`r = grid.move(a2)`

`v += p*(r + GAMMA * V[grid.current_state()])`

`if v > best_value:`

`best_value = v`

`new_a = a`

`policy[s] = new_a`

`if new_a != old_a:`

`is_policy_converged = False`

` `

`if is_policy_converged:`

`break`

 

Again the probability of actually doing the chosen action is 0.5, and the probability of actually doing any other action is 0.5/3.

 

Everything else is the same, we print the values and the final policy at the end.

 

\---

Results:

 

`rewards:`

`---------------------------`

`-1.00| -1.00| -1.00| 1.00|`

`---------------------------`

`-1.00| 0.00| -1.00| -1.00|`

`---------------------------`

`-1.00| -1.00| -1.00| -1.00|`

`initial policy:`

`---------------------------`

`U | U | D | |`

`---------------------------`

`D | | R | |`

`---------------------------`

`U | U | D | U |`

`values:`

`---------------------------`

`-4.52| -2.95| -0.86| 0.00|`

`---------------------------`

`-5.57| 0.00| -1.94| 0.00|`

`---------------------------`

`-5.76| -4.88| -3.44| -2.17|`

`policy:`

`---------------------------`

`R | R | R | |`

`---------------------------`

`U | | R | |`

`---------------------------`

`R | R | U | U |`

 

Notice the policy near the losing state. Since state transitions are random, what action you choose is not always the action that results, but it still has the highest chance of occurring.

 

Therefore, when we’re close to the losing state, it’s better for the agent to just try to lose, which will end up terminating the episode and maximizing the future reward.

 

 

## Value Iteration

 

In this section we are going to talk about an alternative technique for solving the control problem, called value iteration.

 

Recall that the technique we previously studied was called policy iteration.

 

It’s very easy to get all of these confused, because all the algorithms look and sound the same, so coding them will definitely help you get used to the different varieties of solutions we have for MDPs.

 

One of the disadvantages of policy iteration is that it’s an iterative algorithm.

 

Therefore, we have to wait for it to converge.

 

At the same time, the main loop contains 2 steps, and the first step itself is also an iterative algorithm.

 

So you have one iterative algorithm inside another one.

 

One might ask if there’s a more efficient way to go about solving this problem.

 

\---

 

Recall that the policy evaluation algorithm ends when V converges.

 

It’s reasonable to ask, is there a point before convergence, such that the resulting greedy policy doesn’t change?

 

In fact, empirical studies have shown that after only a few iterations of policy evaluation, the resulting greedy policy is constant.

 

What this tells us is that we actually don’t need to wait for policy evaluation to converge when we’re doing policy iteration.

 

We can just do a few steps and then break, because the policy improvement step would find the same policy given additional iterations of policy evaluation.

 

\---

 

However, the algorithm we’re studying in this lecture takes this one step further. It’s called value iteration.

 

What it does is combines the policy evaluation and the policy improvement step into one line.

 

V [k+1]  (s)=max\[a\]{ sum\[s’, r\]{ p(s’,r | s,a)(r+V [k]  (s’)) }}

 

What’s interesting about this is it looks almost exactly like the equations we’ve already seen. In fact if you weren’t paying attention, it would look exactly like the equations we’ve already seen.

 

That’s why I’ve been saying it’s really important to write code to try and understand the differences.

 

You really need to look at this carefully to see what the difference is between this and the other Bellman-type equations we’ve looked at.

 

This equation is very similar to the policy evaluation equation, except we’re taking the max over all possible actions.

 

\---

 

It’s also iterative as you can see with the k index.

 

Similar to policy evaluation, we don’t actually need to wait for the entire kth iteration of V to be available before we start calculating the (k+1)th iteration of V.

 

We can just update it “in-place”.

 

Notice how this does both policy evaluation and policy improvement all in one step.

 

This is because policy improvement occurs by taking the ARGMAX of the expression on the right.

 

So by just taking the max, we’re doing the policy evaluation step on the policy we would have chosen if we had taken the argmax.

 

\---

 

Let’s write all that out in pseudocode so you have another chance to look at it.

 

Step 1 is to initialize V arbitrarily. This can be random numbers or all 0s. It doesn’t really matter so much.

 

Then we enter an infinite loop. Just like policy evaluation, we keep track of the biggest change and break out of the loop when the biggest change falls under some threshold, indicating convergence.

 

The only difference between this and policy evaluation, is that we’re taking the max over all actions for the Bellman equation on the right.

 

After we’ve converged, we can output the policy pi(s) by taking the argmax over every V(s).

 

`initialize V(s) = 0 for all s ∈ S`

` `

`while True:`

`𝛥 = 0`

`for each s ∈ S:`

`old_v = V(s)`

`V(s)= max[a]{ sum[s’,r]{ p(s’,r | s,a)(r+V(s’)) }}`

`𝛥 = max(𝛥, |V(s) - old_v|)`

`if 𝛥 < threshold: break`

` `

`for each s ∈ S:`

`pi(s) = argmax[a]{ sum[s’,r]{ p(s’,r | s,a)(r+V(s’)) }}`

 

 

## Value Iteration in Code

 

In this lecture we’ll be looking at value iteration in code.

 

If you don’t want to code this yourself, although I highly recommend you do, the relevant file for this lecture is value\_iteration.py

 

This script follows the exact same pattern as the previous 2 files, so even if you weren’t coding by yourself before, you can easily do so now, by copying and pasting the previous files and modifying them to implement the new algorithm.

 

At the top we have the same imports and the same constants as before.

 

`import numpy as np`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

` `

`SMALL_ENOUGH = 10e-4`

`GAMMA = 0.9`

`ALL_POSSIBLE_ACTIONS = ('U', 'D', 'L', 'R')`

 

Note that we’ve gone back to deterministic Gridworld, so it’s not windy and there’s no stochastic state transitions.

 

Now let’s go into the main section.

 

`if __name__ == '__main__':`

`# this grid gives you a reward of -0.1 for every non-terminal state`

`# we want to see if this will encourage finding a shorter path to the goal`

`grid = negative_grid()`

` `

`# print rewards`

`print "rewards:"`

`print_values(grid.rewards, grid)`

` `

`# state -> action`

`# we'll randomly choose an action and update as we learn`

`policy = {}`

`for s in grid.actions.keys():`

`policy[s] = np.random.choice(ALL_POSSIBLE_ACTIONS)`

` `

`# initial policy`

`print "initial policy:"`

`print_policy(policy, grid)`

` `

`# initialize V(s)`

`V = {}`

`states = grid.all_states()`

`for s in states:`

`# V[s] = 0`

`if s in grid.actions:`

`V[s] = np.random.random()`

`else:`

`# terminal state`

`V[s] = 0`

 

Same stuff as before, we get the negative grid, print the rewards so you know what they are, and initialize a random policy.

 

We print the initial random policy so you know what it is.

 

We initialize V(s) randomly.

 

Next we have the value iteration loop. It looks very similar to policy evaluation, except now we’re looping through all the possible actions and taking the maximum value.

 

`while True:`

`biggest_change = 0`

`for s in states:`

`old_v = V[s]`

` `

`# V(s) only has value if it's not a terminal state`

`if s in policy:`

`new_v = float('-inf')`

`for a in ALL_POSSIBLE_ACTIONS:`

`grid.set_state(s)`

`r = grid.move(a)`

`v = r + GAMMA * V[grid.current_state()]`

`if v > new_v:`

`new_v = v`

`V[s] = new_v`

`biggest_change = max(biggest_change, np.abs(old_v - V[s]))`

` `

`if biggest_change < SMALL_ENOUGH:`

`break`

 

We break when biggest\_change is below the small\_enough threshold.

 

Next, we take our optimal value function and find the optimal policy. Recall that this is just the argmax.

 

`# find a policy that leads to optimal value function`

`for s in policy.keys():`

`best_a = None`

`best_value = float('-inf')`

`# loop through all possible actions to find the best current action`

`for a in ALL_POSSIBLE_ACTIONS:`

`grid.set_state(s)`

`r = grid.move(a)`

`v = r + GAMMA * V[grid.current_state()]`

`if v > best_value:`

`best_value = v`

`best_a = a`

`policy[s] = best_a`

 

So we loop through all the actions, and we find the action that gives us the best future reward.

 

`print "values:"`

`print_values(V, grid)`

`print "policy:"`

`print_policy(policy, grid)`

 

And finally we print the values and we print the final policy.

 

We can confirm that we get the same answer as before.

 

 

## Summary

 

In this section we are going to summarize everything we did in this section.

 

In the last chapter, we defined the Markov Decision Process, and in this chapter, we looked at one method of finding solutions to MDPs called Dynamic Programming.

 

In particular, we looked at one way of solving the prediction problem, or in other words, finding the value function given a policy.

 

We looked at two ways of solving the control problem, or in other words, finding the optimal policy and optimal value function.

 

The first was called policy iteration, and it involved an iterative algorithm inside another iterative algorithm, which could be inefficient. We then looked at value iteration, which truncates the policy evaluation step, and combines both policy evaluation and policy iteration into one step.

 

\---

 

Notice how all the algorithms we looked at for dynamic programming involved looping through the entire set of states.

 

As we discussed earlier in the course, for more realistic games, the state space can be ridiculously large.

 

Therefore, even just one iteration of value iteration can take a very long time.

 

Also recall, that one way to speed up value iteration is to do the update “in-place”, meaning that we don’t exclusively use the values from the previous iteration to update the values in the current iteration.

 

We can take that a step further with what is called asynchronous value dynamic programming.

 

The modification is simple. Instead of looping through the entire state set, we loop through just a few or even just one of the states per iteration.

 

We can choose these states randomly or based on which states are more likely to be visited, and you could learn that information by having your agent play a few rounds of the game.

 

\---

 

Although we introduced policy iteration as a dynamic programming algorithm in this section, you’ll see that the main concept behind policy iteration will appear again and again throughout the course.

 

What is this main concept?

 

It’s that we iteratively perform 2 steps: policy evaluation, and policy improvement, and we just alternate between the 2 until we reach convergence.

 

The only way we can reach convergence, is when Bellman’s equation becomes true, or in other words, the value has converged for the given policy and the policy has stabilized with respect to greedy selection on the value function.

 

One way to visualize this process is with this 2-dimensional diagram. Initially, the policy and the value function can be highly suboptimal, but by requiring the policy to be greedy with respect to the value function, and the value function to be consistent with the policy, we can converge to the optimal policy and the optimal value function.

 

\---

 

We can talk a little bit about the efficiency of dynamic programming as well.

 

Let’s consider how much better it is than brute force search.

 

You’ll want to think about how you’d solve this problem using what you know from your algorithms class.

 

Let’s call the number of states N and the number of possible actions M

 

If we assume that the agent can go from the start state to the goal state in O(N) time, then we want a sequence of actions of length O(N).

 

The number of possible actions is then O(M^N).

 

How you would solve this practically, is you’d make a list of all the permutations of possible state sequences, and then do policy evaluation on all of them.

 

You’d then keep the policy that gives you the maximum value function.

 

This is exponential in the number of states, so you can see how dynamic programming is a much more efficient solution.

 

\---

 

Lastly, you may have noticed how the dynamic programming solutions require a full model of the environment.

 

In particular, the state transition probabilities. You can imagine that in the real world, these probabilities might be infeasible to measure, especially when the number of states is large.

 

You’ll see that for the remaining sections of the course, we’ll be exploring solutions that don’t require such a model of the environment. These are called “model-free” methods.

 

You also may have noticed that these iterative solutions require an initial estimate. In policy iteration and value iteration, we’re essentially making estimates from other estimates, going back and forth between the value function and the policy.

 

Making that initial estimate is called “bootstrapping”. You’ll see that the next method we’ll look at, Monte Carlo, does not require bootstrapping, while the method we’ll look at after that, called Temporal Difference Learning, will require bootstrapping.

 

# Monte Carlo

 

 

## Monte Carlo Introduction

 

In this chapter of the book, we are going to discuss another technique for solving MDPs, called Monte Carlo.

 

In the last section, Dynamic Programming, you may have noticed something strange.

 

We discussed early on in this course that reinforcement learning is all about learning from experience and playing games.

 

And yet, in none of the Dynamic Programming algorithms did we actually play the game!

 

We had a full model of the environment, which included all the state transition probabilities.

 

You might wonder, is it reasonable to assume that you would have such information in a real-life environment?

 

For board games, maybe, but what about self-driving cars?

 

The way that we implemented our Dynamic Programming algorithms required us to put the agent into a state.

 

That might not always be possible, especially when we’re talking about self-driving cars, or even video games.

 

A video game starts in the state that it decides, you can’t choose any state you want.

 

This is another instance of having “God-mode” capabilities.

 

So it’s not very realistic to assume that’s always possible.

 

In this section, which will focus on Monte Carlo methods, we will be playing the game as it was meant to be played, and we’ll be learning purely from experience.

 

\---

 

“Monte Carlo” is sort of a poorly defined term. Usually it refers to any algorithm that involves a significant random component.

 

With Monte Carlo methods in RL, the random component is the return.

 

Recall that what we are always looking for is the expected return given you’re in a state “s”.

 

With Monte Carlo methods, instead of calculating the true expected value, which requires probability distributions, we instead take the sample mean.

 

E.g.

 

`E(X) ~= sum[i=1..N]{ X(i) } / N`

 

In order for this to work, we need to assume we’re doing episodic tasks only.

 

The reason is because an episode has to terminate before we can calculate any of the returns.

 

This also means Monte Carlo methods are not “fully” online algorithms (like the multi-armed bandit). We don’t do an update after every action, but rather after every episode.

 

\---

 

The methods we use in the Monte Carlo section should be somewhat reminiscent of the multi-armed bandit problem.

 

With the multi-armed bandit problem, we were always averaging the reward after every action.

 

With MDPs, we’re always averaging the return.

 

One way to think of Monte Carlo, is that every state is a separate multi-armed bandit problem, and what we’re trying to do is learn to behave optimally for all of the multi-armed bandit problems at once.

 

\---

 

In this chapter, we are again going to follow the same pattern we did in the Dynamic Programming section.

 

We’ll start by looking at the prediction problem, or in other words, how to do policy evaluation.

 

Then we’ll look at the control problem, or in other words, how to find the optimal policy.

 

 

## Monte Carlo Prediction for the State-Value Function

 

In this section we are going to solve the prediction problem using Monte Carlo estimation.

 

Remember that the definition of the value function is it’s the expected value of the future return given that the current state is “s”.

 

V(s) = E\[G(t) | S(t)=s\]

 

We know that we can estimate any expected value simply by adding up samples and dividing by the total number of samples.

 

V(s) = (1/N) sum\[i=1..N\]{ G(i, s) }

 

In this equation, i is indexing the episode, and s is indexing the state.

 

The question is, how do we get these sampled returns?

 

\---

 

The answer is that we just need to play a bunch of episodes and generate them.

 

For every episode you play, you’ll have a sequence of states and rewards.

 

`s1 s2 s3 … sT`

`r1 r2 r3 … rT`

 

g(t) = r(t+1) + gamma\*g(t+1)

 

And from the rewards we can calculate the returns by definition, which is just the sum of all future rewards.

 

Notice how, to actually implement this in code, it would be very useful to loop through the states and rewards in reverse order, since G depends only on future values.

 

Once we’ve done this for many episodes, we’ll have multiple lists of s’s and G’s, and we can take the sample mean.

 

\---

 

One interesting question that comes up is - what if you see the same state more than once in an episode?

 

For instance, if you see state s at time = 1 and time = 3, what is the return for state s?

 

There are 2 answers to this question, and surprisingly they both lead to the same answer.

 

The first method is called “first-visit” Monte Carlo. That means, you would only count the return for time t = 1.

 

The second method is called “every-visit” Monte Carlo. That means, you would calculate the return for every time you visited the state s, and all of them would contribute to the sample mean.

 

It has been proven that both of these converge to the true value.

 

\---

 

Let’s now look at some pseudocode for Monte Carlo prediction - in particular, the “first-visit” version.

 

`def first_visit_monte_carlo_prediction(𝜋, N):`

`V = random initialization`

`all_returns = {} # default = []`

`do N times:`

`states, returns = play_episode`

`for s, g in zip(states, returns):`

`if not seen s in this episode yet:`

`all_returns[s].append(g)`

`V(s) = sample_mean(all_returns[s])`

`return V`

 

The input into this function is a policy and the number of samples we want to generate.

 

We initialize V randomly, and we create a dictionary to store our returns, with the default value being an empty list.

 

We loop N times. Inside the loop, we generate an episode by playing the game.

 

Next, we loop through the state sequence and return sequence.

 

We only include the return if this is the first time we’ve seen this state in this episode, since this is “first-visit” Monte Carlo.

 

If so, we add the return to our list of returns for this state.

 

Next, we update V(s) to be the sample mean of all the returns we’ve collected for this state.

 

At the end, we return V.

 

\---

 

One thing you may have noticed in the pseudocode is that it requires us to store all the returns we get for each state, so that the sample mean can be calculated.

 

But if you recall from the section on the multi-armed bandit, there are more efficient ways to calculate the mean, such as calculating it from the previous mean.

 

There are also techniques for nonstationary problems, like using a moving average.

 

So all the techniques you learned before still apply here.

 

\---

 

Another thing you should notice about the Monte Carlo method is that because we’re calculating the sample mean, all the same rules of probability apply.

 

That means, the confidence interval is approximately Gaussian, and the variance is the original variance of the data / number of samples collected.

 

Therefore, we are going to be more confident in data that has more samples, but it grows slowly with respect to the number of samples.

 

\---

 

For completion’s sake, I’m also going to show you pseudocode for calculating the returns.

 

`s = grid.current_state()`

`states_and_rewards = [(s, 0)]`

`while not game_over:`

`a = policy(s)`

`r = grid.move(a)`

`s = grid.current_state()`

`states_and_rewards.append((s, r))`

` `

`G = 0`

`states_and_returns = []`

`for s, r in reverse(states_and_rewards):`

`states_and_returns.append((s, G))`

`G = r + gamma*G`

`states_and_returns.reverse()`

 

The first block of code is for collecting the state and reward sequences. This is just playing the game, and keeping a log of all the states and rewards we get, in the order that we get them. Notice that this is a list of tuples.

 

Also notice that the first reward is assumed to be 0 - we don’t get any reward for simply arriving at the start state.

 

The second block of code is for calculating the returns.

 

We start out with an empty list, and then we loop through the states and rewards in reverse order.

 

Note that in the first iteration of this loop, the state s represents a terminal state, and G will be 0. This makes sense since the value of any terminal state should be 0.

 

Next, we update G. Notice how, on the first iteration of the loop, this includes the reward for the terminal state.

 

Once the loop is done, we reverse the list of states and returns, since we want it to be in the order that we visited the states.

 

\---

 

One final thing to note about Monte Carlo.

 

Recall that one of the disadvantages of Dynamic Programming is that we have to loop through the entire set of states on every iteration, and that this is bad for most practical scenarios in which there are a large number of states.

 

Notice how Monte Carlo only updates the value for states that we actually visit.

 

That means, even if the state space is large, if we only ever visit a small subset of states, then it doesn’t matter.

 

Also notice that with Monte Carlo, we don’t even need to know what the states are. We can simply discover them by playing the game.

 

So there are some advantages to Monte Carlo in situations where doing full, exact calculations is infeasible.

 

 

## MC in Code (V)

 

In this lecture, we are going to implement Monte Carlo for finding the state-value function in code.

 

If you don’t want to try to code this yourself, although I highly recommend you do, the relevant file for this lecture is monte\_carlo.py

 

At the top we have our usual imports. We’ve imported both standard\_grid and negative\_grid, I would encourage you to try both. We also make use of the print\_values and print\_policy functions we defined earlier.

 

We have our usual constants as well.

 

`import numpy as np`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

` `

`SMALL_ENOUGH = 10e-4`

`GAMMA = 0.9`

`ALL_POSSIBLE_ACTIONS = ('U', 'D', 'L', 'R')`

 

 

Next we define the play\_game function, which takes in a grid and a policy.

 

`def play_game(grid, policy):`

`# returns a list of states and corresponding returns`

` `

`# reset game to start at a random position`

`# we need to do this, because given our current deterministic policy`

`# we would never end up at certain states, but we still want to measure their value`

`start_states = grid.actions.keys()`

`start_idx = np.random.choice(len(start_states))`

`grid.set_state(start_states[start_idx])`

` `

`s = grid.current_state()`

`states_and_rewards = [(s, 0)] # list of tuples of (state, reward)`

`while not grid.game_over():`

`a = policy[s]`

`r = grid.move(a)`

`s = grid.current_state()`

`states_and_rewards.append((s, r))`

`# calculate the returns by working backwards from the terminal state`

`G = 0`

`states_and_returns = []`

`first = True`

`for s, r in reversed(states_and_rewards):`

`# the value of the terminal state is 0 by definition`

`# we should ignore the first state we encounter`

`# and ignore the last G, which is meaningless since it doesn't correspond to any move`

`if first:`

`first = False`

`else:`

`states_and_returns.append((s, G))`

`G = r + GAMMA*G`

`states_and_returns.reverse() # we want it to be in order of state visited`

`return states_and_returns`

 

Our policy is the same one we used earlier, which is to take the upper-left path all the way to the goal state. And for any state not in that path, to go to the losing state.

 

Since Monte Carlo only calculates values for states that are actually visited, and if we only start at the prescribed start state, there will be some states that we’ll never visit, we need this little hack at the beginning of play\_game which allows us to start the game at any state.

 

This is called the “exploring starts” method and we’ll discuss it more in-depth later on.

 

Next, we play the game. This is pretty much exactly the same as the pseudocode I showed you earlier. The goal here is to make a list of all the states we visited and the rewards we got.

 

Next, we calculate the returns for each state. This is again exactly like the pseudocode I showed you earlier. We visit each state in reverse, and recursively calculate the return.

 

At the end, we reverse the list of returns since we want it to be in chronological order given that we’re doing “first-visit” Monte Carlo.

 

\---

 

Next we enter the main section.

 

`if __name__ == '__main__':`

`# use the standard grid again (0 for every step) so that we can compare`

`# to iterative policy evaluation`

`grid = standard_grid()`

` `

`# print rewards`

`print "rewards:"`

`print_values(grid.rewards, grid)`

` `

`# state -> action`

`policy = {`

`(2, 0): 'U',`

`(1, 0): 'U',`

`(0, 0): 'R',`

`(0, 1): 'R',`

`(0, 2): 'R',`

`(1, 2): 'R',`

`(2, 1): 'R',`

`(2, 2): 'R',`

`(2, 3): 'U',`

`}`

` `

`# initialize V(s) and returns`

`V = {}`

`returns = {} # dictionary of state -> list of returns we've received`

`states = grid.all_states()`

`for s in states:`

`if s in grid.actions:`

`returns[s] = []`

`else:`

`# terminal state or state we can't otherwise get to`

`V[s] = 0`

 

The first thing we do is get the grid, print out the rewards, and create the policy.

 

Next we initialize the returns. Note that we don’t bother setting the values for terminal states because we already know they’re going to be 0.

 

We also don’t bother setting an initial value for any of the other states, because they would be immediately overwritten using the average returns.

 

\---

 

Next we have our Monte Carlo loop. This plays a game and gets the states and returns lists.

 

`# repeat`

`for t in xrange(100):`

` `

`# generate an episode using pi`

`states_and_returns = play_game(grid, policy)`

`seen_states = set()`

`for s, G in states_and_returns:`

`# check if we have already seen s`

`# called "first-visit" MC policy evaluation`

`if s not in seen_states:`

`returns[s].append(G)`

`V[s] = np.mean(returns[s])`

`seen_states.add(s)`

 

Next, we create a set to keep track of all the states we’ve seen, since we only want to add a return if it’s the first time we’ve seen the state in this episode.

 

Next, we loop through all the states and returns. If this is the first time we’ve seen the state, we add G to our returns list for the state.

 

We then recalculate V(s). Notice how we’re not doing anything special to calculate the mean here, just using the default definition.

 

And then we add “s” to the states we’ve seen.

 

At the end of the script, we print the values we calculated, and the policy we used.

 

`print "values:"`

`print_values(V, grid)`

`print "policy:"`

`print_policy(policy, grid)`

 

Result:

 

`rewards:`

`---------------------------`

`0.00| 0.00| 0.00| 1.00|`

`---------------------------`

`0.00| 0.00| 0.00| -1.00|`

`---------------------------`

`0.00| 0.00| 0.00| 0.00|`

`values:`

`---------------------------`

`0.81| 0.90| 1.00| 0.00|`

`---------------------------`

`0.73| 0.00| -1.00| 0.00|`

`---------------------------`

`0.66| -0.81| -0.90| -1.00|`

`policy:`

`---------------------------`

`R | R | R | |`

`---------------------------`

`U | | R | |`

`---------------------------`

`U | R | R | U |`

 

So it looks like we get the exact same answer as iterative policy evaluation.

 

 

## MC to find V in Windy Gridworld

 

In this lecture, we are going to use the same Monte Carlo prediction algorithm to find V, but this time we’ll be in windy Gridworld and we’ll be using a slightly different policy.

 

One thing you might have noticed with the last script, is that Monte Carlo wasn’t really needed, since the returns were deterministic. This was because the 2 probability distributions we’re interested in, pi(a | s), and p(s’,r | s,a), were both deterministic.

 

In Windy Gridworld, the state transitions are not deterministic, so we’ll have a source of randomness, and hence a need for Monte Carlo.

 

Also, the policy will be different.

 

In particular, this policy is always going to try to win, or in other words, travel to the goal state.

 

We’ll see that even though the policy is to go to the goal state, not all values will end up positive, since in windy gridworld, the wind can still end up pushing you into the losing state.

 

So on average, the return for that state is negative.

 

If you don’t want to try to code this yourself, although I highly recommend you do, the relevant file in the course repo is monte\_carlo\_random.py

 

\---

 

`import numpy as np`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

` `

`SMALL_ENOUGH = 10e-4`

`GAMMA = 0.9`

`ALL_POSSIBLE_ACTIONS = ('U', 'D', 'L', 'R')`

 

At the top we have the same imports and constants as the regular Monte Carlo script.

 

Underneath that we have the random\_action function.

 

`def random_action(a):`

`# choose given a with probability 0.5`

`# choose some other a' != a with probability 0.5/3`

`p = np.random.random()`

`if p < 0.5:`

`return a`

`else:`

`tmp = list(ALL_POSSIBLE_ACTIONS)`

`tmp.remove(a)`

`return np.random.choice(tmp)`

 

This works the same way as the previous Gridworld. We have a 0.5 probability of doing the intended action, and a 0.5/3 probability of doing some other action.

 

\---

 

Next we have the play\_game function. Notice that this is exactly the same as before, except instead of using the action a chosen by the policy, we let the “wind” possibly choose another action.

 

`def play_game(grid, policy):`

`# returns a list of states and corresponding returns`

` `

`# reset game to start at a random position`

`# we need to do this, because given our current deterministic policy`

`# we would never end up at certain states, but we still want to measure their value`

`start_states = grid.actions.keys()`

`start_idx = np.random.choice(len(start_states))`

`grid.set_state(start_states[start_idx])`

` `

`s = grid.current_state()`

`states_and_rewards = [(s, 0)] # list of tuples of (state, reward)`

`while not grid.game_over():`

`a = policy[s]`

`a = random_action(a)`

`r = grid.move(a)`

`s = grid.current_state()`

`states_and_rewards.append((s, r))`

`# calculate the returns by working backwards from the terminal state`

`G = 0`

`states_and_returns = []`

`first = True`

`for s, r in reversed(states_and_rewards):`

`# the value of the terminal state is 0 by definition`

`# we should ignore the first state we encounter`

`# and ignore the last G, which is meaningless since it doesn't correspond to any move`

`if first:`

`first = False`

`else:`

`states_and_returns.append((s, G))`

`G = r + GAMMA*G`

`states_and_returns.reverse() # we want it to be in order of state visited`

`return states_and_returns`

 

\---

 

Next we go down to the main section. We have the same grid and rewards as before.

 

What’s different about this is the policy. In particular, we are always trying to get to the goal, no matter what state we’re in. If we find ourselves under the wall, we choose to go left, so that we can take the upper-left route to the goal.

 

`if __name__ == '__main__':`

`# use the standard grid again (0 for every step) so that we can compare`

`# to iterative policy evaluation`

`grid = standard_grid()`

` `

`# print rewards`

`print "rewards:"`

`print_values(grid.rewards, grid)`

` `

`# state -> action`

`# found by policy_iteration_random on standard_grid`

`# MC method won't get exactly this, but should be close`

`# values:`

`# ---------------------------`

`# 0.43| 0.56| 0.72| 0.00|`

`# ---------------------------`

`# 0.33| 0.00| 0.21| 0.00|`

`# ---------------------------`

`# 0.25| 0.18| 0.11| -0.17|`

`# policy:`

`# ---------------------------`

`# R | R | R | |`

`# ---------------------------`

`# U | | U | |`

`# ---------------------------`

`# U | L | U | L |`

`policy = {`

`(2, 0): 'U',`

`(1, 0): 'U',`

`(0, 0): 'R',`

`(0, 1): 'R',`

`(0, 2): 'R',`

`(1, 2): 'U',`

`(2, 1): 'L',`

`(2, 2): 'U',`

`(2, 3): 'L',`

`}`

 

Notice that I’ve added the answer that we get from policy iteration in the comments. That’s the great thing about these algorithms - you can use them to sanity check each other.

 

We expect Monte Carlo to get close to, but not exactly this answer.

 

\---

 

Notice how everything after that is the same. The Monte Carlo algorithm doesn’t change, because the fact that we’re taking averages already takes into account any randomness both in the policy and in the state transitions.

 

Run it and see what you get:

 

`rewards:`

`---------------------------`

`0.00| 0.00| 0.00| 1.00|`

`---------------------------`

`0.00| 0.00| 0.00| -1.00|`

`---------------------------`

`0.00| 0.00| 0.00| 0.00|`

`values:`

`---------------------------`

`0.43| 0.55| 0.72| 0.00|`

`---------------------------`

`0.32| 0.00| 0.19| 0.00|`

`---------------------------`

`0.25| 0.17| 0.11| -0.17|`

`policy:`

`---------------------------`

`R | R | R | |`

`---------------------------`

`U | | U | |`

`---------------------------`

`U | L | U | L |`

 

You can double check these and verify that they are close to what we get with policy iteration.

 

 

## MC for Finding Q / Exploring-Starts Optimization

 

As you’ll recall, the pattern we want to follow us to first look at how to solve the prediction problem, which is finding a value function given a policy, and then to look at how to solve the control problem, which is how to find the optimal policy.

 

In this section, we are going to start thinking about how to find the optimal policy using Monte Carlo.

 

You should realize that when we try to do that, we come across a major problem.

 

The problem is, we only have V(s) for a given policy, but we don’t know what actions will lead to a better V(s), because we can’t do a look-ahead search.

 

With Monte Carlo, all we’re able to do is play an episode straight through and use the returns as samples.

 

The key to using Monte Carlo for the control problem then, is to find Q, since Q is indexed by both s and a, and we can choose the argmax over a to determine the best policy.

 

\---

 

So how do we use Monte Carlo to find Q?

 

The process is largely the same as for finding V, except that instead of just returning tuples of states and returns, we’ll return triples of states, actions, and returns.

 

\---

 

You can already see why this might be problematic.

 

Recall that the number of values we need to store grows quadratically with the state set size and the action set size.

 

That means, we have a lot more values to approximate, and that means we need to do many more steps of Monte Carlo in order to get a good answer.

 

\---

 

There is another problem with trying to estimate Q.

 

This goes back to our explore-exploit dilemma.

 

If we have a fixed policy, then every Q(s,a) will only have samples for one action.

 

This means that out of |S|x|A| values we need to fill in, we’ll only be able to fill in 1/|A| of the values.

 

\---

 

The way we can fix this is, as we discussed earlier, using the “exploring starts” method.

 

With exploring starts for Q, we now randomly choose an initial state and an initial action.

 

Thereafter we follow the policy, and so the answer we get is Q\_pi(s, a).

 

This is consistent with our definition of Q, which is the expected value of the return, given that we’re in state s and doing action a.

 

Q(s,a) = E\[G(t) | S(t)=s,A(t)=a\]

 

\---

 

We can now return to the control problem.

 

If you think carefully, you’ll realize we already know the answer to this problem.

 

We discussed earlier how the method we can always use to find an optimal policy is generalized policy iteration, where we alternate between the policy evaluation and policy improvement steps.

 

For policy evaluation, we just discussed that. We just use Monte Carlo to get an estimate for Q.

 

The policy improvement step is the same as always, we just take the argmax over the actions from Q.

 

pi(s) = argmax\[a\]{ Q(s,a) }

 

\---

 

One issue with this, as we already discussed, is that because we need to find Q over all states across all actions, this can take a very long time using sampling.

 

And so we again have this problem where there’s an iterative algorithm inside another iterative algorithm.

 

\---

 

The solution to this is to take the same approach as we do with value iteration.

 

Instead of doing a fresh Monte Carlo policy evaluation on each round, where it would take a long time to collect samples, all we do is keep updating the same Q, and do policy improvement after every single episode.

 

This means that, on every iteration of the outer loop, we generate only one episode, use that episode to improve our estimate of Q, and then immediately do the policy improvement step.

 

\---

 

Let’s look at this in pseudocode to solidify this idea.

 

The first step is to initialize Q and pi randomly.

 

`Q = random, pi = random`

`while True:`

`choose random start state s`

`states, actions, returns = generate an episode starting from s`

`# evaluation step`

`for s, a, G in zip(states, actions, returns):`

`all_returns(s, a).append(G)`

`Q(s,a) = mean(all_returns(s,a))`

` `

`# improvement step`

`pi(s) = argmax[a]{ Q(s,a) }`

 

And then, in an infinite loop, we first choose a random state and a random action to start from.

 

Remember this is called the exploring-starts method.

 

Next, we generate an episode from this starting position, following the current policy.

 

From this, we receive a list of triples containing states, actions, and returns.

 

We append these to a dictionary of returns keyed on state-action pairs.

 

Next, we recalculate Q(s,a) as the average of all the returns for this state-action pair.

 

Next, we do the policy improvement step, which is to assign the action that’s the argmax of Q.

 

\---

 

There is one subtle problem with this algorithm.

 

Recall that if we do an action that results in us bumping into a wall, we end up in the same state as before.

 

So if we follow this policy, we’ll never end up in a terminal state and therefore never finish the episode.

 

To avoid this problem, we’ll introduce a hack, where if we end up in the same state after doing an action, we’ll give this a reward of -100, which is lower than any other reward from the environment, and end the episode.

 

\---

 

It’s interesting that this method converges, even though the returns that we average for Q are for different policies.

 

Intuitively, Q has to converge, since if Q is suboptimal, then the policy will change, and that will in turn cause Q to change.

 

We can only achieve stability when both the value and the policy converge to the optimal value and the optimal policy.

 

An interesting fact is that this has never been formally proven.

 

 

## MC-ES in Code

 

In this lecture we are going to use Monte-Carlo Exploring-Starts to solve the control problem, or in other words, find the optimal policy and the optimal value function.

 

If you don’t want to code this yourself, although I highly recommend you do, the relevant file is monte\_carlo\_es.py

 

We start out with our standard imports and constants.

 

`import numpy as np`

`import matplotlib.pyplot as plt`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

` `

`GAMMA = 0.9`

`ALL_POSSIBLE_ACTIONS = ('U', 'D', 'L', 'R')`

 

Next we have the play\_game function.

 

`def play_game(grid, policy):`

`# returns a list of states and corresponding returns`

` `

`# reset game to start at a random position`

`# we need to do this if we have a deterministic policy`

`# we would never end up at certain states, but we still want to measure their value`

`# this is called the "exploring starts" method`

`start_states = grid.actions.keys()`

`start_idx = np.random.choice(len(start_states))`

`grid.set_state(start_states[start_idx])`

` `

`s = grid.current_state()`

`a = np.random.choice(ALL_POSSIBLE_ACTIONS) # first action is uniformly random`

` `

`# be aware of the timing`

`# each triple is s(t), a(t), r(t)`

`# but r(t) results from taking action a(t-1) from s(t-1) and landing in s(t)`

`states_actions_rewards = [(s, a, 0)]`

`while True:`

`old_s = grid.current_state()`

`r = grid.move(a)`

`s = grid.current_state()`

`if old_s == s:`

`# hack so that we don't end up in an infinitely long episode`

`# bumping into the wall repeatedly`

`states_actions_rewards.append((s, None, -100))`

`break`

`elif grid.game_over():`

`states_actions_rewards.append((s, None, r))`

`break`

`else:`

`a = policy[s]`

`states_actions_rewards.append((s, a, r))`

` `

`# calculate the returns by working backwards from the terminal state`

`G = 0`

`states_actions_returns = []`

`first = True`

`for s, a, r in reversed(states_actions_rewards):`

`# the value of the terminal state is 0 by definition`

`# we should ignore the first state we encounter`

`# and ignore the last G, which is meaningless since it doesn't correspond to any move`

`if first:`

`first = False`

`else:`

`states_actions_returns.append((s, a, G))`

`G = r + GAMMA*G`

`states_actions_returns.reverse() # we want it to be in order of state visited`

`return states_actions_returns`

 

The first few lines are choosing the first state and the first action randomly, which is required when we’re doing exploring starts.

 

Next, we play the game. Notice how we are now storing triples of states, actions, and rewards.

 

We have an extra if-statement here, so that if our policy is to bump into a wall, we’ll break out of the loop with a very negative reward, so that the agent never chooses this action again.

 

Next, we calculate the returns. This is largely the same as before except now we’re adding in the actions.

 

\---

 

Next, we have a special function that simultaneously does the argmax and the max over a dictionary, which is what we’ll be using to store Q.

 

`def max_dict(d):`

`# returns the argmax (key) and max (value) from a dictionary`

`# put this into a function since we are using it so often`

`max_key = None`

`max_val = float('-inf')`

`for k, v in d.iteritems():`

`if v > max_val:`

`max_val = v`

`max_key = k`

`return max_key, max_val`

 

All it does is returns the key for the maximum value, and the maximum value itself.

 

\---

 

Next we have the main section. I’m using the negative grid here but you can try the standard grid as well.

 

`if __name__ == '__main__':`

`# use the standard grid again (0 for every step) so that we can compare`

`# to iterative policy evaluation`

`# grid = standard_grid()`

`# try the negative grid too, to see if agent will learn to go past the "bad spot"`

`# in order to minimize number of steps`

`grid = negative_grid(step_cost=-0.1)`

` `

`# print rewards`

`print "rewards:"`

`print_values(grid.rewards, grid)`

` `

`# state -> action`

`# initialize a random policy`

`policy = {}`

`for s in grid.actions.keys():`

`policy[s] = np.random.choice(ALL_POSSIBLE_ACTIONS)`

` `

`# initialize Q(s,a) and returns`

`Q = {}`

`returns = {} # dictionary of state -> list of returns we've received`

`states = grid.all_states()`

`for s in states:`

`if s in grid.actions: # not a terminal state`

`Q[s] = {}`

`for a in ALL_POSSIBLE_ACTIONS:`

`Q[s][a] = 0 # needs to be initialized to something so we can argmax it`

`returns[(s,a)] = []`

`else:`

`# terminal state or state we can't otherwise get to`

`pass`

 

We print the rewards as usual, and set the initial policy to random actions.

 

Next we initialize Q and our returns dictionary.

 

Notice how, even though Q doesn’t strictly need to be initialized in order to do policy evaluation, it does need to be initialized just in case we do the argmax and the values haven’t been set yet.

 

\---

 

Next, we have our main loop.

 

`# repeat until convergence`

`deltas = []`

`for t in xrange(2000):`

`if t % 1000 == 0:`

`print t`

` `

`# generate an episode using pi`

`biggest_change = 0`

`states_actions_returns = play_game(grid, policy)`

`seen_state_action_pairs = set()`

`for s, a, G in states_actions_returns:`

`# check if we have already seen s`

`# called "first-visit" MC policy evaluation`

`sa = (s, a)`

`if sa not in seen_state_action_pairs:`

`old_q = Q[s][a]`

`returns[sa].append(G)`

`Q[s][a] = np.mean(returns[sa])`

`biggest_change = max(biggest_change, np.abs(old_q - Q[s][a]))`

`seen_state_action_pairs.add(sa)`

`deltas.append(biggest_change)`

` `

`# update policy`

`for s in policy.keys():`

`policy[s] = max_dict(Q[s])[0]`

 

Notice how we’re keeping track of the biggest changes per iteration. This is for debugging purposes only and is not required, unless you want to use the delta to test for convergence.

 

The first thing we do in the loop is play a game and get the states\_actions\_returns triples.

 

Next, we create a set to store the state-action pairs we’ve seen. Remember that we are still using the “first-visit” method, so we only want to update one instance of every state-action pair per episode.

 

Next, we loop through all the state-action pairs in the episode, update their returns list, and update Q.

 

When that’s done, we go to the policy improvement step. Recall that this is just the argmax over Q. We choose the 0th element since it returns a key-value tuple.

 

\---

 

Next, we plot the deltas, and print the optimal policy.

 

Note that we can also find the optimal state-value function using Q, so we do that too, and print it out.

 

`plt.plot(deltas)`

`plt.show()`

` `

`print "final policy:"`

`print_policy(policy, grid)`

` `

`# find V`

`V = {}`

`for s, Qs in Q.iteritems():`

`V[s] = max_dict(Q[s])[1]`

` `

`print "final values:"`

`print_values(V, grid)`

 

\---

 

Result:

 

`final policy:`

`---------------------------`

`R | R | R | |`

`---------------------------`

`U | | U | |`

`---------------------------`

`R | R | U | L |`

`final values:`

`---------------------------`

`0.62| 0.80| 1.00| 0.00|`

`---------------------------`

`0.46| 0.00| 0.80| 0.00|`

`---------------------------`

`-0.66| 0.15| 0.62| 0.46|`

 

Notice how we have a few 100s in the deltas. This is because our initial policy contained actions that led to bumping into a wall.

 

The final policy makes sense, as do the values.

 

 

## MC Control without ES

 

In this section, we are going to continue our discussion of Monte Carlo for the control problem.

 

Recall that one of the disadvantages of the method we just looked at, is that we need to use “exploring starts”.

 

We talked about how that might be infeasible for any game we’re not playing in “God-mode”.

 

For example, think of a self-driving car. It wouldn’t be possible to enumerate all the edge cases that the car might find itself in, and even if you could it would take a lot of work to put the car in those exact states.

 

So in this lecture, we’re going to look at how we might use Monte Carlo for control, without using “exploring starts”.

 

\---

 

Recall what we talked about earlier in this section, that all of the techniques we learned about with the multi-armed bandit problem are applicable here.

 

In particular, what we want to do is not follow the greedy policy, but the epsilon-greedy policy, or any other method that allows for more exploration.

 

The modifications to the code should be fairly simple. All we need to do is remove the part where we do the exploring starts, and instead only start in the official start position.

 

Then, in the portion of the code where we play the game, instead of just following the greedy policy, we’ll have a small probability epsilon, of doing a random action.

 

\---

 

It’s interesting to consider what the probability of reaching a state that is not part of the policy’s trajectory is.

 

For a state that’s K steps away from the start state, we would need to be in exploration mode on each step and choose the necessary states to get to the target state.

 

So in total that’s:

 

p = \[ epsilon/|A(s)| \] ^ K

 

You can imagine that this is a very small number, so for states that are very far off from the policy’s trajectory, you’ll need to do many iterations of Monte Carlo for the value to be accurate for those states.

 

 

## MC Control without ES Code

 

In this section we are going to implement Monte Carlo control using epsilon-greedy, so that we don’t need to use exploring starts.

 

If you don’t want to try to code this yourself, although I highly recommend you do, the relevant file in the course repo is monte\_carlo\_no\_es.py

 

We start out with all the same imports as before, all the same constants as before.

 

`import numpy as np`

`import matplotlib.pyplot as plt`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

`from monte_carlo_es import max_dict`

` `

`GAMMA = 0.9`

`ALL_POSSIBLE_ACTIONS = ('U', 'D', 'L', 'R')`

 

We have a function that chooses random actions.

 

Notice how, if we’re doing epsilon-soft by definition, this function actually becomes much simpler to write.

 

`def random_action(a, eps=0.1):`

`# choose given a with probability 1 - eps + eps/4`

`# choose some other a' != a with probability eps/4`

`p = np.random.random()`

`# if p < (1 - eps + eps/len(ALL_POSSIBLE_ACTIONS)):`

`# return a`

`# else:`

`# tmp = list(ALL_POSSIBLE_ACTIONS)`

`# tmp.remove(a)`

`# return np.random.choice(tmp)`

`#`

`# this is equivalent to the above`

`if p < (1 - eps):`

`return a`

`else:`

`return np.random.choice(ALL_POSSIBLE_ACTIONS)`

 

I’ve left some comments in there if you want to look at the naive way of implementing it.

 

\---

 

Next, we have the play\_game function.

 

`def play_game(grid, policy):`

`# returns a list of states and corresponding returns`

`# in this version we will NOT use "exploring starts" method`

`# instead we will explore using an epsilon-soft policy`

`s = (2, 0)`

`grid.set_state(s)`

`a = random_action(policy[s])`

` `

`# be aware of the timing`

`# each triple is s(t), a(t), r(t)`

`# but r(t) results from taking action a(t-1) from s(t-1) and landing in s(t)`

`states_actions_rewards = [(s, a, 0)]`

`while True:`

`r = grid.move(a)`

`s = grid.current_state()`

`if grid.game_over():`

`states_actions_rewards.append((s, None, r))`

`break`

`else:`

`a = random_action(policy[s]) # the next state is stochastic`

`states_actions_rewards.append((s, a, r))`

` `

`# calculate the returns by working backwards from the terminal state`

`G = 0`

`states_actions_returns = []`

`first = True`

`for s, a, r in reversed(states_actions_rewards):`

`# the value of the terminal state is 0 by definition`

`# we should ignore the first state we encounter`

`# and ignore the last G, which is meaningless since it doesn't correspond to any move`

`if first:`

`first = False`

`else:`

`states_actions_returns.append((s, a, G))`

`G = r + GAMMA*G`

`states_actions_returns.reverse() # we want it to be in order of state visited`

`return states_actions_returns`

 

Notice how we’ve taken out the exploring-starts code, and we’re now always starting from position (2, 0).

 

Also notice the line where we add the epsilon-greedy policy, where we make use of the random\_action function above.

 

The returns calculation is exactly the same as you would expect.

 

\---

 

Next, we go down to the main section.

 

Notice how this is all exactly the same as before.

 

`if __name__ == '__main__':`

`# use the standard grid again (0 for every step) so that we can compare`

`# to iterative policy evaluation`

`# grid = standard_grid()`

`# try the negative grid too, to see if agent will learn to go past the "bad spot"`

`# in order to minimize number of steps`

`grid = negative_grid(step_cost=-0.1)`

` `

`# print rewards`

`print "rewards:"`

`print_values(grid.rewards, grid)`

` `

`# state -> action`

`# initialize a random policy`

`policy = {}`

`for s in grid.actions.keys():`

`policy[s] = np.random.choice(ALL_POSSIBLE_ACTIONS)`

` `

`# initialize Q(s,a) and returns`

`Q = {}`

`returns = {} # dictionary of state -> list of returns we've received`

`states = grid.all_states()`

`for s in states:`

`if s in grid.actions: # not a terminal state`

`Q[s] = {}`

`for a in ALL_POSSIBLE_ACTIONS:`

`Q[s][a] = 0`

`returns[(s,a)] = []`

`else:`

`# terminal state or state we can't otherwise get to`

`pass`

 

The only difference with this algorithm isn’t in how we do policy iteration, it’s in what policy we use to play the game.

 

So we have the negative grid, we print the rewards, we initialize a random policy, and we initialize a random Q.

 

Notice that we need to initialize Q to a value even though it’s not needed for the evaluation problem.

 

This is because when we do the argmax later, we need to have values to choose from.

 

\---

 

In the main loop, we are again keeping track of the max deltas, so we can plot the changes as we go.

 

`# repeat until convergence`

`deltas = []`

`for t in xrange(5000):`

`if t % 1000 == 0:`

`print t`

` `

`# generate an episode using pi`

`biggest_change = 0`

`states_actions_returns = play_game(grid, policy)`

` `

`# calculate Q(s,a)`

`seen_state_action_pairs = set()`

`for s, a, G in states_actions_returns:`

`# check if we have already seen s`

`# called "first-visit" MC policy evaluation`

`sa = (s, a)`

`if sa not in seen_state_action_pairs:`

`old_q = Q[s][a]`

`returns[sa].append(G)`

`Q[s][a] = np.mean(returns[sa])`

`biggest_change = max(biggest_change, np.abs(old_q - Q[s][a]))`

`seen_state_action_pairs.add(sa)`

`deltas.append(biggest_change)`

` `

`# calculate new policy pi(s) = argmax[a]{ Q(s,a) }`

`for s in policy.keys():`

`a, _ = max_dict(Q[s])`

`policy[s] = a`

 

\---

 

At the end, we again calculate V from Q, and print the optimal policy and optimal values.

 

`plt.plot(deltas)`

`plt.show()`

` `

`# find the optimal state-value function`

`# V(s) = max[a]{ Q(s,a) }`

`V = {}`

`for s in policy.keys():`

`V[s] = max_dict(Q[s])[1]`

` `

`print "final values:"`

`print_values(V, grid)`

`print "final policy:"`

`print_policy(policy, grid)`

` `

`Let’s run this and see what we get.`

 

 

## MC Summary

 

In this lecture, we are going to summarize everything we looked at in this chapter.

 

This section was all about Monte Carlo methods.

 

In the last section on Dynamic Programming, we made the weird assumption that we knew all the state transition probabilities and never actually played the game.

 

So we were never able to learn from experience, as you would expect a reinforcement learning agent to do.

 

We followed our usual pattern of first looking at the prediction problem and then looking at the control problem.

 

The main technique we use with Monte Carlo is that the value function is the expected return given a state.

 

We know from probability that the expected value of something can be approximated by its sample mean.

 

In order to use Monte Carlo, we needed to generate episodes and calculate the returns for each episode.

 

This gave us a list of pairs of states and returns.

 

We then averaged these returns to find the value for each state.

 

Recall that there are 2 methods for averaging the returns, “first-visit” and “every-visit”.

 

While these have both been proven to converge to the same result, we used first-visit because it’s simpler.

 

\---

 

We saw that Monte Carlo methods can be more efficient than Dynamic Programming because it doesn’t require us to loop through the entire state space.

 

Because of this, we might never get the “full” value function, but it might not matter if many of those states would never be reached, or reached very rarely.

 

In other words, the more we visit a state, the more accurate the value will be, for that state.

 

Since the Monte Carlo method results in each state being visited a different number of times, depending on the policy, we used the exploring starts technique in order to make sure we had adequate data for each state.

 

\---

 

We then looked at the control problem.

 

The difference with Monte Carlo is that we now need to use Q instead of V, so that we can take the argmax of Q over all the actions.

 

This is required since we can’t do the kind of look-ahead search with Monte Carlo that we did with Dynamic Programming.

 

We saw that we could continue to use the idea of policy iteration from the dynamic programming section.

 

Recall that this is where we alternate between policy evaluation and policy improvement.

 

We talked about the fact that Monte Carlo has one major disadvantage here.

 

Monte Carlo needs many samples in order to be accurate, and it has to happen inside a loop, which makes it very inefficient.

 

We took the same approach here as we did with value iteration, which was to do only one update for evaluation per iteration.

 

What’s surprising about this is that the sample returns are for different policies, since the policy evolves as we do the iterations.

 

What’s also surprising is that this has never been formally proven to converge.

 

\---

 

One of the major disadvantages of the first control solution we looked at, is that we needed to use exploring-starts in order to get a full measurement of Q.

 

We saw that it’s not necessary to use exploring starts if we use epsilon-greedy instead, since epsilon-greedy allows us to continually explore all the states in the state space.

 

We learned that ALL of the techniques we learned about, when we studied the multi-armed bandit, apply here.

 

In fact, MDPs are like having a different multi-armed bandit problem at each state.

 

# Temporal Difference Learning

 

## Intro to TD

 

In this section of the course, we are going to look at a third technique for reinforcement learning, called temporal difference learning, or just “TD” for short.

 

TD learning is one of the most important techniques in reinforcement learning, and you’ll see how it combines ideas from the first 2 techniques, Dynamic Programming and Monte Carlo.

 

You’ll recall that one of the disadvantages of Dynamic Programming was that it required a full model of the environment, and never learned from experience.

 

We saw that Monte Carlo on the other hand, does learn from experience, and you’ll see in this section that TD learning also learns from experience.

 

With the Monte Carlo method, we saw that we could only update the value function after completing an episode.

 

On the other hand, Dynamic Programming used bootstrapping, or in other words, it was able to improve its estimates based on existing estimates.

 

We’ll see that TD learning also uses bootstrapping, and furthermore, it’s fully online. So we don’t need to wait for an episode to finish before we update our value estimates.

 

\---

 

In this chapter, we are going to take the same approach as we did in the previous 2 sections.

 

We are first going to look at the prediction problem, or in other words, finding the value function given a policy.

 

Next, we are going to look at the control problem.

 

Similar to the previous 2 sections, we are going to explore two different ways of approaching the control problem, SARSA, and Q-Learning, which has become popular as of late.

 

 

## TD(0) Theory

 

In this section we are going to look at how to apply temporal difference learning to the prediction problem, or in other words, finding the value function.

 

You might think this is a strange name at first. Why is there a 0 in the name and not some other number?

 

The reason is that there are other TD learning methods, such as TD(1), and more generally, TD(lambda), but these are outside the scope of this book.

 

They are similar but not necessary to understand Q-Learning and approximation methods, which is what we eventually want to get to.

 

\---

 

So how does TD(0) work?

 

First, let’s think back to Monte Carlo.

 

Recall that one disadvantage of Monte Carlo is that we need to wait for the episode to finish before calculating the returns, since the return depends on all future rewards.

 

Also recall, that the Monte Carlo method is to average the returns, and that earlier in the course we looked at different ways of calculating averages.

 

\---

 

In particular, let’s look at the method that does not require us to actually store all the returns.

 

V(S(t)) = V(S(t)) + alpha\*\[G(t)-V(S(t))\]

 

Recall that alpha can be constant or it can decay with time.

 

So if we used this formula, it would be an alternative way of calculating the average return for a state.

 

\---

 

Now recall the definition of V. Recall that it’s the expected value of the return given a state.

 

But also recall that we can define it recursively.

 

V(s) = E\[G(t) | S(t)=s\] = E\[R(t+1)+gamma\*V(S(t+1)) | S(t)=s\]

 

\---

 

So, it’s reasonable to ask, if we can just replace the return in the update equation, with this recursive definition of V.

 

V(S(t)) = V(S(t)) + alpha\*\[R(t+1) + gamma\*V(S(t+1)) - V(S(t))\]

V(s) = V(s) + alpha\*\[r+V(s’)-V(s)\]

 

What we get from this is the TD(0) method.

 

If you look at this carefully, you’ll realize why this is a fully online bootstrapping method.

 

We’re now not calculating G, the full return.

 

Instead, we’re just using another V estimate, in particular, the V for the next state.

 

What this also tells us is that we can’t update V(s), until we know s’.

 

So rather than waiting for the entire episode to finish, we just need to wait until we reach the next state, to update the value for the current state.

 

\---

 

It’s helpful to examine how these estimates work and what the sources of randomness are.

 

With Monte Carlo, the randomness came from the fact that each episode could play out in a different way.

 

So the return for a state would be different if all the later state transitions had some randomness.

 

With TD(0), we have yet another source of randomness.

 

In particular, we don’t even know the return, so instead we use r + gamma\*V(s’) to estimate the return G.

 

\---

 

In this section, we learned why temporal difference learning is advantageous in comparison to both dynamic programming and Monte Carlo.

 

Unlike dynamic programming, we do not require a model of the environment. We learn from experience, and we update only the states that we actually visit.

 

Unlike Monte Carlo, we don’t need to wait for an episode to finish before we can start learning. This can be advantageous in situations where we have very long episodes. We can improve our performance during the episode itself, rather than having to wait until the next episode.

 

It can even be used for continuing tasks, in which there are no episodes at all.

 

 

## TD(0) in Code

 

In this section, we are going to implement TD(0) in code.

 

If you don’t want to try to code this yourself, although I highly recommend you do, the relevant file in the course repo is td0\_prediction.py

 

We start off with our standard imports.

 

`import numpy as np`

`import matplotlib.pyplot as plt`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

` `

`SMALL_ENOUGH = 10e-4`

`GAMMA = 0.9`

`ALPHA = 0.1`

`ALL_POSSIBLE_ACTIONS = ('U', 'D', 'L', 'R')`

 

We also have our usual constants, except now we also need a learning rate alpha.

 

Next, we have the random\_action function. I didn’t import it from the other file since I wanted to put this comment in here.

 

`def random_action(a, eps=0.1):`

`# we'll use epsilon-soft to ensure all states are visited`

`# what happens if you don't do this? i.e. eps=0`

`p = np.random.random()`

`if p < (1 - eps):`

`return a`

`else:`

`return np.random.choice(ALL_POSSIBLE_ACTIONS)`

 

We have the same issue with TD as we do with Monte Carlo. And that’s if we never visit a state, we’ll never update its value.

 

So if we have a deterministic policy without any exploration, some states won’t have values. Which is fine if you don’t care about those values, but we want to add some exploration here to make it more interesting.

 

\---

 

Next we have the play\_game function.

 

Notice how this is much simpler than the Monte Carlo version, since we don’t need to calculate any returns. All we need to do is return a list of states and rewards.

 

Technically, we should be doing the update while we play the game, which would be true online learning, but I want to compartmentalize the playing of the game and updating the agent for clarity.

 

`def play_game(grid, policy):`

`# returns a list of states and corresponding rewards (not returns as in MC)`

`# start at the designated start state`

`s = (2, 0)`

`grid.set_state(s)`

`states_and_rewards = [(s, 0)] # list of tuples of (state, reward)`

`while not grid.game_over():`

`a = policy[s]`

`a = random_action(a)`

`r = grid.move(a)`

`s = grid.current_state()`

`states_and_rewards.append((s, r))`

`return states_and_rewards`

 

\---

 

Next, we go to the main section.

 

`if __name__ == '__main__':`

`# use the standard grid again (0 for every step) so that we can compare`

`# to iterative policy evaluation`

`grid = standard_grid()`

` `

`# print rewards`

`print "rewards:"`

`print_values(grid.rewards, grid)`

` `

`# state -> action`

`policy = {`

`(2, 0): 'U',`

`(1, 0): 'U',`

`(0, 0): 'R',`

`(0, 1): 'R',`

`(0, 2): 'R',`

`(1, 2): 'R',`

`(2, 1): 'R',`

`(2, 2): 'R',`

`(2, 3): 'U',`

`}`

 

I’m using the standard grid here, so you can compare this to our earlier scripts. The policy is also the same as the first policy we used.

 

Note that you won’t get the same answer, since before we weren’t using epsilon-greedy.

 

\---

 

Next, we initialize all the values to 0.

 

`V = {}`

`states = grid.all_states()`

`for s in states:`

`V[s] = 0`

 

After that, we have our main loop.

 

`# repeat until convergence`

`for it in xrange(1000):`

` `

`# generate an episode using pi`

`states_and_rewards = play_game(grid, policy)`

`# the first (s, r) tuple is the state we start in and 0`

`# (since we don't get a reward) for simply starting the game`

`# the last (s, r) tuple is the terminal state and the final reward`

`# the value for the terminal state is by definition 0, so we don't`

`# care about updating it.`

`for t in xrange(len(states_and_rewards) - 1):`

`s, _ = states_and_rewards[t]`

`s2, r = states_and_rewards[t+1]`

`# we will update V(s) AS we experience the episode`

`V[s] = V[s] + ALPHA*(r + GAMMA*V[s2] - V[s])`

 

Note that even though we could do the update “inline” as we played the game, I decided not to do that since it would make the code messy, having to interleave the updates and the playing of the game.

 

And so once we have our list of states and rewards, we loop through them and do the TD(0) update, which is the same equation you saw in the theory lecture.

 

Finally, we print the values we found, and the policy.

 

`print "values:"`

`print_values(V, grid)`

`print "policy:"`

`print_policy(policy, grid)`

 

Run this yourself and see what you get.

 

 

## SARSA Theory

 

In this lecture we are going to look at how to apply the TD(0) algorithm to the control problem.

 

By now you are probably noticing the pattern: what we’re going to do is apply TD(0) to policy iteration.

 

In particular, we’re going to use the value iteration version where we continually update Q based on itself, and we’re going to do it in place, and any actions we take are always greedy with respect to our current estimate of Q.

 

So in this section, we’re skipping the part where we do a full policy evaluation, and just immediately going to the more efficient form.

 

\---

 

Recall from the Monte Carlo section that the reason we want to use Q is because it allows us to choose an action based on the argmax of Q over a, whereas we can’t do that with V because it’s only indexed by the state.

 

Since Q has the same recursive form, we can apply the same update equation as before.

 

Q(S(t),A(t)) = Q(S(t),A(t)) + alpha\*\[R(t+1)+gama\*Q(S(t+1),A(t+1))-Q(S(t),A(t))\]

Q(s,a) = Q(s,a) + alpha\*\[r+gamma\*Q(s’,a’)-Q(s,a)\]

 

Notice that we have the same limitation as we did with Monte Carlo. Since Q is indexed by both state and action, we need more iterations to gather enough data for convergence.

 

Because the update depends on knowing the entire 5-tuple (s,a,r,s’,a’), this method is named SARSA.

 

\---

 

Since SARSA requires you to know Q(s,a) for all the possible actions a, in a state s, so that you can accurately choose the argmax, we have the same problem as we did with Monte Carlo.

 

Recall that the problem was, if you follow a deterministic policy, you’ll only ever do 1/|A| of the possible actions, which will leave most of Q undefined.

 

So in order to remedy that problem, we either had to use exploring starts, OR a policy that allows for exploration, like epsilon-greedy.

 

Since we already know exploring starts is not realistic, we are going to use epsilon-greedy.

 

\---

 

Let’s look at some pseudocode to solidify this idea.

 

`Q(s,a) = arbitrary, Q(terminal, a) = 0`

`for t=1..N`

`s = start_state, a = epsilon_greedy_from(Q(s))`

`while not game over:`

`s’, r = do_action(a)`

`a’ = epsilon_greedy_from(Q(s’))`

`Q(s,a) = Q(s,a) + alpha*[r + gamma*Q(s’,a’) - Q(s,a)]`

`s = s’, a = a’`

 

First, we initialize Q arbitrarily, and 0 for any terminal state.

 

Next we enter a loop.

 

Inside the loop, we start a game.

 

We get the first state and select the first action based on epsilon-greedy and the current Q. We’ll call this (s, a)

 

Inside this loop, we start another loop, that ends when the episode is over.

 

We do the action a, to get the next state, s’, and the reward, r.

 

We then choose the next action based on epsilon-greedy and the current Q. We’ll call this a’.

 

Next, we do our update for Q(s,a), which depends on: Q(s,a), r, and Q(s’,a’).

 

Next, we update s to be s’, and we update a to be a’.

 

\---

 

One interesting fact about SARSA is that a convergence proof has never been published.

 

However, it has been stated informally that SARSA will converge if the policy converges to a greedy policy.

 

One way to achieve this is to let epsilon = 1/t, where t represents time.

 

This is the form we’ll be using in the code.

 

Note that the numerator doesn’t have to be 1. You can have 0.5/t, or 0.8/t, anything you want.

 

Also, you don’t HAVE to have 1/t decay, you can have 1/t^2/3, or any other power you choose.

 

You should consider this a hyperparameter.

 

\---

 

Also recall that learning rates can also decay.

 

There is a problem with using a 1/t decay though.

 

Consider that, for each time, only one state-action pair will be updated in Q.

 

Therefore, the learning rate will decay for values of Q that have never been updated before!

 

You could try to remedy this, by only decaying the learning rate once per episode, but you still have the same problem.

 

Only a subset of the full set of states are going to be visited in an episode.

 

And only one of the possible actions per state are going to be taken.

 

So even if you only decay the learning rate once per episode, you’re still decaying the learning rate for parts of Q that have never been updated before.

 

\---

 

To solve this, we take inspiration from deep learning - in particular, the AdaGrad and RMSprop algorithms.

 

Recall that what makes these unique, is the effective learning rates decrease more when past gradients have been large.

 

In other words, the more something has changed in the past, the more we’ll decrease the learning rate in the future.

 

Our version will be simpler than these techniques, but the idea is the same.

 

We’re going to keep a count of how many times we’ve seen a state-action pair.

 

We’ll set alpha to be the original alpha / the count.

 

alpha(s,a) = alpha0/count(s,a)

 

Or more generally:

 

alpha(s,a)=alpha0/(k+m\*count(s,a))

 

In this way, every state-action pair has its own alpha, and so each of them will have their own individually decaying learning rate.

 

 

## SARSA in Code

 

In this lecture, we are going to implement SARSA in code.

 

If you don’t want to try to code this yourself, although I highly recommend you do, the relevant file in the course repo is sarsa.py

 

At the top, we have our standard imports. Notice how we also need the max\_dict function from monte\_carlo\_es.

 

`import numpy as np`

`import matplotlib.pyplot as plt`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

`from monte_carlo_es import max_dict`

`from td0_prediction import random_action`

` `

`GAMMA = 0.9`

`ALPHA = 0.1`

`ALL_POSSIBLE_ACTIONS = ('U', 'D', 'L', 'R')`

 

We have the same constants as before. Note that alpha here, is not the effective alpha we’ll be using for Q, but the effective alpha will be derived from this initial alpha.

 

Notice how in this script, we don’t have a play\_game function, because with SARSA, playing the game and doing the updates can’t be separate.

 

We have to do the updates while we play the game. So as promised, TD methods are fully online.

 

\---

 

Now we enter the main section. Notice how we’re using the negative grid. You’re welcome to try the standard grid too to observe the effect.

 

`if __name__ == '__main__':`

`grid = negative_grid(step_cost=-0.1)`

` `

`print "rewards:"`

`print_values(grid.rewards, grid)`

 

Next, we print the rewards, and initialize Q.

 

`# initialize Q(s,a)`

`Q = {}`

`states = grid.all_states()`

`for s in states:`

`Q[s] = {}`

`for a in ALL_POSSIBLE_ACTIONS:`

`Q[s][a] = 0`

 

After that, we create two update\_counts dictionaries. The dictionary called just update\_counts is to see what proportion of time we spend in each state. The dictionary called update\_counts\_sa is for the adaptive learning rate.

 

`update_counts = {}`

`update_counts_sa = {}`

`for s in states:`

`update_counts_sa[s] = {}`

`for a in ALL_POSSIBLE_ACTIONS:`

`update_counts_sa[s][a] = 1.0`

 

Next, we enter the main loop. We’re using the “t” variable here for epsilon-greedy.

 

`# repeat until convergence`

`t = 1.0`

`deltas = []`

`for it in xrange(10000):`

`if it % 100 == 0:`

`t += 10e-3`

`if it % 2000 == 0:`

`print "it:", it`

 

Notice how it’s only going to increase every 100 steps, and by a very tiny amount.

 

This is also a hyperparameter, you would choose this based on your own experimentation.

 

Inside the loop, we play the game.

 

We set the start state and find the initial action based on Q.

 

`s = (2, 0) # start state`

`grid.set_state(s)`

` `

`a = max_dict(Q[s])[0]`

`a = random_action(a, eps=0.5/t)`

`biggest_change = 0`

`while not grid.game_over():`

`r = grid.move(a)`

`s2 = grid.current_state()`

` `

`# we need the next action as well since Q(s,a) depends on Q(s',a')`

`# if s2 not in policy then it's a terminal state, all Q are 0`

`a2 = max_dict(Q[s2])[0]`

`a2 = random_action(a2, eps=0.5/t) # epsilon-greedy`

` `

`# we will update Q(s,a) AS we experience the episode`

`alpha = ALPHA / update_counts_sa[s][a]`

`update_counts_sa[s][a] += 0.005`

`old_qsa = Q[s][a]`

`Q[s][a] = Q[s][a] + alpha*(r + GAMMA*Q[s2][a2] - Q[s][a])`

`biggest_change = max(biggest_change, np.abs(old_qsa - Q[s][a]))`

` `

`# we would like to know how often Q(s) has been updated too`

`update_counts[s] = update_counts.get(s,0) + 1`

` `

`# next state becomes current state`

`s = s2`

`a = a2`

 

Next, we enter the game loop.

 

We do the action to get the reward, and find the next state.

 

Next, we find the next action based on epsilon-greedy. Notice how epsilon here is not constant but decaying with time.

 

Next, we calculate alpha, which is the initial alpha / the count.

 

We also update the count, but only by a small amount.

 

Notice that we’re keeping track of the deltas here as well, since we would like to know how much Q is changing as we learn.

 

Next, we do our Q update, and we update the update counts dictionary, and then we set “s” and “a” to the new “s” and “a”.

 

Finally, we exit the loop.

 

`plt.plot(deltas)`

`plt.show()`

` `

`# determine the policy from Q*`

`# find V* from Q*`

`policy = {}`

`V = {}`

`for s in grid.actions.keys():`

`a, max_q = max_dict(Q[s])`

`policy[s] = a`

`V[s] = max_q`

` `

`# what's the proportion of time we spend updating each part of Q?`

`print "update counts:"`

`total = np.sum(update_counts.values())`

`for k, v in update_counts.iteritems():`

`update_counts[k] = float(v) / total`

`print_values(update_counts, grid)`

` `

`print "values:"`

`print_values(V, grid)`

`print "policy:"`

`print_policy(policy, grid)`

 

Since we want to print the policy, we need to find it by taking the argmax of Q.

 

We also use this opportunity to calculate the state-value function as well.

 

And also recall that we want to show what proportion of time we spend in each state, so we collect those values and use the print\_values function to show them.

 

At the end, we print the state-values and the final policy.

 

Run this and see what you get.

 

 

## Q-Learning

 

In this section we are going to discuss Q-Learning.

 

Q-Learning is very interesting because it deviates from the strategy we’ve been taking so far.

 

Recall that the main theme behind each of the control algorithms we studied is generalized policy iteration.

 

We always alternate between policy evaluation, and then policy improvement, which means choosing an action greedily based on the current value estimate.

 

What’s the same about all these control algorithms we’ve studied, is that they are called “on-policy” methods.

 

That means, we are always updating the value function based on the current policy.

 

What’s different about Q-Learning is that it’s an off-policy method.

 

This means, the actions you take can be completely random, and yet you still end up with the optimal value function, from which you can calculate the optimal policy.

 

\---

 

So how does Q-Learning work?

 

It actually looks a lot like SARSA.

 

It wouldn’t be surprising if you look at these 2, and they look exactly the same to you.

 

Q(S(t),A(t)) = Q(S(t),A(t))+alpha\*\[R(t+1) + max\[a’\]{ Q(S(t+1),a’) } - Q(St,At)\]

Q(s,a) = Q(s,a) + alpha\*\[r+max\[a’\]{ Q(s’,a’) } - Q(s,a)\]

 

So the idea is, instead of actually choosing a’ based on the argmax of Q, we instead update Q based on the max over all actions.

 

Now your first thought might be, “well isn’t that exactly the same?”

 

If we choose a’ as the argmax of Q, then the thing multiplied by gamma will be Q(s’, a’), which is maxed over a’.

 

\---

 

Here is the difference.

 

With Q-Learning, remember that it’s an off-policy method.

 

Q(s’,a’) might be the max over all a’, but this doesn’t necessarily mean a’ has to be our next action.

 

We update Q(s,a) using the max of Q(s’,a’) even if we don’t end up doing the action a’ in the next step.

 

What this suggests is that it doesn’t matter at all what policy we follow. We can choose actions randomly and still get the same answer. The code will demonstrate this.

 

In reality, if you do end up taking purely random actions, what will end up happening is that your agent will act sub-optimally very often, and that will make your episodes last longer.

 

And because of that the script will take longer to run for the same number of episodes.

 

\---

 

So the key difference with Q-Learning is that it doesn’t matter what policy we use.

 

It’s reasonable to ask then, under what circumstances is Q-Learning equivalent to SARSA?

 

If the policy you use during Q-Learning is a greedy policy, meaning you always choose the argmax over Q, then your Q(s’,a’) will correspond to the next action you take.

 

And so in that case, you’ll be doing SARSA, but you’ll also be doing Q-Learning.

 

 

## Q-Learning in Code

 

In this lecture we are going to implement Q-Learning in code.

 

If you don’t want to try to code this yourself, although I highly recommend you do, the relevant file in the course repo is q\_learning.py

 

Keep in mind that a lot of this is the same as the SARSA script.

 

Let’s just look at the main loop since that’s where all the relevant changes are.

 

`# repeat until convergence`

`t = 1.0`

`deltas = []`

`for it in xrange(10000):`

`if it % 100 == 0:`

`t += 10e-3`

`if it % 2000 == 0:`

`print "it:", it`

` `

`# instead of 'generating' an epsiode, we will PLAY`

`# an episode within this loop`

`s = (2, 0) # start state`

`grid.set_state(s)`

` `

`# the first (s, r) tuple is the state we start in and 0`

`# (since we don't get a reward) for simply starting the game`

`# the last (s, r) tuple is the terminal state and the final reward`

`# the value for the terminal state is by definition 0, so we don't`

`# care about updating it.`

`a, _ = max_dict(Q[s])`

`biggest_change = 0`

`while not grid.game_over():`

`a = random_action(a, eps=0.5/t) # epsilon-greedy`

`# random action also works, but slower since you can bump into walls`

`# a = np.random.choice(ALL_POSSIBLE_ACTIONS)`

`r = grid.move(a)`

`s2 = grid.current_state()`

` `

`# adaptive learning rate`

`alpha = ALPHA / update_counts_sa[s][a]`

`update_counts_sa[s][a] += 0.005`

` `

`# we will update Q(s,a) AS we experience the episode`

`old_qsa = Q[s][a]`

`# the difference between SARSA and Q-Learning is with Q-Learning`

`# we will use this max[a']{ Q(s',a')} in our update`

`# even if we do not end up taking this action in the next step`

`a2, max_q_s2a2 = max_dict(Q[s2])`

`Q[s][a] = Q[s][a] + alpha*(r + GAMMA*max_q_s2a2 - Q[s][a])`

`biggest_change = max(biggest_change, np.abs(old_qsa - Q[s][a]))`

` `

`# we would like to know how often Q(s) has been updated too`

`update_counts[s] = update_counts.get(s,0) + 1`

` `

`# next state becomes current state`

`s = s2`

`a = a2`

 

First thing you’ll notice is that the place where we choose the action we actually do is now in a different spot.

 

I’m doing epsilon-greedy in this script but I also leave you the option of choosing a uniform random action.

 

You’ll see that both work, but uniform random takes longer to complete the same number of episodes since it doesn’t try to go directly to the goal.

 

Notice how we are still using our adaptive learning rate and adaptive epsilon.

 

Next, notice the spot where we choose a2 and the next Q.

 

This part is the same as SARSA.

 

We also assign a to a2 at the end of the loop.

 

But once we wrap back around to the top, this a is going to possibly change. And so that’s what differentiates Q-Learning from SARSA.

 

Run this and confirm that we get the expected answer.

 

Note that your policy can be different due to randomness. But generally speaking any route you take will still lead you to the goal. There are just multiple ways of getting there.

 

 

## TD Summary

 

In this lecture we are going to summarize everything we did in this section.

 

This section was all about temporal difference learning, which combines aspects of both Monte Carlo and Dynamic Programming.

 

From Monte Carlo, we incorporate ideas like learning from experience, meaning we actually play the game.

 

We also learned how to generalize the idea of taking the sample mean of the returns, using what we learned in the multi-armed bandit section.

 

The problem with Monte Carlo is that it’s not fully online.

 

We also incorporated ideas from dynamic programming, such as bootstrapping, and using the recursive form of the value function to estimate the return.

 

When we put these 2 together, we get TD(0), where instead of taking the sample mean of the returns, we take the sample mean of the estimated return, which is based on the current reward and the next state value.

 

\---

 

For the control problem, we saw that we again have to use the action-value function instead of the state-value function, for the same reason as Monte Carlo estimation.

 

We derived the SARSA algorithm, which combines ideas from value iteration and TD(0).

 

We learned the difference between on-policy and off-policy algorithms, and we determined in hindsight that all the control solutions we’ve seen have been on-policy up until now.

 

We then learned about an off-policy algorithm called Q-Learning, which has gained traction recently in part due to Deep Q-Learning.

 

\---

 

One disadvantage of all these methods is that they require us to estimate Q.

 

As we learned early on, the state space can easily become infeasible to enumerate, and then on top of that, for every state you need to enumerate all the possible actions as well.

 

So in real-world problems, it’s very possible that Q does not even fit into memory.

 

The method of storing Q as a dictionary and indexing it by state and action is called the tabular method.

 

All the methods we’ve learned about so far have been tabular methods.

 

As you might imagine, tabular methods are only practical for small problems.

 

In the next section, we’ll learn a new technique that helps us get around this problem, using function approximation.

 

This essentially allows us to compress the amount of space we need to represent Q.

 

# Function Approximation

 

## Intro to Approximation

 

In this chapter, we are going to study approximation methods.

 

Recall that at the end of the last section, we discussed a major disadvantage of the methods we’ve been studying so far.

 

That is, they all require us to estimate the value function for each state, and in the case of the action-value function, each state and each action.

 

We learned early on in the course that the state space can grow infeasibly large very quickly, which makes all of the methods we studied impractical.

 

The answer to this problem is approximation.

 

\---

 

Recall in our earlier studies of deep learning, that neural networks are universal function approximators.

 

That means, given the right architecture, a neural network can approximate any function to an arbitrary degree of accuracy.

 

In practice, they don’t perform perfectly but they do perform very well.

 

Mathematically, what we are going to do, is first do a feature extraction.

 

So from the state s, we can extract a feature vector x.

 

Our goal is to find a function, that takes in a feature vector x, and a set of parameters theta, that faithfully approximates the value function, V(s).

 

x = get\_features(s) = phi(s)

f(x; phi) = theta.dot(x) = theta.dot(phi(s))

f(x; phi) ~= V(s) <-- our goal

 

\---

 

In this book, we are going to focus specifically on linear methods.

 

As you’ll see, function approximation methods require us to use models that are differentiable.

 

So you wouldn’t be able to use something like a decision tree or k-nearest neighbor.

 

In the sequel to this book, we’ll look at deep learning methods, which are also differentiable.

 

Unlike linear methods, we won’t need to do feature engineering beforehand, although we could. Deep learning models are much more expressive and do a lot of the work automatically.

 

Models like convolutional neural networks will allow us to use raw pixel data as the state, and the neural network will do its own automatic feature extraction and selection.

 

However, those are harder to implement, and take away from the main focus of this course, which is the fundamentals of reinforcement learning.

 

So you don’t need to know anything about deep learning to get through this course, but you do need to know about some basic machine learning techniques like linear regression and gradient descent.

 

\---

 

The outline of this chapter is as follows.

 

We are first going to apply approximation methods to Monte Carlo prediction.

 

That means we’ll be estimating the value function given a fixed policy, but instead of representing the value function as a dictionary indexed by state, we’ll use a linear function approximator.

 

Recall that Monte Carlo methods require us to play the entire episode and calculate the returns before doing any updates.

 

Next, we’ll apply approximation methods to TD(0) for prediction.

 

Remember that TD(0) takes aspects of both Monte Carlo sampling and the bootstrapping method of dynamic programming.

 

After doing the prediction problem, we’ll move on to the control problem, and we’ll use SARSA for this, but we’ll of course be replacing Q with a linear function approximator.

 

\---

 

One thing to keep in mind in this section, is that you can always sanity check your work, by comparing your results to the non-approximated versions of the code.

 

Since we’re doing approximation, we don’t expect our answers to be exactly equal to the non-approximated versions, but they should be close.

 

One obstacle you may encounter is that your algorithm might be implemented perfectly, but your model is bad.

 

Remember that linear models are not very expressive.

 

So if you extract a poor set of features, your model won’t be able to learn the value function well.

 

Or in other words, your model will have a large error.

 

To avoid this, you’ll have to proactively think about what features are good for mapping states to values. You’ll have to put in manual work on feature engineering in order to improve your results.

 

 

## Linear Models

 

In this lecture, we are going to discuss linear models in the context of reinforcement learning.

 

In particular, what we are doing here is applying supervised learning to reinforcement learning.

 

Recall that supervised learning basically amounts to function approximation.

 

We’re trying to find a parameterized function that closely approximate the true function.

 

In this case, that true function is the value function that we used to solve MDPs.

 

\---

 

Earlier in the course, we talked about the fact that rewards have to be real numbers.

 

Since returns are sums of rewards, they are also real numbers.

 

And since values are expected values of returns, they are also real numbers.

 

So if you think of the possible supervised learning methods we have: classification and regression, it should be clear that what we want to do here is regression.

 

\---

 

In particular, we want our estimate of V to be close to the true V.

 

As you know, for all supervised learning methods we need a cost function, and the appropriate cost function for regression is squared error.

 

We can thus represent the error as the squared difference between V and V\_hat.

 

Error = \[V(s) - V\_hat(s)\]^2

 

\---

 

Now that we have our basic error function, we can replace V with its definition, which is the expected value of the return.

 

Error = \[E\[G(t) | S(t)=s\] - V\_hat(s)\]^2

 

But since we don’t actually know this expected value, we need to replace it with something else.

 

\---

 

In particular, we can replace it with the sample mean of the actual returns.

 

Recall that this is the approach we took when we studied Monte Carlo methods.

 

Error = \[ (1/N) sum\[i=1..N\]{ G(i,s) - V\_hat(s) \]^2

 

\---

 

An alternative way of looking at this, is that we treat each state and return pair as a training sample.

 

In this way, what we’ll try to do is minimize the squared difference between all of the G and V\_hats simultaneously.

 

Error = sum\[i=1..N\]{ \[G(i,s) - V\_hat(s)\]^2 }

 

So this should look more like what we’re used to when we’re doing regression, which is the sum of the squared differences between all the y’s and y\_hats.

 

Error = sum\[i=1..N\]{ \[y(i) - y\_hat(i)\]^2 }

 

\---

 

The advantage of representing the error function in this way, is it allows us to do stochastic gradient descent.

 

If you recall, this is where do take a small step in the direction of the gradient with respect to the cost of only one sample at a time.

 

This is perfect for our needs, because at every iteration of the game, we’ll only have one state and return pair to look at.

 

\---

 

If you recall, V\_hat is parameterized by theta.

 

In other words, what we are trying to find is the theta that allows V\_hat to be the best approximation.

 

To achieve this, we want to do gradient descent with respect to theta, and minimize the error we derived earlier.

 

V\_hat(s) = theta.dot(phi(s)) = theta.dot(x)

 

theta = theta - alpha\*d(Error)/d(theta)

 

Alpha once again represents the learning rate.

 

\---

 

We can take this a step further and replace the error with the squared difference we saw earlier.

 

Remember this is stochastic gradient descent so we’re only looking at ONE sample of G at a time.

 

theta = theta + alpha\*\[G -V\_hat(s)\] d(V\_hat(s))/d(theta)

 

\---

 

Recall that we are looking only at linear models in this class, so V\_hat is the dot product of the feature vector x and theta.

 

In other words, the derivative of V with respect to theta, is x.

 

theta = theta + alpha\*\[G -V\_hat(s)\] x

 

\---

 

Something interesting happens when you think back to our Monte Carlo methods, or in other words, when we were not parameterizing V\_hat.

 

Instead, V\_hat(s) itself was the parameter we were trying to find, and we were trying to find it for all states s.

 

If V\_hat(s) is itself the parameter, then we get this update equation.

 

V(s) = V(s) + alpha\*(G - V(s))d\[V(s)\]/d\[V(s)\]

 

V(s) = V(s) + alpha\*(G - V(s))

 

But if you recall, this is the exact same equation we had before for updating the mean!

 

So you see what we were doing before to find V, was actually an instance of gradient descent.

 

 

## Features

 

In this lecture we are going to discuss feature engineering.

 

Recall that neural networks can in some sense, automatically find good nonlinear transformations, or in other words, features, of the data.

 

But in this book we are only going to study linear methods, which means we’ll have to come up with features on our own.

 

\---

 

One way you can think of states is that they are categorical variables.

 

So for example, with Gridworld, you can think of position (0,0) as category 1, position (0,1) as category 2, and so on.

 

And as you know, the way that we encode categories into feature vectors is one-hot-encoding.

 

\---

 

Let’s discuss what would happen if we were to one-hot encode each state.

 

We have |S| states, so the dimensionality of X, which we’ll call D, is the cardinality of |S|.

 

D=|S|

 

So we have a big long feature vector X, of size |S|.

 

And then for each of the states, we set one of the values in X to 1.

 

s = (0,0) → x = \[1, 0, 0, …\]

s = (0,1) → x = \[0, 1, 0, …\]

 

\---

 

The problem with this, is that it doesn’t allow us to compress the amount of space it takes to store the value function, which is the entire reason we want to do this in the first place.

 

Recall that if we store V as a dictionary, it’ll have |S| keys and |S| values.

 

So we haven’t made any improvement if we do one-hot encoding.

 

In fact, it is equivalent to what we were doing before, since each theta in this case would represent the value for the corresponding state.

 

V(s=0) = theta.dot(\[1,0,0,...\]) = theta\[0\] = 0th component of theta

 

\---

 

There is however, one positive aspect to using one-hot encoding for your feature transformation.

 

Let’s suppose your algorithm isn’t working, and V\_hat isn’t representing the true V very well.

 

One reason your V\_hat might not be good is because your features might be bad.

 

So your code might be perfectly fine and free of bugs, but still not yielding good results because the features are bad.

 

So in that case, you could change your feature transformer to use one-hot encoding, where you predict each V(s) individually.

 

If you do this, and your code works, that tells you that your features are bad.

 

\---

 

So if one-hot encoding is bad, then what’s good?

 

In the case of Gridworld, consider that each (i, j) position actually represents a position in 2-dimensional space.

 

Therefore, it’s more like a real number than a category.

 

So you can represent the X vector as simply (i, j) itself. You might want to scale it so its mean is 0 and its variance is 1.

 

(x1,x2) = (i,j)

 

We would consider this feature vector to simply be the raw data - without any feature engineering.

 

\---

 

What’s the problem with setting x to just be the location of the agent?

 

Remember that our model is linear.

 

Let’s say j is fixed.

 

That means, V can only change linearly with respect to i.

 

That means, V can only be a line with respect to this x-coordinate.

 

So it’s either always increasing or always decreasing.

 

This is not very expressive.

 

\---

 

Recall from my linear regression class, that one easy way to make new features is by creating polynomials.

 

You may have learned in your calculus studies, that an infinite Taylor expansion can approximate any function.

 

So if we start with x1 and x2, we can create the terms x1^2, x2^2, and x1\*x2.

 

You can also create higher order polynomials if you want, but you have to be careful of overfitting.

 

This is the method we’ll use in this course, but if you know of other ways to manually create features, you are welcome to use those as well.

 

 

## MC Prediction Theory

 

Now that we’ve set the groundwork for incorporating supervised linear models into our MDPs, we can start applying them to the prediction problem and the control problem.

 

We are of course going to start with the prediction problem.

 

In this lecture in particular, we are going to use Monte Carlo estimation, but replace the value function dictionary with our linear model of the value function.

 

\---

 

Recall that for Monte Carlo estimation, we have 2 main steps which we do repeatedly.

 

The first step is to play the game, and calculate a list of states and returns.

 

The second step is to update V(s) using the return as the target and V(s) as the prediction. Remember that this is gradient descent but it’s also equivalent to calculating the mean of all the returns for this state.

 

V(s) = V(s) + alpha\*(G - V(s))

 

\---

 

Since in this lecture we are approximating V(s) with the parameter theta, what we want to update instead is theta.

 

So now we do continue to do stochastic gradient descent, but with respect to theta instead of V.

 

theta = theta + alpha\*(G - V\_hat(s))x

 

\---

 

Remember that this is for a fixed policy, since we’re doing the prediction problem.

 

Let’s look at some pseudocode to solidify this idea.

 

We start by taking in an input policy pi, and randomly initializing the theta vector.

 

Next, we enter a loop for some number of iterations.

 

On each iteration, we play the game, which returns a sequence of states and returns.

 

We loop through these states and returns, and apply our update equation to theta, treating the return as the target.

 

`def mc_approx_prediction(𝜋):`

`𝜃 = random`

`for i=1..N`

`states_and_returns = play_game`

`for s, g in states_and_returns:`

`x = 𝜙(s)`

`𝜃 ← 𝜃 + 𝛼(g - 𝜃Tx)x`

 

 

## MC Prediction Code

 

In this lecture we are going to implement Monte Carlo prediction with a parameterized value function, in code.

 

If you don’t want to try to code this yourself, although I highly recommend you do, the relevant file in the course repo is approx\_mc\_prediction.py

 

At the top we have our usual imports.

 

`import numpy as np`

`import matplotlib.pyplot as plt`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

` `

`# NOTE: this is only policy evaluation, not optimization`

` `

`# we'll try to obtain the same result as our other MC script`

`from monte_carlo_random import random_action, play_game, SMALL_ENOUGH, GAMMA, ALL_POSSIBLE_ACTIONS`

` `

`LEARNING_RATE = 0.001`

 

We are also importing some things from our previous Monte Carlo script that are useful.

 

We are also defining a learning rate which we’ll be using for gradient descent.

 

Next we have the main section.

 

We’ll be using the standard\_grid for this demo.

 

`if __name__ == '__main__':`

`grid = standard_grid()`

` `

`print "rewards:"`

`print_values(grid.rewards, grid)`

` `

`# state -> action`

`# policy:`

`# ---------------------------`

`# R | R | R | |`

`# ---------------------------`

`# U | | U | |`

`# ---------------------------`

`# U | L | U | L |`

`policy = {`

`(2, 0): 'U',`

`(1, 0): 'U',`

`(0, 0): 'R',`

`(0, 1): 'R',`

`(0, 2): 'R',`

`(1, 2): 'U',`

`(2, 1): 'L',`

`(2, 2): 'U',`

`(2, 3): 'L',`

`}`

 

Next, we print the rewards and set the policy.

 

\---

 

Next, we randomly initialize the theta vector and define a function that turns the state into a feature vector x.

 

`# initialize theta`

`# our model is V_hat = theta.dot(x)`

`# where x = [row, col, row*col, 1] - 1 for bias term`

`theta = np.random.randn(4) / 2`

`def s2x(s):`

`return np.array([s[0] - 1, s[1] - 1.5, s[0]*s[1] - 3, 1])`

 

Notice that the only nonlinear feature here is the interaction effect between the i-coordinate and the j-coordinate.

 

We also have a 1 which represents the bias term.

 

\---

 

Next, we have our main loop.

 

`# repeat until convergence`

`deltas = []`

`t = 1.0`

`for it in xrange(20000):`

`if it % 100 == 0:`

`t += 0.01`

`alpha = LEARNING_RATE/t`

`# generate an episode using pi`

`biggest_change = 0`

`states_and_returns = play_game(grid, policy)`

`seen_states = set()`

`for s, G in states_and_returns:`

`# check if we have already seen s`

`# called "first-visit" MC policy evaluation`

`if s not in seen_states:`

`old_theta = theta.copy()`

`x = s2x(s)`

`V_hat = theta.dot(x)`

`# grad(V_hat) wrt theta = x`

`theta += alpha*(G - V_hat)*x`

`biggest_change = max(biggest_change, np.abs(old_theta - theta).sum())`

`seen_states.add(s)`

`deltas.append(biggest_change)`

` `

`plt.plot(deltas)`

`plt.show()`

 

Notice how we’re using a decaying learning rate, so alpha is the original learning rate / t.

 

The pattern here is the same as with regular Monte Carlo, we play the game and get a sequence of states and returns.

 

We then loop through the states and returns, but instead of updating V we now update the parameter theta, using the equation you saw earlier for stochastic gradient descent.

 

We are also keeping track of all the deltas, which are now measuring the absolute differences in theta.

 

\---

 

At the end, we create a values dictionary so that we can print it out using the print\_values function.

 

`# obtain predicted values`

`V = {}`

`states = grid.all_states()`

`for s in states:`

`if s in grid.actions:`

`V[s] = theta.dot(s2x(s))`

`else:`

`# terminal state or state we can't otherwise get to`

`V[s] = 0`

` `

`print "values:"`

`print_values(V, grid)`

`print "policy:"`

`print_policy(policy, grid)`

 

Run this and see what you get.

 

 

## TD(0) Semi-Gradient Prediction Theory

 

Since we were able to apply approximation methods to Monte Carlo, it is reasonable to ask if we can apply approximation methods to TD learning as well.

 

The answer is that we can, but there is one caveat.

 

\---

 

Let’s begin by looking at the algorithm.

 

Recall that the main difference between Monte Carlo and Temporal Difference Learning is that with Temporal Difference Learning we don’t use the actual return, we instead estimate the return based on the reward and the value function for the next state.

 

theta = theta + alpha\*\[r+gamma\*V\_hat(s’) - V\_hat(s)\] d(V\_hat(s))/d(theta)

theta = theta + alpha\*\[target - prediction\] d(prediction)/d(theta)

 

There is one small problem with this algorithm.

 

It’s that the target we’re using here is not a real target, because it depends on a prediction that the model makes, in particular, V\_hat(s’).

 

So in a sense we’re using the model output as a target to fix the model parameters, which seems strange.

 

At the same time, this works, so we do it anyway.

 

We call this a “semi-gradient” method, because since the target we’re using is not a true target, the gradient is not a true gradient.

 

\---

 

Let’s now go to the code.

 

If you don’t want to try to code this yourself, although I highly recommend you do, the relevant file is approx\_semigradient\_td0\_prediction.py

 

Remember that there are two main differences between this and Monte Carlo.

 

The first, as you’ve seen, is that we don’t use the returns in the update for theta.

 

Because of this, when we play the game, we also don’t need to bother calculating the returns, since we’ll be using the rewards directly.

 

\---

 

`import numpy as np`

`import matplotlib.pyplot as plt`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

`from td0_prediction import play_game, SMALL_ENOUGH, GAMMA, ALPHA, ALL_POSSIBLE_ACTIONS`

 

At the top, we have our usual imports. We also import some useful stuff from our previous td0 prediction script, like play\_game.

 

In this script, we’re going to define the model as a class, with an API like sci-kit learn’s.

 

`class Model:`

`def __init__(self):`

`self.theta = np.random.randn(4) / 2`

`def s2x(self, s):`

`return np.array([s[0] - 1, s[1] - 1.5, s[0]*s[1] - 3, 1])`

` `

`def predict(self, s):`

`x = self.s2x(s)`

`return self.theta.dot(x)`

` `

`def grad(self, s):`

`return self.s2x(s)`

 

So we have the init function, which we use to initialize theta.

 

We have the s2x function, which transforms the state into a feature vector. Notice that we’re using the same feature transformation as we did for Monte Carlo. Note that these may not be good features.

 

We have the predict function, which takes in a state s, transforms it into x, and returns the dot product between theta and x.

 

Finally we have the gradient function, which just returns x.

 

\---

 

Next, we have the main section.

 

`if __name__ == '__main__':`

`# use the standard grid again (0 for every step) so that we can compare`

`# to iterative policy evaluation`

`grid = standard_grid()`

` `

`# print rewards`

`print "rewards:"`

`print_values(grid.rewards, grid)`

` `

`# state -> action`

`policy = {`

`(2, 0): 'U',`

`(1, 0): 'U',`

`(0, 0): 'R',`

`(0, 1): 'R',`

`(0, 2): 'R',`

`(1, 2): 'R',`

`(2, 1): 'R',`

`(2, 2): 'R',`

`(2, 3): 'U',`

`}`

 

We’re using the standard grid, and the same policy we were using earlier, where we take a direct path to the goal, but if we’re not on that path, then we go directly to the losing state.

 

Next, we create a model and enter the main loop.

 

`model = Model()`

`deltas = []`

` `

`# repeat until convergence`

`k = 1.0`

`for it in xrange(20000):`

`if it % 10 == 0:`

`k += 0.01`

`alpha = ALPHA/k`

`biggest_change = 0`

` `

`# generate an episode using pi`

`states_and_rewards = play_game(grid, policy)`

` `

`for t in xrange(len(states_and_rewards) - 1):`

`s, _ = states_and_rewards[t]`

`s2, r = states_and_rewards[t+1]`

`# we will update V(s) AS we experience the episode`

`old_theta = model.theta.copy()`

`if grid.is_terminal(s2):`

`target = r`

`else:`

`target = r + GAMMA*model.predict(s2)`

`model.theta += alpha*(target - model.predict(s))*model.grad(s)`

`biggest_change = max(biggest_change, np.abs(old_theta - model.theta).sum())`

`deltas.append(biggest_change)`

` `

`plt.plot(deltas)`

`plt.show()`

 

We have some code to calculate the decaying learning rate.

 

We play the game to get a sequence of states and rewards.

 

Next, we loop through the states and rewards.

 

Since we know the value at the terminal state is 0, we don’t bother to make a prediction for the target if s2 is terminal.

 

Next, we implement our update equation for theta.

 

\---

 

When the loop is done, we create a dictionary of values from the model, so that we can print them out with the print\_values function.

 

`# obtain predicted values`

`V = {}`

`states = grid.all_states()`

`for s in states:`

`if s in grid.actions:`

`V[s] = model.predict(s)`

`else:`

`# terminal state or state we can't otherwise get to`

`V[s] = 0`

` `

`print "values:"`

`print_values(V, grid)`

`print "policy:"`

`print_policy(policy, grid)`

 

Lastly, we print the policy.

 

Run this and see what you get.

 

 

## Semi-Gradient SARSA

 

In this section, we are going to move on the control problem.

 

In particular, we’re going to implement SARSA, but instead of using Q, we are going to create a parameterized model to approximate Q.

 

Note that this is going to be more difficult than approximating V, since instead of approximating |S| values, we have to approximate |S|x|A| values.

 

\---

 

At the same time, the basic idea is the same.

 

Recall that our target is r + gamma\*Q(s’,a’), and our prediction is Q(s,a).

 

Since Q is an approximation, and it appears in both the target and prediction, this is also not a true gradient, so this is also a semi-gradient method.

 

theta = theta + alpha\*\[r+Q(s’,a’)-Q(s,a)\]d\[Q(s,a)\]/d\[theta\]

 

\---

 

Since Q is indexed by both s and a, we need a way to combine them both into a feature vector.

 

Once simple method would be to take what we had before for V\_hat, and just one-hot encode the actions.

 

So in effect, we’d have:

 

(row, col, row\*col, U, D, L, R, 1)

 

However, if you did do this, and I would recommend doing so, so that you can go through the same thought process as I did, you would find that this is not expressive enough.

 

In other words, a linear model given these features, can’t accurately approximate Q.

 

\---

 

What I eventually decided to go with, was to add square terms, and have a separate set of features for each action.

 

`X = [`

`r && U,`

`c *&& U,`

`r*r && U,`

`c*c *&& U,`

`r*c && U,`

`1 && U,`

`r && D,`

`…`

`]`

 

So for each of the actions, we have row, column, row^2, col^2, row\*col, and 1, which represents not really a bias, but the one-hot encoded action.

 

There is however, still a lone bias term.

 

You might wonder, given so many features, if that still compresses Q.

 

So let’s calculate this.

 

For each of the 4 directions, we have 6 different features involving different combinations of row and column. So that’s 24 + 1 bias term so the total is 25.

 

If you were to store Q as a table, you’d have 9 states, and 4 actions per state, so in total that’s 36. So there’s still a bit of savings.

 

\---

 

In the code, I also give you the option of one-hot encoding all the state-action pairs, which is equivalent to just doing regular SARSA without any approximation.

 

So you can try that also to convince yourself that things are working.

 

In order to implement this, we keep a dictionary called SA2IDX which maps state-action pairs to a unique index in X.

 

This is similar to what you’ve seen in my NLP classes where we have a word2idx dictionary and we map each word in the vocabulary to a unique index in X.

 

 

## Semi-Gradient SARSA Code

 

In this section we are going to implement semi-gradient SARSA in code.

 

If you don’t want to try to code this yourself, although I highly recommend you do, the relevant file is approx\_semigradient\_sarsa\_control.py

 

Remember that this is for solving the control problem, so the goal is to find the optimal policy.

 

This is a semi-gradient method because we’re using temporal difference learning, and the target is not a true target, because it uses a model prediction.

 

Because of this, the gradient we use is also not a true gradient, so we call this a semi-gradient method.

 

At the top we have all our usual imports.

 

`import numpy as np`

`import matplotlib.pyplot as plt`

`from grid_world import standard_grid, negative_grid`

`from iterative_policy_evaluation import print_values, print_policy`

`from monte_carlo_es import max_dict`

`from sarsa import random_action, GAMMA, ALPHA, ALL_POSSIBLE_ACTIONS`

` `

`SA2IDX = {}`

`IDX = 0`

 

We also create a dictionary for mapping state-action pairs to indexes, and a global index variable that keeps track of the number of state-action pairs we’ve already seen so that it can assign the next index.

 

Next, we create our Model class.

 

`def sa2x(self, s, a):`

`# NOTE: using just (r, c, r*c, u, d, l, r, 1) is not expressive enough`

`return np.array([`

`s[0] - 1 if a == 'U' else 0,`

`s[1] - 1.5 if a == 'U' else 0,`

`(s[0]*s[1] - 3)/3 if a == 'U' else 0,`

`(s[0]*s[0] - 2)/2 if a == 'U' else 0,`

`(s[1]*s[1] - 4.5)/4.5 if a == 'U' else 0,`

`1 if a == 'U' else 0,`

`s[0] - 1 if a == 'D' else 0,`

`s[1] - 1.5 if a == 'D' else 0,`

`(s[0]*s[1] - 3)/3 if a == 'D' else 0,`

`(s[0]*s[0] - 2)/2 if a == 'D' else 0,`

`(s[1]*s[1] - 4.5)/4.5 if a == 'D' else 0,`

`1 if a == 'D' else 0,`

`s[0] - 1 if a == 'L' else 0,`

`s[1] - 1.5 if a == 'L' else 0,`

`(s[0]*s[1] - 3)/3 if a == 'L' else 0,`

`(s[0]*s[0] - 2)/2 if a == 'L' else 0,`

`(s[1]*s[1] - 4.5)/4.5 if a == 'L' else 0,`

`1 if a == 'L' else 0,`

`s[0] - 1 if a == 'R' else 0,`

`s[1] - 1.5 if a == 'R' else 0,`

`(s[0]*s[1] - 3)/3 if a == 'R' else 0,`

`(s[0]*s[0] - 2)/2 if a == 'R' else 0,`

`(s[1]*s[1] - 4.5)/4.5 if a == 'R' else 0,`

`1 if a == 'R' else 0,`

`1`

`])`

`# if we use SA2IDX, a one-hot encoding for every (s,a) pair`

`# in reality we wouldn't want to do this b/c we have just`

`# as many params as before`

`# x = np.zeros(len(self.theta))`

`# idx = SA2IDX[s][a]`

`# x[idx] = 1`

`# return x`

` `

`def predict(self, s, a):`

`x = self.sa2x(s, a)`

`return self.theta.dot(x)`

` `

`def grad(self, s, a):`

`return self.sa2x(s, a)`

 

The init function is the same as before, it just initializes theta. Notice how the dimensionality is now 25.

 

Next, we have our feature transformer function, sa2x. It creates all the features we talked about in the previous lecture.

 

You can also comment this out, since underneath I give you the option of one-hot encoding the state-action pairs as well.

 

Using that would be the equivalent of doing regular SARSA.

 

Next, we have the predict and gradient functions, which are the same as before.

 

Next, we have a function called getQs. The reason we need this is because at some point during SARSA, we need to take the argmax over Q, but we can’t do that if Q isn’t represented as a dictionary.

 

`def getQs(model, s):`

`# we need Q(s,a) to choose an action`

`# i.e. a = argmax[a]{ Q(s,a) }`

`Qs = {}`

`for a in ALL_POSSIBLE_ACTIONS:`

`q_sa = model.predict(s, a)`

`Qs[a] = q_sa`

`return Qs`

 

So the job of this function is to turn the Q predictions into a dictionary given some state s.

 

\---

 

Next, we have the main section.

 

We use the negative grid here but you are welcome and encouraged to try the standard grid too.

 

`if __name__ == '__main__':`

`grid = negative_grid(step_cost=-0.1)`

` `

`print "rewards:"`

`print_values(grid.rewards, grid)`

` `

`# no policy initialization, we will derive our policy from most recent Q`

`# enumerate all (s,a) pairs, each will have its own weight in our "dumb" model`

`# essentially each weight will be a measure of Q(s,a) itself`

`states = grid.all_states()`

`for s in states:`

`SA2IDX[s] = {}`

`for a in ALL_POSSIBLE_ACTIONS:`

`SA2IDX[s][a] = IDX`

`IDX += 1`

 

We print the rewards, and then we populate the SA2IDX dictionary.

 

Next, we initialize the model, and then we enter the main loop.

 

`# initialize model`

`model = Model()`

` `

`# repeat until convergence`

`t = 1.0`

`t2 = 1.0`

`deltas = []`

`for it in xrange(20000):`

`if it % 100 == 0:`

`t += 10e-3`

`t2 += 0.01`

`if it % 1000 == 0:`

`print "it:", it`

`alpha = ALPHA / t2`

 

Notice I have 2 time variables here, t and t2, since I want the learning rate and epsilon to decrease at different rates.

 

These are hyperparameters, so you would only be able to find good values via experimentation.

 

Next, we go into the main loop. Notice how we need to use the getQs function here before we use max\_dict.

 

\---

 

Next, we enter the game loop.

 

`s = (2, 0) # start state`

`grid.set_state(s)`

` `

`# get Q(s) so we can choose the first action`

`Qs = getQs(model, s)`

` `

`a = max_dict(Qs)[0]`

`a = random_action(a, eps=0.5/t) # epsilon-greedy`

`biggest_change = 0`

`while not grid.game_over():`

`r = grid.move(a)`

`s2 = grid.current_state()`

` `

`# we need the next action as well since Q(s,a) depends on Q(s',a')`

`# if s2 not in policy then it's a terminal state, all Q are 0`

`old_theta = model.theta.copy()`

`if grid.is_terminal(s2):`

`model.theta += alpha*(r - model.predict(s, a))*model.grad(s, a)`

`else:`

`# not terminal`

`Qs2 = getQs(model, s2)`

`a2 = max_dict(Qs2)[0]`

`a2 = random_action(a2, eps=0.5/t) # epsilon-greedy`

` `

`# we will update Q(s,a) AS we experience the episode`

`model.theta += alpha*(r + GAMMA*model.predict(s2, a2) - model.predict(s, a))*model.grad(s, a)`

`# next state becomes current state`

`s = s2`

`a = a2`

` `

`biggest_change = max(biggest_change, np.abs(model.theta - old_theta).sum())`

`deltas.append(biggest_change)`

` `

`plt.plot(deltas)`

`plt.show()`

 

Similar to the TD(0) prediction script, we have a different target depending on whether or not we’re in a terminal state.

 

If we’re in a terminal state, I already know Q(s’,a’) is 0, so I can make a more accurate target.

 

Everything else in the script should be stuff you’ve seen before.

 

Run this and see what you get.

 

 

## Summary and Next Steps

 

In this section we are going to summarize what we covered in this chapter, and what we covered in this book.

 

We are also going to discuss possible next steps - some ideas for what to study next in reinforcement learning.

 

\---

 

This chapter was all about approximation methods.

 

We learned early on in the course that the state space of an MDP can quickly grow too large to enumerate, and hence, trying to store a value function that needs to be defined for every state in the state space, can be infeasible.

 

Approximation methods allow us to parameterize the value function, so that effectively we need a smaller number of parameters than the size of the state space.

 

Specifically, we learned that differentiable models are a good fit, because we can use stochastic gradient descent, and continue learning in an online fashion, like we’ve done throughout the book.

 

Remember that online learning is desirable, because episodes can be very long, so it’s good if our agent can improve during the episode.

 

The type of differentiable model we looked at in this course was linear regression, but we can just as easily apply it to neural networks and deep learning.

 

Using linear regression meant we had to engineer our own features, since the raw features we had - the i coordinate and the j coordinate, did not yield an expressive-enough model.

 

\---

 

We applied approximation methods to 3 algorithms we learned about earlier in the course.

 

First, we used approximation with Monte Carlo prediction.

 

Next, we used approximation with a natural extension of Monte Carlo prediction, TD(0) prediction.

 

We learned that, because TD(0) requires us to use the model to form the target, the gradient we used for gradient descent is not a true gradient, so we call it a semi-gradient method.

 

Finally, we used approximation for control - in particular, we applied it to the SARSA algorithm. Since SARSA is also a temporal difference method, we again were not using the true gradient, but a semi-gradient.

 

\---

 

You may have wondered why we didn’t apply approximation methods to Q-Learning.

 

Recall that Q-Learning is an off-policy method.

 

Some sources have stated that using approximation methods for off-policy control methods do not have good convergence characteristics.

 

However, if you want to try to modify the existing SARSA approximation script to use Q-Learning instead, you are encouraged to do so.

 

Remember that the main difference between SARSA and Q-Learning is that the Q we use for the update does not necessarily correspond to the next action we take.

 

So basically the line of code where you choose your action goes somewhere else.

 

\---

 

To put all this into context, let’s now go through an overview of everything we accomplished in this course.

 

We started out this course looking at the multi-armed bandit problem, which you first saw in my Bayesian Machine Learning, A/B testing course.

 

You learned about the explore-exploit dilemma, which is central to reinforcement learning.

 

We saw 4 different ways to solve the multi-armed bandit problem, including epsilon-greedy, optimistic initial values, UCB1, and Thompson sampling.

 

Next, you learned about some more of the basic definitions in reinforcement learning, and you applied them to create a tic-tac-toe agent.

 

By coding a tic-tac-toe agent, we were able to get a feel for how reinforcement learning works, and the types of algorithms we use for learning.

 

\---

 

In the next chapter, we formalized all the concepts we learned about reinforcement learning into a framework of Markov Decision Processes, or MDPs.

 

You learned about policies, state-value functions, and action-value functions.

 

You learned about the concept of returns, which is the sum of discounted future rewards.

 

\---

 

In the next chapters, we looked at 3 different ways of solving MDPs.

 

In particular, we were interested in solving 2 problems: the prediction problem, which is finding the value function given a policy, and the control problem, which is finding the optimal policy.

 

In the first section on Dynamic Programming, we directly applied Bellman’s Equation to solve both of these problems.

 

You learned about the idea of policy iteration, and the more efficient way of doing it, called value iteration.

 

We learned that Dynamic Programming isn’t really practical because it doesn’t learn from experience and assumes we know all the relevant probability distributions.

 

So in the next section, we looked at Monte Carlo methods, which learn only from experience.

 

With Monte Carlo, instead of calculating expected values precisely using probability distributions, we instead estimate them using sample means.

 

The problem with Monte Carlo is that it’s not fully online, which is a problem if you have very long episodes or continuing tasks.

 

The final method we looked at was temporal difference learning, which combines aspects of both Dynamic Programming and Monte Carlo.

 

TD learning uses bootstrapping, which means it makes estimates based on other estimates, and this allows it to be fully online, since we don’t need to wait for an episode to be over before making updates.

 

At the same time, TD learning also learns from experience, which means we don’t need a probabilistic model of the MDP.

 

\---

 

In the final section of the course, we learned how all 3 of the previous methods can be infeasible for large state spaces, so we looked at ways of compressing the value function.

 

The only requirement for our function approximators is that they be differentiable.

 

As you know, deep learning methods are also differentiable.

 

Libraries like Theano and TensorFlow automatically calculate gradients for us, which would make the update equations easier in the case where we have lots of parameters and complex functions.

 

We’ll be looking at deep reinforcement learning in the followup to this course.

 

\---

 

There are also some other things we didn’t consider in this course, that would be worth studying now that you know the basics.

 

We know that state-spaces are not necessarily discrete. For example, if our state space is an image of our environment, images represent the real world - light intensity in a continuous 3-dimensional space. Light intensity is also continuous.

 

We know that action-spaces are not necessarily discrete either. For example, if your agent needs to decide how much force to apply to a motor. Force is a continuous variable.

 

\---

 

Another point to consider is that we’ve so far only parameterized the value function.

 

In a future course, we’ll also look at how we can parameterize the policy, pi(a | s).

 

We call this the “policy gradient” method.

 

\---

 

Another point to consider is that when we learned from experience in this course, we learned from our current experience only, and we did stochastic gradient descent based on our most recent action.

 

What happens though, as you play the episodes, you accumulate (input, target) pairs.

 

In essence, what you’re doing is accumulating training data.

 

Practically speaking, you could even store these input-target pairs in a file and use them to train later.

 

So even though we are doing online learning, there’s no reason we can’t also use our previous experience as well.

 

In other words, I can replay a previous episode, and continue to update the parameters of my model with gradient descent based on those old episodes.

 

\---

 

So there are still lots of things to learn in the field of reinforcement learning.

 

As you’ve seen, even at the fundamental level we still have a lot of open questions, and things that we assume to be true that haven’t even been proven.

 

At the same time, this was a massive book, with tons of different algorithms, so I hope you can now appreciate how far-reaching the field of reinforcement learning is.

 

Thanks for reading!

## 读累了记得休息一会哦~

 

### **网站：**[https://elib.cc](https://elib.cc)

#### 百万电子书免费下载

 

# Conclusion

 

 I really hope you had as much fun reading this book as I did making it.

 

Did you find anything confusing? Do you have any questions?

 

I am always available to help. Just email me at: [info@lazyprogrammer.me](mailto:info@lazyprogrammer.me)

 

I do 1:1 coaching and consulting as well.

 

Do you want to learn more about deep learning? Perhaps online courses are more your style. I happen to have a few of them.

 

My online courses are a lot like the book, but you get to see me derive the formulas and write the code live. There are also a ton more examples, like how to optimize an e-commerce store and facial expression recognition.

 

For any of these courses, just use the coupon code AMZN12 (on [udemy.com](http://udemy.com) ) or just AMZN (on [deeplearningcourses.com](http://deeplearningcourses.com) ) to get 88% off. It is my thank you for purchasing this book.

 

[Deep Learning Prerequisites: Linear Regression in Python](https://deeplearningcourses.com/c/data-science-linear-regression-in-python?coupon=AMZN)

Link 1: [https://deeplearningcourses.com/c/data-science-linear-regression-in-python?coupon=AMZN](https://deeplearningcourses.com/c/data-science-linear-regression-in-python?coupon=AMZN)

Link 2: [https://www.udemy.com/data-science-linear-regression-in-python/?couponCode=AMZN12](https://www.udemy.com/data-science-linear-regression-in-python/?couponCode=AMZN12)

\* A great first thing to learn if you know nothing about machine learning

\* Requires only basic calculus, some linear algebra, and Python coding

\* Prove Moore’s Law is true using linear regression

\* Predict systolic blood pressure using age and body weight

 

[Deep Learning Prerequisites: Logistic Regression in Python](https://deeplearningcourses.com/c/data-science-logistic-regression-in-python?coupon=AMZN)

Link 1: [https://deeplearningcourses.com/c/data-science-logistic-regression-in-python?coupon=AMZN](https://deeplearningcourses.com/c/data-science-logistic-regression-in-python?coupon=AMZN)

Link 2: [https://www.udemy.com/data-science-logistic-regression-in-python/?couponCode=AMZN12](https://www.udemy.com/data-science-logistic-regression-in-python/?couponCode=AMZN12)

\* Logistic Regression is the basic building block of neural networks (i.e. it is a “neuron” model)

\* In-depth look at binary classification

\* How to derive features from your data

\* Harder than Linear Regression because the solution can’t be found in “closed-form”, we need numerical methods (called gradient descent)

\* Teaches you all of the tools you need for deep learning and neural networks - in fact you’ll find that neural networks just use all the same tools with just a slightly more complicated model

\* First look at the facial expression recognition problem

\* Apply logistic regression to optimize an e-commerce store

 

[Data Science: Deep Learning in Python](https://deeplearningcourses.com/c/data-science-deep-learning-in-python?coupon=AMZN) (deep learning pt1)

Link 1: [https://deeplearningcourses.com/c/data-science-deep-learning-in-python?coupon=AMZN](https://deeplearningcourses.com/c/data-science-deep-learning-in-python?coupon=AMZN)

Link 2: [https://www.udemy.com/data-science-deep-learning-in-python/?couponCode=AMZN12](https://www.udemy.com/data-science-deep-learning-in-python/?couponCode=AMZN12)

\* Put “neurons” together to make “neural networks”, a.k.a. “networks of neurons”

\* Learn how neural networks are more powerful than linear methods (like linear and logistic regression)

\* Derive the backpropagation algorithm using only principles you already know

\* Go from binary classification to multi-class classification

\* Attempt the facial expression recognition problem again

\* Apply neural networks to optimize an e-commerce store

 

[Data Science: Practical Deep Learning in Theano and TensorFlow](https://deeplearningcourses.com/c/data-science-deep-learning-in-theano-tensorflow?coupon=AMZN) (deep learning pt2)

Link 1: [https://deeplearningcourses.com/c/data-science-deep-learning-in-theano-tensorflow?coupon=AMZN](https://deeplearningcourses.com/c/data-science-deep-learning-in-theano-tensorflow?coupon=AMZN)

Link 2: [https://www.udemy.com/data-science-deep-learning-in-theano-tensorflow/?couponCode=AMZN12](https://www.udemy.com/data-science-deep-learning-in-theano-tensorflow/?couponCode=AMZN12)

\* Learn an easier and more flexible way to write neural networks with Theano and TensorFlow

\* Methods for improving backpropagation - momentum, adaptive learning rates

\* Speed up training using the GPU on AWS (Amazon Web Services)

\* Advanced regularization techniques (dropout, etc.)

\* Knowing how to use Theano/TensorFlow is absolutely required to get to the next stage -> writing your own convolutional neural networks

 

[Deep Learning: Convolutional Neural Networks in Python](https://deeplearningcourses.com/c/deep-learning-convolutional-neural-networks-theano-tensorflow?coupon=AMZN) (deep learning pt3)  
Link 1: [https://deeplearningcourses.com/c/deep-learning-convolutional-neural-networks-theano-tensorflow?coupon=AMZN](https://deeplearningcourses.com/c/deep-learning-convolutional-neural-networks-theano-tensorflow?coupon=AMZN)

Link 2: [https://www.udemy.com/deep-learning-convolutional-neural-networks-theano-tensorflow/?couponCode=AMZN12](https://www.udemy.com/deep-learning-convolutional-neural-networks-theano-tensorflow/?couponCode=AMZN12)

\* Learn your first advanced neural network architecture for images

\* Learn about the convolution operation and how it’s applied to visual effects like blurring and edge detection

\* Apply convolution to audio effects like echo

\* Write your own CNN with Theano and TensorFlow

\* Attempt the facial expression recognition problem again

 

[Cluster Analysis & Unsupervised Machine Learning in Python](https://deeplearningcourses.com/c/cluster-analysis-unsupervised-machine-learning-python?coupon=AMZN)

Link 1: [https://deeplearningcourses.com/c/cluster-analysis-unsupervised-machine-learning-python?coupon=AMZN](https://deeplearningcourses.com/c/cluster-analysis-unsupervised-machine-learning-python?coupon=AMZN)

Link 2: [https://www.udemy.com/cluster-analysis-unsupervised-machine-learning-python/?couponCode=AMZN12](https://www.udemy.com/cluster-analysis-unsupervised-machine-learning-python/?couponCode=AMZN12)

\* K-Means Clustering

\* Hierarchical Clustering

\* Gaussian Mixture Models

\* Provides background that is very helpful for both Hidden Markov Models and Unsupervised Deep Learning

 

[Unsupervised Deep Learning in Python](https://deeplearningcourses.com/c/unsupervised-deep-learning-in-python?coupon=AMZN) (deep learning pt4)  
Link 1: [https://deeplearningcourses.com/c/unsupervised-deep-learning-in-python?coupon=AMZN](https://deeplearningcourses.com/c/unsupervised-deep-learning-in-python?coupon=AMZN)

Link 2: [https://www.udemy.com/unsupervised-deep-learning-in-python/?couponCode=AMZN12](https://www.udemy.com/unsupervised-deep-learning-in-python/?couponCode=AMZN12)

\* Derive principal components analysis (PCA) from scratch, and understand its limitations

\* Use PCA for data visualization

\* Make the connection between PCA and unsupervised neural networks like the Autoencoder

\* Learn a nonlinear visualization technique called t-SNE (jointly developed by the godfather of deep learning, Geoffrey Hinton)

\* Learn how autoencoders and RBMs (Restricted Boltzmann Machines) can be used for pretraining a neural network and help with the vanishing gradient problem, leading to improved supervised performance

 

[Data Science: Natural Language Processing in Python](https://deeplearningcourses.com/c/data-science-natural-language-processing-in-python?coupon=AMZN)

Link 1: [https://deeplearningcourses.com/c/data-science-natural-language-processing-in-python?coupon=AMZN](https://deeplearningcourses.com/c/data-science-natural-language-processing-in-python?coupon=AMZN)

Link 2: [https://www.udemy.com/data-science-natural-language-processing-in-python/?couponCode=AMZN12](https://www.udemy.com/data-science-natural-language-processing-in-python/?couponCode=AMZN12)

\* Learn about how machine learning can be applied to language, text, and speech

\* Write a spam detection algorithm

\* Perform sentiment analysis

\* Learn how to use the NLTK library

\* Visualize the results of latent semantic analysis (LSA)

\* Write your own article spinner

 

[Unsupervised Machine Learning: Hidden Markov Models in Python](https://deeplearningcourses.com/c/unsupervised-machine-learning-hidden-markov-models-in-python?coupon=AMZN)

Link 1: [https://deeplearningcourses.com/c/unsupervised-machine-learning-hidden-markov-models-in-python?coupon=AMZN](https://deeplearningcourses.com/c/unsupervised-machine-learning-hidden-markov-models-in-python?coupon=AMZN)

Link 2: [https://www.udemy.com/unsupervised-machine-learning-hidden-markov-models-in-python/?couponCode=AMZN12](https://www.udemy.com/unsupervised-machine-learning-hidden-markov-models-in-python/?couponCode=AMZN12)

\* Classic theory of Markov chains

\* Real-world application: Google’s PageRank

\* Language-modeling and sequence modeling in general

\* Possible applications: Stock price modeling, time series, DNA

\* Apply deep learning skills: Find HMM parameters using Theano and gradient descent

\* Will teach you critical skills for tackling RNNs (recurrent neural networks)

 

[Deep Learning: Recurrent Neural Networks in Python](https://deeplearningcourses.com/c/deep-learning-recurrent-neural-networks-in-python?coupon=AMZN) (deep learning pt5)

Link 1: [https://deeplearningcourses.com/c/deep-learning-recurrent-neural-networks-in-python?coupon=AMZN](https://deeplearningcourses.com/c/deep-learning-recurrent-neural-networks-in-python?coupon=AMZN)

Link 2: [https://www.udemy.com/deep-learning-recurrent-neural-networks-in-python/?couponCode=AMZN12](https://www.udemy.com/deep-learning-recurrent-neural-networks-in-python/?couponCode=AMZN12)

\* Also focus on time series but are much more powerful than HMMs (no Markov assumption or computational underflow)

\* Learn more about the popular LSTM (long short-term memory) unit and GRU (gated recurrent unit)

\* Better language modeling and poetry generation

 

[Deep Learning: Natural Language Processing in Python](https://deeplearningcourses.com/c/natural-language-processing-with-deep-learning-in-python?coupon=AMZN) (deep learning pt6)

Link 1: [https://deeplearningcourses.com/c/natural-language-processing-with-deep-learning-in-python?coupon=AMZN](https://deeplearningcourses.com/c/natural-language-processing-with-deep-learning-in-python?coupon=AMZN)

Link 2: [https://www.udemy.com/natural-language-processing-with-deep-learning-in-python/?couponCode=AMZN12](https://www.udemy.com/natural-language-processing-with-deep-learning-in-python/?couponCode=AMZN12)

\* Combine NLP with deep learning

\* word2vec (famous for king - man = queen - woman)

\* GLoVe (similar to word2vec, created at Stanford, team is famous for their NLP work)

\* Recursive Neural Networks (well-suited for natural language understanding, state-of-the-art for sentiment analysis)

 

[Data Science: Supervised Machine Learning in Python](https://deeplearningcourses.com/c/data-science-supervised-machine-learning-in-python?coupon=AMZN)

Link 1: [https://deeplearningcourses.com/c/data-science-supervised-machine-learning-in-python?coupon=AMZN](https://deeplearningcourses.com/c/data-science-supervised-machine-learning-in-python?coupon=AMZN)

Link 2: [https://www.udemy.com/data-science-supervised-machine-learning-in-python/?couponCode=AMZN12](https://www.udemy.com/data-science-supervised-machine-learning-in-python/?couponCode=AMZN12)

\* Classic machine learning algorithms

\* Geometrical and algorithmic, no calculus required!

\* Write everything from scratch, no cheating with Sci-Kit Learn

\* K-Nearest Neighbor

\* Naive Bayes and Bayesian Classifiers in General

\* Decision Trees

\* Perceptron (ancestor of deep learning)

\* Practical considerations like overfitting and cross-validation

\* Build your own machine learning web-service

 

[Bayesian Machine Learning in Python: A/B Testing](https://deeplearningcourses.com/c/bayesian-machine-learning-in-python-ab-testing?coupon=AMZN)

Link 1: [https://deeplearningcourses.com/c/bayesian-machine-learning-in-python-ab-testing?coupon=AMZN](https://deeplearningcourses.com/c/bayesian-machine-learning-in-python-ab-testing?coupon=AMZN)

Link 2: [https://www.udemy.com/bayesian-machine-learning-in-python-ab-testing?couponCode=AMZN12](https://www.udemy.com/bayesian-machine-learning-in-python-ab-testing?couponCode=AMZN12)

\* Go from frequentist probability to Bayesian probability

\* Learn how to apply adaptive online learning to A/B tests, and why traditional A/B tests are insufficient

\* Understand the “explore-exploit” dilemma - required for reinforcement learning

\* Fundamental math required for further study in Bayesian Machine Learning and Inference

 

[Ensemble Machine Learning in Python: Random Forest and AdaBoost](https://deeplearningcourses.com/c/machine-learning-in-python-random-forest-adaboost?coupon=AMZN)

Link 1: [https://deeplearningcourses.com/c/machine-learning-in-python-random-forest-adaboost?coupon=AMZN](https://deeplearningcourses.com/c/machine-learning-in-python-random-forest-adaboost?coupon=AMZN)

Link 2: [https://www.udemy.com/machine-learning-in-python-random-forest-adaboost/?couponCode=AMZN12](https://www.udemy.com/machine-learning-in-python-random-forest-adaboost/?couponCode=AMZN12)

\* Combine models from earlier machine learning courses to create much more powerful predictors

\* Learn and derive the all-important bias-variance tradeoff

\* Understand the theory and implement 2 of the most popular and time-tested ensemble methods: Random Forest and AdaBoost

 

[Artificial Intelligence: Reinforcement Learning in Python](https://deeplearningcourses.com/c/artificial-intelligence-reinforcement-learning-in-python?coupon=AMZN)

Link 1: [https://deeplearningcourses.com/c/artificial-intelligence-reinforcement-learning-in-python?coupon=AMZN](https://deeplearningcourses.com/c/artificial-intelligence-reinforcement-learning-in-python?coupon=AMZN)

Link 2: [https://www.udemy.com/artificial-intelligence-reinforcement-learning-in-python/?couponCode=AMZN12](https://www.udemy.com/artificial-intelligence-reinforcement-learning-in-python/?couponCode=AMZN12)

\* Learn a completely different learning paradigm (compared to supervised and unsupervised learning)

\* Learn how to code an agent that plays “games” and interacts with environments (anything from beating world champions in Go to self-driving cars)

\* Much more potential than simply labeling things (classification), function approximation (regression), and modeling data distributions (unsupervised learning and clustering)

 

[Deep Learning Prerequisites: The Numpy Stack in Python](https://deeplearningcourses.com/c/deep-learning-prerequisites-the-numpy-stack-in-python)

Link 1: [https://deeplearningcourses.com/c/deep-learning-prerequisites-the-numpy-stack-in-python](https://deeplearningcourses.com/c/deep-learning-prerequisites-the-numpy-stack-in-python)

Link 2: [https://www.udemy.com/deep-learning-prerequisites-the-numpy-stack-in-python](https://www.udemy.com/deep-learning-prerequisites-the-numpy-stack-in-python)

\* Take this if you have trouble following the coding examples in my machine learning courses, it’s free!

\* Covers most-used features of the Numpy stack

\* Covers Numpy, Scipy, Pandas, Matplotlib

 

[SQL for Marketers: Dominate data analytics, data science, and big data](https://deeplearningcourses.com/c/sql-for-marketers-data-analytics-data-science-big-data?coupon=AMZN)

Link 1: [https://deeplearningcourses.com/c/sql-for-marketers-data-analytics-data-science-big-data?coupon=AMZN](https://deeplearningcourses.com/c/sql-for-marketers-data-analytics-data-science-big-data?coupon=AMZN)

Link 2: [https://www.udemy.com/sql-for-marketers-data-analytics-data-science-big-data/?couponCode=AMZN12](https://www.udemy.com/sql-for-marketers-data-analytics-data-science-big-data/?couponCode=AMZN12)

\* SQL - structured query language - a language that can be applied to databases as small as the ones sitting on your iPhone, to databases as large as the ones that span multiple continents

\* Learn the mechanics of the language

\* Apply it to real-world data analytics and marketing problems

\* Write SQL in Spark - all these skills apply to big data!

 

Finally, I am always giving out coupons and letting you know when you can get my stuff for free . But you can only do this if you are a current student of mine! Here are some ways I notify my students about coupons and free giveaways:

 

My newsletter, which you can sign up for at [http://lazyprogrammer.me](http://lazyprogrammer.me) (it comes with a free 6-part intro to machine learning course)

 

My Twitter, [https://twitter.com/lazy\_scientist](https://twitter.com/lazy_scientist)

 

My Facebook page, [https://facebook.com/lazyprogrammer.me](https://facebook.com/lazyprogrammer.me) (don’t forget to hit “like”!)