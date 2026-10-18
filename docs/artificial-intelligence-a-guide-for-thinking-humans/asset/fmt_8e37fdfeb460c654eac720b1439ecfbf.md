
> Let’s dig into this a bit. How *general* is this AI, really? How applicable to the real world, beyond games? To what extent are these systems actually learning “on their own”? And what is it, exactly, that they learn?

## Generality and “Transfer Learning”

When I was searching online for articles about AlphaGo, the web offered me this catchy headline: “DeepMind’s AlphaGo Mastered Chess in Its Spare Time.”^()

The same is true for the various Atari game-playing programs: each learns its own network weights from scratch. It’s as if you learned to play *Pong*, but then in order to learn to play *Breakout*, you’d have to completely forget everything you learned about playing *Pong* and start from square one.

A hopeful phrase in the machine-learning community is “transfer learning,” which refers to the ability of a program to *transfer* what it has learned about one task to help it perform a different, related task. For humans, transfer learning is automatic. After I learned to play Ping-Pong, I was able to transfer some of those skills to help me in learning tennis and badminton. Knowing how to play checkers helped me in learning how to play chess. When I was a toddler, it took me a while to learn how to twist the doorknob in my room, but once I had mastered that skill, my abilities quickly generalized to most any kind of doorknob.

Humans exhibit this kind of transfer from one task to another seemingly effortlessly; our ability to generalize what we learn is a core part of what it means for us to *think*. Thus, in human-speak, we might say that another term for transfer learning is, well, *learning*.

In stark contrast with humans, most “learning” in current-day AI is not transferable between related tasks. In this regard, the field is still far from what Hassabis calls “general AI.” While the topic of transfer learning is one of the most active areas of research for machine-learning practitioners, progress on this front is still nascent.^()

## “Without Human Examples or Guidance”

Unlike supervised learning, reinforcement learning holds the promise of programs that can truly learn on their own, simply by performing actions in their “environment” and observing the outcome. DeepMind’s most important claim about its results, especially on AlphaGo, is that the work has delivered on that promise: “Our results comprehensively demonstrate that a pure reinforcement learning approach is fully feasible, even in the most challenging of domains: it is possible to train to superhuman level, without human examples or guidance, given no knowledge of the domain beyond basic rules.”^()

We have the claim. Now let’s look at the caveats. AlphaGo (or more precisely, the AlphaGo Zero version) indeed didn’t use any human examples in its learning, but human “guidance” is another story. A few aspects of human guidance that were critical to its success include the specific architecture of its convolutional neural network, the use of Monte Carlo tree search, and the setting of the many hyperparameters that both of these entail. As the psychologist and AI researcher Gary Marcus has pointed out, none of these crucial aspects of AlphaGo were “learned from the data, by pure reinforcement learning. Rather, \[they were\] built in innately … by DeepMind’s programmers.”^()

## The Most Challenging of Domains

One additional aspect of DeepMind’s statement needs to be explored: “even in the most challenging of domains.” How can we assess how challenging a domain is for AI? As we’ve seen, many things we humans consider quite easy (for example, describing the contents of a photo) are extremely challenging for computers. Conversely, many things we humans would find terrifically challenging (for example, correctly multiplying two fifty-digit numbers), computers can do in a split second with a one-line program.

One way to assess the challenge of a domain for computers is to see how well very simple algorithms perform on it. In 2018, a group of researchers at Uber AI Labs found that some relatively simple algorithms nearly matched (and sometimes outperformed) DeepMind’s deep Q-learning method on several Atari video games. The most surprising good performer was “random search”: instead of training a Deep Q-Network by reinforcement learning over many episodes, one can simply try out many different convolutional neural networks with *randomly* chosen weights.^()

You’d think that a network with random weights would perform abominably on an Atari video game. Indeed, most such networks are terrible players. But the Uber researchers kept trying new random-weight networks, and eventually (in less time than it took to train a Deep Q-Network) they found networks that performed nearly as well as or even better than networks trained by deep Q-learning on five out of the thirteen games they tested. Another relatively simple algorithm, a so-called genetic algorithm,^()

I haven’t heard of anyone trying a similar random search for network weights for Go. I’d be very surprised if that worked at all. Given the long history of attempts to build computer Go players, I’m convinced that Go counts as a genuinely challenging domain for AI. However, as Gary Marcus pointed out, there are many games humans play that are even more challenging for AI than Go. One striking example Marcus gives is charades,^()

## What Did These Systems Learn?

Like other applications of deep learning, it’s hard to interpret what the neural networks used in these game-playing systems have actually learned. In reading the sections above, you might have noticed some subtle anthropomorphism creeping into my descriptions: for example, I said, “DeepMind’s *Breakout* player discovered the strategy of tunneling through the bricks.”

It’s dangerously easy, for me as much as anyone, to slip into this kind of language when talking about the behavior of AI systems. However, our language often carries unconscious assumptions that may not hold for these programs. Did DeepMind’s *Breakout* player actually discover the concept of *tunneling*? Gary Marcus reminds us that we need to be careful here:

> The system has learned no such thing; it doesn’t really understand what a tunnel, or what a wall is; it has just learned specific contingencies for particular scenarios. Transfer tests—in which the deep reinforcement learning system is confronted with scenarios that differ in minor ways from the ones on which the system was trained—show that deep reinforcement learning’s solutions are often extremely superficial.^()

> Marcus is referring to a few studies that tried to probe how well deep Q-learning systems can transfer what they learned, even to very small variations of the same game. For example, one group of researchers studied a system similar to DeepMind’s *Breakout* player. They found that once the player is trained to “superhuman” level, if the paddle’s position on the screen is shifted up by a few pixels, the system’s performance plummets.^()

> These are just two examples of deep Q-learning’s inability to generalize, which contrasts strikingly with human intelligence. I don’t know of any study that probed the concept of tunneling in DeepMind’s *Breakout* player, but I’d guess that the system couldn’t generalize to, say, tunneling *down* or *sideways*, without considerable retraining. As Marcus notes, while *we humans* attribute to the program a certain understanding of what we consider basic concepts (for example, *wall*, *ceiling*, *paddle*, *ball*, *tunneling*), the program actually has no such concepts:
