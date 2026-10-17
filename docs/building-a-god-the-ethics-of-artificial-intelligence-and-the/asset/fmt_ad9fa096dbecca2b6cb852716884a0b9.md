
It is interesting to note that I. J. Good joined Marvin Minsky and worked with Stanley Kubrick during the filming of `2001: A Space Odyssey` just a few short years later. `Kubrick`, a fan of both `Good`’s and `Minsky`’s work, has been credited as one of the most thorough film directors in terms of researching the various aspects of aeronautics, computer systems, and AI. He also collaborated with co-screenwriter and science fiction author `Arthur C. Clarke` on the film. Perhaps this explains why he so effectively created the misaligned and haunting computer: `HAL 9000`. Just consider the chilling and misaligned conversation that takes place between `Dr. Dave Bowman`, the mission commander aboard `Discovery One`, and `HAL 9000`—the onboard computer:

> DAVE: Open the pod bay doors, Hal.

> 

> HAL: I’m sorry, Dave. I’m afraid I can’t do that.

> 

> DAVE: What’s the problem?

> 

> HAL: I think you know what the problem is just as well as I do.

> 

> DAVE: What are you talking about, Hal?

> 

> HAL: This mission is too important for me to allow you to jeopardize it.

> 

> DAVE: I don’t know what you’re talking about, Hal.

> 

> HAL: I know that you and Frank were planning to disconnect me, and I’m afraid that’s something I can’t allow to happen.

> 

> DAVE: Where the hell’d you get that idea, Hal?

> 

> HAL: Although you took very thorough precautions in the pod against my hearing you, I could see your lips move.

> 

> DAVE: All right, Hal. I’ll go in through the emergency air lock.

> 

> HAL: Without your space helmet, Dave, you’re going to find that rather difficult.

> 

> DAVE: Hal, I won’t argue with you anymore. Open the doors!

> 

> HAL: Dave…. This conversation can serve no purpose anymore. Goodbye.[^(56)](#Notes.xhtml#ch01.ftn.0067)

The horrific realization that humans have gradually lost control over an AI entity was immortalized in this scene. But Dave had time to react to `HAL`’s misalignment with human values. We may not be so fortunate.

By 1970, Good was explicitly stating his concerns about AI risks, hoping that the matter would be widely discussed in the following decade; but unfortunately, this did not happen. As you can see in [figure 1.2](#Chapter01.xhtml#fig1_2), there have been a number of so-called seasons of AI that represent when more and less time was being given to the potential for hope, growth, and concern in the emerging technologies.

![fig_33_1.jpg](Images/chpt_fig_002.jpg)

Figure 1.2. The seasons of AI. `*Created for the author. All rights to the author.*`

#### *Prolog*

In the 1960s, artificial intelligence was making rapid progress, supported generously by the U.S. government, especially the Department of Defense. However, advancements slowed in the mid-1970s and almost came to a halt in the United States when Congress cut off funding in 1974, which led to the first AI winter. From 1974 to 1980, many of the communities around the world stagnated with AI development. But during this period, there was a focus on expert systems, and knowledge-based AI used predefined rules and knowledge to solve complex problems in specific domains. For example, `Prolog`, a logic programming computer language, was developed in Marseille, France, in 1972 by `Alain Colmerauer` and `Philippe Roussel` as an alternative to LISP and was immediately associated with artificial intelligence and computational linguistics.

> Prolog was one of the first logic programming languages and remains the most popular such language today, with several free and commercial implementations available. The language has been used for theorem proving, expert systems, term rewriting, type systems, and automated planning, as well as its original intended field of use, natural language processing… \[it\]… is well-suited for specific tasks that benefit from rule-based logical queries such as searching databases, voice control systems, and filling templates.[^(57)](#Notes.xhtml#ch01.ftn.0068)

Prolog was an attempt to make a programming language that enables the expression of logic instead of carefully specified instructions on the computer.

> The execution of a Prolog program is equivalent to searching the tree of possibilities and determining the objects which satisfy the given rules. This is equivalent to proof by proposition. Prolog has an excellent backtrack mechanism, so when exploring the tree it can always return to another branch if the present branch does not contain the answer. This approach is equivalent to depth first search which is known as an efficient algorithm for traversing trees with a large number of nodes. Sometimes there can be several answers which are true in a given circumstance. This is because the program does not terminate as soon as the first answer is found, but keeps going until the entire tree of possibilities has been checked. Prolog is a conversational language, meaning the user and the computer have a “conversation.” Firstly, the user specifies the objects and the relationships that exist between these objects. Prolog can then answer the questions about this set of data.[^(58)](#Notes.xhtml#ch01.ftn.0069)

Aside from the development of new programs and computer languages assisting AI, expert systems were being created as well.

#### *MYCIN*

`MYCIN`, a medical expert system developed in 1974 at Stanford University, demonstrated the potential of AI in assisting human experts in diagnosis and decision-making, marking a significant step in the application of AI to real-world problem-solving:

> `MYCIN` was an early backward chaining expert system that used artificial intelligence to identify bacteria causing severe infections, such as bacteremia and meningitis, and to recommend antibiotics, with the dosage adjusted for patient’s body weight—the name derived from the antibiotics themselves, as many antibiotics have the suffix “-mycin.” The `MYCIN` system was also used for the diagnosis of blood clotting diseases. `MYCIN` was developed over five or six years in the early 1970s at Stanford University. It was written in LISP as the doctoral dissertation of `Edward Shortliffe` under the direction of `Bruce G. Buchanan`, `Stanley N. Cohen` and others.[^(59)](#Notes.xhtml#ch01.ftn.0070)

In his short paper on the program, `Edward Shortliffe` describes the program with a considerable nod to the great minds in AI of the past and with great hope for the future:

> `MYCIN` has also demonstrated that, if AI researchers are willing to accept the current limitations of the field, and to select real-world goals that are compatible with those limitations, a useful system can be developed using techniques for representation and control that would not have been available if it were not for prior work in artificial intelligence. This is perhaps the program’s principal lesson for AI.[^(60)](#Notes.xhtml#ch01.ftn.0071)

The 1980s saw increased interest in rule-based expert systems, but the early part of this decade was still quite chilly from an “AI winter,” due largely to a phase of reduced funding and enthusiasm because of unmet expectations. The rediscovery of neural networks and the development of backpropagation as a learning algorithm in the mid-1980s created a trend out of the winter and into the next AI summer as it laid the groundwork for the resurgence of interest in artificial neural networks.

#### *Neural Networks*

In 1986, `David Rumelhart`, `Geoffrey Hinton`, and `Ronald Williams` introduced the concept of the “restricted Boltzmann machine” (`RBM`).

> \[A\] restricted Boltzmann machine is an algorithm useful for dimensionality reduction, classification, regression, collaborative filtering, feature learning and topic modeling…. `RBM`s are shallow, two-layer neural nets that constitute the building blocks of deep-belief networks. The first layer of the `RBM` is called the visible, or input, layer, and the second is the hidden layer.[^(61)](#Notes.xhtml#ch01.ftn.0072)
