| Machine learning | Program synthesis |
|---|---|
| Model: differentiable parametric function | Model: graph of operators from a programming language |
| Engine: gradient descent | Engine: discrete search (such as genetic search) |
| Requires a lot of data to produce reliable results | Data-efficient, can work with a couple of training examples |

Program synthesis is how we're going to add program-centric abstraction capabilities to our AI systems. It's the missing piece of the puzzle. I mentioned earlier that deep learning techniques were entirely unusable on ARC, a reasoning-focused intelligence test. Meanwhile, very crude program-synthesis approaches are already producing very promising results on this benchmark.

# ### 14.5.2 Blending together deep learning and program synthesis

Of course, deep learning isn't going anywhere. Program synthesis isn't its replacement; it is its complement. It's the hemisphere that has been so far missing from our artificial brains. We're going to be leveraging both, in combination. There are two major ways this will take place:

+   1. Developing systems that integrate both deep learning modules and discrete algorithmic modules
+   2. Using deep learning to make the program search process itself more efficient

Let's review each of these possible avenues.

# INTEGRATING DEEP LEARNING MODULES AND ALGORITHMIC MODULES INTO HYBRID SYSTEMS

Today, the most powerful AI systems are hybrid: they leverage both deep learning models and handcrafted symbol-manipulation programs. In DeepMind's AlphaGo, for example, most of the intelligence on display is designed and hardcoded by human programmers (such as Monte Carlo Tree Search). Learning from data happens only in specialized submodules (value networks and policy networks). Or consider autonomous vehicles: a self-driving car is able to handle a large variety of situations because it maintains a model of the world around it—a literal 3D model—full of assumptions hardcoded by human engineers. This model is constantly updated via deep learning perception modules that interface it with the surroundings of the car.

For both of these systems—AlphaGo and self-driving vehicles—the combination of human-created discrete programs and learned continuous models is what unlocks a level of performance that would be impossible with either approach in isolation, such as an end-to-end deep net or a piece of software without ML elements. So far, the discrete algorithmic elements of such hybrid systems are painstakingly hardcoded by human engineers. But in the future, such systems may be fully learned, with no human involvement.