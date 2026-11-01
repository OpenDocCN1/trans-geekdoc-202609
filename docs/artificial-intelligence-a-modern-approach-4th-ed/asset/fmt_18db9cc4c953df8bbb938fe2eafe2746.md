
Tristan Harris’s time well spent movement at the Center for Humane Technology is a step towards giving us more well-rounded choices (Harris, 2016). The movement addresses an issue that was recognized by Herbert Simon in 1971: “A wealth of information creates a poverty of attention.” Perhaps in the future we will have personal agents that stick up for our true long-term interests rather than the interests of the corporations whose apps currently fill our devices. It will be the agent’s job to mediate the offerings of various vendors, protect us from addictive attention-grabbers, and guide us towards the goals that really matter to us.

Time well spent
Personal agent

### Learning
[Chapters 19](#Chapter19-00.xhtml), [21](#Chapter21-00.xhtml), [22](#Chapter22-00.xhtml), and [23](#Chapter23-00.xhtml) described how agents can learn. Current algorithms can cope with quite large problems, reaching or exceeding human capabilities in many tasks—as long as we have sufficient training examples and we are dealing with a predefined vocabulary of features and concepts. But learning can stall when data are sparse, or unsupervised, or when we are dealing with complex representations.

Much of the recent resurgence of AI in the popular press and in industry is due to the success of deep learning ([Chapter 22](#Chapter22-00.xhtml)). On the one hand, this can be seen as the incremental maturation of the subfield of neural networks. On the other hand, we can see it as a revolutionary leap in capabilities spurred by a confluence of factors: the availability of more training data thanks to the Internet, increased processing power from specialized hardware, and a few algorithmic tricks, such as generative adversarial networks (`GANs`), batch normalization, dropout, and the rectified linear (`ReLU`) activation function.

The future should see continued emphasis on improving deep learning for the tasks it excels at, and also extending it to cover other tasks. The brand name “deep learning” has proven to be so popular that we should expect its use to continue, even if the mix of techniques that fuel it changes considerably.

We have seen the emergence of the field of data science as the confluence of statistics, programming, and domain expertise. While we can expect to see continued development in the tools and techniques necessary to acquire, manage, and maintain big data, we will also need advances in transfer learning so that we can take advantage of data in one domain to improve performance on a related domain.

The vast majority of machine learning research today assumes a factored representation, learning a function `h:ℝ^(n)→ℝ` for regression and `h:ℝ^(n)→{0,1}` for classification. Machine learning has been less successful for problems that have only a small amount of data, or problems that require the construction of new structured, hierarchical representations. Deep learning, especially with convolutional networks applied to computer vision problems, has demonstrated some success in going from low-level pixels to intermediate-level concepts like Eye and Mouth, then to Face, and finally to Person or Cat.

A challenge for the future is to more smoothly combine learning and prior knowledge. If we give a computer a problem it has not encountered before—say, recognizing different models of cars—we don’t want the system to be powerless until it has been fed millions of labeled examples.

The ideal system should be able to draw on what it already knows: it should already have a model of how vision works, and how the design and branding of products in general work; now it should use transfer learning to apply that to the new problem of car models. It should be able to find on its own information about car models, drawing from text, images, and video available on the Internet. It should be capable of apprenticeship learning: having a conversation with a teacher, and not just asking “may I have a thousand images of a Corolla,” but rather being able to understand advice like “the Insight is similar to the Prius, but the Insight has a larger grille.” It should know that each model comes in a small range of possible colors, but that a car can be repainted, so there is a chance that it might see a car in a color that was not in the training set. (If it didn’t know that, it should be capable of learning it, or being told about it.)

All this requires a communication and representation language that humans and computers can share; we can’t expect a human analyst to directly modify a model with millions of weights. Probabilistic models (including probabilistic programming languages) give humans some ability to describe what we know, but these models are not yet well integrated with other learning mechanisms.

The work of Bengio and LeCun (2007) is one step towards this integration. Recently Yann LeCun has suggested that the term “deep learning” should be replaced with the more general differentiable programming (Siskind and Pearlmutter, 2016; Li et al., 2018); this suggests that our general programming languages and our machine learning models could be merged together.

Differentiable programming

Right now, it is common to build a deep learning model that is differentiable, and thus can be trained to minimize loss, and retrained when circumstances change. But that deep learning model is only one part of a larger software system that takes in data, massages the data, feeds it to the model, and figures out what to do with the model’s output. All these other parts of the larger system were written by hand by a programmer, and thus are nondifferentiable, which means that when circumstances change, it is up to the programmer to recognize any problems and fix them by hand. With differentiable programming, the hope is that the entire system is subject to automated optimization.

The end goal is to be able to express what we know in whatever form is convenient to us: informal advice given in natural language, a strong mathematical law like `F = ma`, a statistical model accompanied by data, or a probabilistic program with unknown parameters that can be automatically optimized through gradient descent. Our computer models will learn from conversations with human experts as well as by using all the available data.

Yann LeCun, Geoffrey Hinton, and others have suggested that the current emphasis on supervised learning (and to a lesser extent reinforcement learning) is not sustainable—that computer models will have to rely on weakly supervised learning, in which some supervision is given with a small number of labeled examples and/or a small number of rewards, but most of the learning is unsupervised, because unannotated data are so much more plentiful.

LeCun uses the term predictive learning for an unsupervised learning system that can model the world and learn to predict aspects of future states of the world—not just predict labels for inputs that are independent and identically distributed with respect to past data, and not just predict a value function over states. He suggests that `GANs` (generative adversarial networks) can be used to learn to minimize the difference between predictions and reality.

Predictive learning

Geoffrey Hinton stated in 2017 that “My view is throw it all away and start again,” meaning that the overall idea of learning by adjusting parameters in a network is enduring, but the specifics of the architecture of the networks and the technique of back-propagation need to be rethought. Smolensky (1988) had a prescription for how to think about connectionist models; his thoughts remain relevant today.

### Resources
