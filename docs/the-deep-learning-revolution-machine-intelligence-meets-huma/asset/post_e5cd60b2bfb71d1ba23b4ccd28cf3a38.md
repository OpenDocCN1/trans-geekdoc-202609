
Taking courses at Princeton, I discovered that exciting progress was being made by neuroscientists, whose relatively young science was founded forty-five years ago. Before that, research on the brain was carried out in many disciplines: biology, psychology, anatomy, physiology, pharmacology, neurology, psychiatry, bioengineering, and many others. At the first meeting of the Society for Neuroscience in 1971, Vernon Mountcastle personally greeted everyone at the door.12 Today there are over 40,000 members of the society, and 30,000 show up at the annual meeting. I met this legendary neurophysiologist, who had discovered the cortical column and who had a formidable personality, at the Johns Hopkins University when I moved to the Department of Biophysics there for my first job in 1982.13 I would work closely with Mountcastle in planning the Mind/Brain Institute at Johns Hopkins, the first institute of its kind in the world, established in 1994.

There are many different levels of investigation in the brain (figure 4.4), and important discoveries have been made at each of them; integrating all that knowledge is a formidable problem. This is reminiscent of the Humpty Dumpty nursery rhyme:

> Humpty Dumpty sat on a wall,
> Humpty Dumpty had a great fall.
> All the king's horses and all the king's men
> Couldn't put Humpty together again.

Although neuroscientists are very good at taking the brain apart, putting the pieces together poses a more difficult problem, one that requires synthesis rather than reduction, which is what I wanted to do. But first I had to know what the parts are, and the brain has lots of parts.

In a graduate seminar taught by Charles Gross, a psychologist who studied the monkey visual system at Princeton, I was impressed with the progress that had been made by David Hubel and Torsten Wiesel at Harvard Medical School in recording from single neurons in the visual cortex. If physics wasn't the royal road to understanding how the brain works, maybe neuroscience would be. For their pioneering work in the primary visual cortex, Hubel and Wiesel would receive a Nobel Prize in Physiology or Medicine in 1981. (Their discoveries, discussed in chapter 5, are the basis for deep learning, the subject of chapter 9.)

## What I learned at Woods Hole

After finishing my doctorate in physics at Princeton in 1978, I attended a ten-week, in-depth summer course on experimental neurobiology at the

## Levels of Investigation

![](img/dd452eef0506ea820c436fef2f776436_68_0.png)

Figure 4.4
Levels of investigation in the brain. (Left) The spatial scale ranges from the molecular level at the bottom to the entire central nervous systems (CNS) at the top. Much is known about each of these levels, but the least understood is the network level with its small groups of highly interconnected neurons—the level modeled by artificial neural networks. (Right) Icons for synapse (bottom), simple cell in visual cortex (middle), and hierarchy of cortical areas in the visual cortex (top). Adapted from P. S. Churchland, and T. J. Sejnowski, “Perspectives on Cognitive Neuroscience,” Science, 242 (1988): 741–745, figure 1.

Marine Biological Laboratory at Woods Hole. I arrived on the first day of the course in a casual blue sports coat and neatly pressed khaki pants, only to be taken aside by Story Landis, one of the course instructors, who bought me my first pair of jeans. Story was on the faculty in the Harvard Department of Neurobiology at the time and went on to become the director of the National Institute for Neurological Disorders and Stroke at the National Institutes of Health. She still reminds me of this incident.

After the summer course, I stayed on for a few weeks in September to wrap up a project I had started. Sharks and rays (which include skates) are able to sense very weak electrical fields; indeed, they can detect the signal from a 1.5-volt battery clear across the Atlantic Ocean. With this sixth sense, skates can navigate by the weak electrical signals from their motion through the earth’s magnetic field, which generates microvolt signals in their electroreceptors. My project yielded spectacular electron microscope images of the skate electroreceptor.14

I was taking photos in the basement of Loeb Hall at Woods Hole when I received an unexpected call from Stephen Kuffler, who founded the Neurobiology Department at Harvard Medical School. Kuffler is a legend in neuroscience, and getting an offer to work with him as a postdoctoral fellow in his lab was life changing. I moved to Boston after finishing a brief postdoctoral fellowship with Alan Gelperin on mapping metabolic activity in the pedal ganglion of the garden slug Limax maximus.15 I will never be able to eat a snail again without a synapse in the bullfrog sympathetic ganglion (figure 4.5) that was 60,000 times slower than the fast millisecond excitatory response at another synapse on the same neuron.17 These ganglia contain the neurons that form the output of the bullfrog’s autonomic nervous system, which regulates glands and internal organs. After stimulating the nerve to the synapse, I could walk to the coffeepot and back before the synaptic input to the neuron had reached a peak, which it would in around 1 minute, taking 10 minutes to recover. Synapses are the fundamental computational elements in the brain, and the diversity of synapse types is telling. This experience taught me that

![](img/dd452eef0506ea820c436fef2f776436_70_0.png)

Figure 4.5
Bullfrog sympathetic ganglion cell. As neurons, these cells receive inputs from the spinal cord and innervate glands in the skin of bullfrogs. They are large and their electrical signals are easy to record with a microelectrode (bottom). They have no dendrites and can be electrically stimulated by a nerve (top, background) or with chemicals (top, pair of micropipettes). Stimulating the nerve elicits three different synaptic signals: a fast millisecond excitatory response, similar to that at the neuromuscular junction; a slower excitatory response that peaks in 10 seconds and lasts 1 minute; and a late slow excitatory response that peaks in 1 minute and lasts 10 minutes. This illustrates the broad range of time scales that are present in even the simplest neurons. From S. W. Kuffler, and T. J. Sejnowski, “Peptidergic and Muscarinic Excitation at Amphibian Sympathetic Synapses,” Journal of Physiology 341 (1983): 257–278, plate I.

complexity might not be the royal road to understanding brain function. To understand the brain, I had to understand how, through evolution, nature had solved a large collection of problems long ago and passed those solutions on from species to species up the evolutionary ladder. We have ion channels in our brains that first evolved in bacteria billions of years ago.

## The Missing Link

But if physics was too simple and biology too complex, where should I look for guidance? Unlike forces in physics, brain circuits have a purpose, which is to solve computational problems, like seeing and moving around, in order to survive in the world. Even a perfect physical model of how a neuron worked wouldn't tell us what its purpose was. Neurons are in the business of processing signals that carry information, and computation was

![](img/dd452eef0506ea820c436fef2f776436_71_0.png)

Figure 4.6 Terry Sejnowski and Geoffrey Hinton discussing network models of vision in Boston in 1980. This was one year after Geoffrey and I met at the Parallel Models of Associative Memory workshop in La Jolla and one year before I started my lab at Johns Hopkins in Baltimore and Geoffrey started his research group at Carnegie Mellon in Pittsburgh. Courtesy of Geoffrey Hinton.

the missing link in trying to understand nature. I have over the last forty years been pursuing this goal, pioneering a new field called “computational neuroscience.”

After his stint as a postdoctoral fellow at UCSD, Geoffrey Hinton returned to England, where he had a research position with the Applied Psychology Unit of the Medical Research Council (MRC) at Cambridge. One day in 1981, he received a call at 2:00 a.m. from someone who introduced himself as Charles Smith, president of the System Development Foundation in Palo Alto, California.18 Smith said that his foundation wanted to fund potentially promising but risky research that was unlikely to succeed and Geoffrey had been highly recommended to him. Geoffrey wasn’t sure that this was for real. Good friend that he is, Geoffrey mentioned my research to Smith, telling him it was even more unlikely to succeed than his.

The foundation was indeed real and provided us with our first grants, which greatly speeded up our research. We could now afford to buy faster computers and to pay the students working with us. Geoffrey replaced his Apple II with a fancy Lisp machine19 when he moved to Carnegie Mellon in Pittsburgh; I briefly had more computer power than the entire Computer Science Department when I moved to Johns Hopkins in Baltimore.20 I was also able to buy the first modem that linked Hopkins to the ARPANET, a precursor to the Internet, so that Geoffrey and I could e-mail each other. We could not have asked for a better start to our careers as we set off in new directions (figure 4.6). I was fortunate to be funded over the years by the Office of Naval Research, which also supported Frank Rosenblatt and many other neural network researchers.
