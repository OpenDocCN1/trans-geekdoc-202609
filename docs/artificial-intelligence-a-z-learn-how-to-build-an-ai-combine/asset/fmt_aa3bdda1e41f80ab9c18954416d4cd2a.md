
# Preface

Nileriver Publications is the finest book publishers in the world. We publish excellent books to the learning environment. One of the notable secrets for our success in public friendly books is that we note the different approaches to project development that are needed to meet one or more of differing objectives in all the activities we do and try to put everything in the book. The main goal of our book writing is to give the subject to all the ranges of learners right from the basics to the advanced level. We believe in sharing knowledge and we conduct lot of activities to share the knowledge to the world which you can get it from our website. With the experience of publishing 20,000 books so far we are becoming better and better and getting very close to the learners which exactly matches the requirement at the hour of need. Nileriver Team is proud to receive thousands of reviews which say our team is the best in providing solutions. We continue to work hard and provide the best for the years coming.

# Table of Contents

- [Preface](#part0001.xhtml)
- [Fundamentals of Reinforcement Learning](#part0003.xhtml)
  - [Reinforcement Learning](#part0003.xhtml#aNW)
  - [Exploration Vs., Exploitation](#part0003.xhtml#toc2_Exploration_Vs.__Exploitation)
  - [WHAT IS REINFORCEMENT LEARNING](#part0003.xhtml#toc3_WHAT_IS_REINFORCEMENT_LEARNING)
  - [1/ UPPER CONFIDENCE BOUND REINFORCEMENT LEARNING](#part0003.xhtml#aNZ)
  - [2/ THOMPSON SAMPLING REINFORCEMENT LEARNING](#part0003.xhtml#aP0)
  - [Main components In RL Process:](#part0003.xhtml#aP1)
  - [RL Process: Reward](#part0003.xhtml#aP2)
  - [RL Process: Goals and Actions:](#part0003.xhtml#aP3)
  - [RL Process: State:](#part0003.xhtml#aP4)
  - [RL Agent: Policy](#part0003.xhtml#toc10_RL_Agent__Policy)
  - [RL Agent: Model](#part0003.xhtml#aP6)
  - [Q – Learning Intuition](#part0003.xhtml#toc23_Q___Learning_Intuition)
  - [Let’s first understand what is a denial-of-service (DoS) attack](#part0003.xhtml#toc13_Let_s_first_understand_what_is_a_denial-of-service__DoS__attack)
  - [TCP/IP Stack Implementation Weaknesses](#part0003.xhtml#aP9)
  - [TCP/IP Weaknesses](#part0003.xhtml#toc15_TCP_IP_Weaknesses)
  - [Brute Force](#part0003.xhtml#aPB)
  - [Identify a DDoS Attack Early](#part0003.xhtml#aPC)
  - [Overprovision Bandwidth](#part0003.xhtml#aPD)
  - [Defend at Network Perimeter (if You Run Your Own Web Server)](#part0003.xhtml#toc19_Defend_at_Network_Perimeter__if_You_Run_Your_Own_Web_Server_)
  - [Call Your ISP or Hosting Provider](#part0003.xhtml#aPF)
  - [Call a DDoS Specialist](#part0003.xhtml#toc21_Call_a_DDoS_Specialist)
  - [Policy vs Plan](#part0003.xhtml#aPH)
  - [Q-Learning Visualization](#part0003.xhtml#aPJ)
  - [Q-learning is basically a DP problem that is solved by a Fixed Point Method.](#part0003.xhtml#aPK)
  - [What is “Q”?](#part0003.xhtml#aPM)
  - [Q learning - Algorithm:](#part0003.xhtml#toc26_Q_learning_-_Algorithm_)
  - [Deep Q-Learning](#part0003.xhtml#toc34_Deep_Q-Learning)
  - [Deep Q-Learning](#part0003.xhtml#aPR)
  - [Pseudo Code:](#part0003.xhtml#aPS)
  - [How deep-Q networks (DQN) work](#part0003.xhtml#aPT)
  - [Intuition behind Q-Learning :](#part0003.xhtml#toc31_Intuition_behind_Q-Learning__)
  - [Deep reinforcement learning and reinforcement learning](#part0003.xhtml#aPV)
  - [Does AlphaGo use Deep Q-Learning](#part0003.xhtml#toc33_Does_AlphaGo_use_Deep_Q-Learning)
  - [Deep Convolutional Q-Learning Intuition](#part0003.xhtml#toc43_Deep_Convolutional_Q-Learning_Intuition)
  - [Q-learning and neural networks work together](#part0003.xhtml#aPY)
  - [Intuitive explanation of Convolutional Neural Networks](#part0003.xhtml#aPZ)
  - [Deep neural networks, Machine learning, Deep learning](#part0003.xhtml#toc37_Deep_neural_networks__Machine_learning__Deep_learning)
  - [What is a convolutional neural network?](#part0003.xhtml#aR1)
  - [Layers Of CNN](#part0003.xhtml#aR2)
  - [Pooling](#part0003.xhtml#aR3)
  - [Fully Connected Layer](#part0003.xhtml#aR4)
  - [Applications of CNN](#part0003.xhtml#aR5)
  - [A3C Intuition](#part0003.xhtml#aR6)
  - [DQN, PPO, and A3C](#part0003.xhtml#aR7)
  - [Deep deterministic policy gradient](#part0003.xhtml#aR8)
  - [Art algorithms in Machine Learning?](#part0003.xhtml#toc46_Art_algorithms_in_Machine_Learning_)
  - [Delayed reward in reinforcement learning](#part0003.xhtml#toc47_Delayed_reward_in_reinforcement_learning)
  - [Artificial Neural Networks](#part0003.xhtml#toc55_Artificial_Neural_Networks)
  - [What is neural network concept?](#part0003.xhtml#toc49_What_is_neural_network_concept_)
  - [Now comes the Neural Network.](#part0003.xhtml#toc50_Now_comes_the_Neural_Network.)
  - [Contemporize NN](#part0003.xhtml#toc51_Contemporize_NN)
  - [Convolutional neural network](#part0003.xhtml#toc52_Convolutional_neural_network)
  - [How does a neural network work](#part0003.xhtml#toc53_How_does_a_neural_network_work)
  - [Deep Neural Network / Artificial Neural Network](#part0003.xhtml#aRH)
  - [Convolutional neural networks](#part0003.xhtml#aRJ)
  - [Convolutional neural network (CNN)](#part0003.xhtml#aRK)

# Fundamentals of Reinforcement Learning

## Reinforcement Learning

**Reinforcement Learning** is a type of Machine Learning used extensively in **Artificial Intelligence** and likely the act of utmost plausible task. And in a bit of rage for perfection in this pretext put simply, it is all about learning through experience. You put a dumb agent in an environment where it will start off with random actions and over time, through experience, it’ll figure out what to do on its own for your project information. Further getting things into your control so our dumb agent gets smarter over time and likely the act of utmost plausible task. Since for a purpose getting into details of this this process where our dumb agent performs an action to get a reward and goes into the next stage is called a **Markov Decision Process (MDP)**. Depending on necessity in an MDP, the good part is that the past experiences and encounters can be discarded as they are encrypted in the present state and likely the act of utmost plausible task. Further getting things into your control so the future state is decided based on where we presently stand and you observe the changes. Because of such importance and credibility more formally, our agent performs an action `aa` in a state `ss` and ends up in a new state `s′s′`. Given the present scenario, the future is independent of the past. That’s the beauty of it :P In general, an MDP involves these 4 things…

- A set of States
- A set of Actions
- A Transition Function which implements an action is the present state to get to the next new state and likely the act of utmost plausible task. Since for a purpose getting into details of this this could also incorporate some degree of randomness as we don’t live in an ideal universe.
- A Reward Function that will decide what rewards we receive for our actions.
