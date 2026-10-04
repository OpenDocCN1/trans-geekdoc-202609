
Saying “a network is made up of components” is like saying “a menagerie of hand-made glass animals is made up of…glass”—it is not very useful. More specifically, what are the components of a network? In the network world, there are

• Hardware devices that process and forward traffic, such as routers, switches, and stateful packet filters

• The environmentals, such as the power and cooling

• The cabling, interfaces, and other hardware

• The software running on these devices (the operating system)

• The software applications providing the information needed to forward packets; the control plane

• The specifications to which the network was designed and needs to operate in order to fulfill *business requirements*

• The requirements placed on the network by the applications the network is supporting

A broader, and simpler, set of terms might be: requirements + network software + protocols + equipment. Again, this might be a little obvious, but it is easy to forget the entire picture at 2 a.m. when the fires are burning hot, and you are trying to put them out.

How well can you know each of these four systems? Can you know them in fine detail, down to the last packet transmitted and the last bit in each packet? Can you know the flow of every packet through the network, and every piece of information any particular application pushes into a packet, or the complete set of ever-changing business requirements?

Obviously, the answer to these questions is no.

As these four systems within a network interact (remember interaction surfaces from the first chapter?), they create a larger system that suffers from a combinatorial explosion. [Figure 24-1](#ch24.xhtml#ch24fig01) illustrates.

![Image](graphics/24fig01.jpg)

**Figure 24-1** *Combinatorial Explosion of Systems in a Network*

There are far too many combinations, and far too many possible states, for any one person to know all of them. How can you reduce the amount of information so you can reasonably understand the state of an entire system, and hence be able to troubleshoot it? By building abstract models of the system’s components, the interaction points between those components, and, ultimately, of the system itself.

**This is the first skill of effective troubleshooting: build a set of models describing the system.**

All models will necessarily be *incomplete;* a model can represent only some aspects of an entire system or subsystem. Thus, models are a two-edged sword: they present a more readily understandable version of a system, but they also present a necessarily incomplete version of a system.

### Models and Troubleshooting

There is no single way, nor a single set of tools, you can use to build an effective model. This section will consider some common kinds of models—*how* models and *what* models—and discuss how to build them. The importance of accurate models and the ability to use models in the troubleshooting process effectively are also considered here.

**Note**

This has some interesting implications, of course. For instance, when a system is a “black box,” which means you are not supposed to know how the system works, your ability to troubleshoot the system itself is nonexistent, and your ability to troubleshoot any larger system of which the black box is a component is severely hampered.

#### Build *How* Models

*How* models are built using problem/solution sets. This entire book, in fact, is an exercise in building *how* models, using a three-step process:

1\. Determine the problem that needs to be solved.

2\. Investigate the range of possible solutions for the particular problem.

3\. Understand how this particular implementation uses a particular solution to solve a particular problem.

A potential fourth step beyond these three is integrating many solutions together into a complete system, considering the interaction between the solutions (such as where one solution reduces or increases the effectiveness of some other solution, etc.).

How models, of course, do not answer only one sort of question; for instance, when considering *how* Border Gateway Protocol (BGP) peers are formed:

1\. How does BGP manage flow control, error control/correction, and data marshaling between two BGP speakers?

2\. How does BGP manage the peering state between two BGP speakers?

3\. How does an operator configure BGP to properly form peering relationships between two BGP speakers?

Each of these is a separate kind of *how* question. Where many engineers go wrong in building a solid foundation for troubleshooting is knowing the answers to the second and third questions, while never spending time on the first. Engineering tends to end up being focused on the question *how do I get this done?* rather than *how does this work?*, specifically *why does this work this way?* The result is a “hunt and peck” sort of troubleshooting style—combining small snippets of past problems with lots of knowledge about how things should be configured to make them work. This is generally a very inefficient way to not only design networks and protocols, but also to troubleshoot them.

You need to be able to build *how* models of all three types. There are several useful ways to build up your stock of *how* models, including

• Reading protocol theory and specifications, so you understand how and why a protocol operates (what problems are being solved and how they are being solved)

• Examining the designs of protocols and networks, and how they have performed in the real world

• Learning basic algorithms and heuristics, along with the problems they are designed to solve

Essentially, building *how* models is more about *theory* than *practice;* this is why engineers often skip learning *how* models—which prevents them from growing their engineering skills over the long term. *How* models are sometimes best expressed in a graphical format, such as Universal Modeling Language (UML) sketches, or flow charts.

#### Build *What* Models

*What* models are different from *how* models in describing the state of a particular network or application, or a common pattern found across many networks or applications. These kinds of models generally answer questions such as

• What is the normal path of this traffic flow (the signal path) through the system (such as a network, application, etc.)?

• What is the normal set of top talkers on this network?

• What is the normal distribution of load between these two paths in the network?

• What is the normal startup process between two BGP speakers?

The only real way to learn *what* is to observe and summarize many times over. For instance, observing the top talkers across a large number of networks, or even in a single network across a number of years, will give you a good sense of where to look for top talkers, and a good sense of when the top talkers in *this situation* do not make sense.

Manipulation in the observation process is important here, as well; [Figure 24-2](#ch24.xhtml#ch24fig02) illustrates.

![Image](graphics/24fig02.jpg)

**Figure 24-2** *Manipulation and Causation*

In [Figure 24-2](#ch24.xhtml#ch24fig02), some value (representing, perhaps, an event or a property of an object) is assigned a variable, `X`. The question causation answers is: *does `X` somehow cause `Y`?* To answer this question, a range of possible interventions, or rather actions that will potentially modify `X`, are considered. In order to show `X` causes `Y`, all other potential interventions, `Z[1]` through `Z[n]`, are held constant, while one potential intervention, `Z[i]`, is manipulated. Manipulability is useful in building *how* models by helping you understand the relationship between the different parts of a system; if you manipulate the impact of `X` on `Y` by changing `Z[i]`, then you can better understand the relationship between `X` and `Y`.
