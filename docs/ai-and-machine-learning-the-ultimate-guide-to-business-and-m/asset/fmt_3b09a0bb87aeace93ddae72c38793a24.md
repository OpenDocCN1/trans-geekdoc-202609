
# 1.3.3. emergence and development

In 1956, a two-month seminar was held at Dartmouth College (one of the oldest universities in the United States), attended by ten leading researchers in the new direction:

- John McCarthy, Dartmouth College;
- Marvin Minsky, Harvard University;
- Claude Shannon, Bell Laboratories;
- Nathaniel Rochester, IBM;
- Arthur Samuel, IBM;
- Allen Newell, Carnegie Mellon University;
- Herbert Simon, Carnegie Mellon University;
- Trenchard Moore, Princeton University;
- Ray Solomonoff, Massachusetts Institute of Technology;
- Oliver Selfridge, Massachusetts Institute of Technology.

This seminar is considered the beginning of artificial intelligence as an independent direction, and the term `artificial intelligence` itself was proposed and adopted. No particular scientific results were produced by the Dartmouth seminar. Other important events took place there: artificial intelligence was recognized as a separate branch of science, the first impressive results were demonstrated (similar to the `Logic Theorist` program), and the scientific community was formed as a result of personal acquaintance of the leaders.

---

Although the title of Wiener's book makes no mention of thinking, the hated question "Can machines think?" [\[18\]](#part0005.xhtml#_ftn18) first appeared two years later in Turing's famous article. (In this article in particular, a constructive criterion for the presence of AI in a machine, the so-called Turing test, was formulated for the first time.)

Regarding this topic, opinions differed not only among external observers, journalists, and the general public, but also among the scientists themselves who had started working in the field of AI. Of course, the overall reaction from the working researchers was positive. The subtlety is that two similar questions can be asked:

1. Can a machine think like a human?
2. Can a machine think rationally?

The search for a constructive answer to the first question leads to the modeling of human thought, in which it is considered important not only to obtain an answer to an intellectual question, but also to analyze the means of obtaining an answer. This direction is called **neurocybernetics**.

The main method of neurocybernetics is the mathematical modeling of the human brain. As early as 1943, American scientists Warren McCulloch and Walter Pitts proposed a mathematical model for the operation of a human brain neuron—an **artificial neuron**—and methods for combining artificial neurons into a **neural network**.

This was followed by the pioneering work of Rosenblatt, Minsky, and other researchers. However, in the 70s, work in this direction slowed down somewhat due to the low quantitative capabilities of computers of that time. The fact is that in the human brain there are 10 to 14 billion ($10^9$) neurons working in parallel, and each has an average of about seven thousand ($10^3$) connections to other neurons. The number of artificial neurons in the first networks was measured in hundreds, at best thousands, but such large quantitative differences (millions of times) create a qualitative abyss—it is impossible to study large systems on small models. Note that the human brain's quantitative indicators in neural networks have not yet been reached [\[19\]](#part0005.xhtml#_ftn19), but the scale is gradually becoming appropriate.

In answering the second question, we come to the cybernetics of the **"black box"** when only entry and exit, stimulus and reaction are observed and the inner structure of the "thinking agent" remains hidden from observation. Unlike neurocybernetics, **"black box"** cybernetics does not care how the "thinking" device works. The main thing is that it reacts to the given input actions in the same way as the human brain, i.e., rationally.

Researchers in this field immediately switched from highly complex parallel nondeterministic neurocybernetic networks to relatively simple algorithmic models that manipulate abstract symbols rather than real-world signals. That's why we prefer the term **symbolic AI** (see fig. Error! Text of the specified style is missing in the document. .10).

The most notable pioneering work in this direction was the `Logic Theorist` program developed by A. Newell, G. Simon, and J. Shaw in 1955–1956. Working in the field of automatic theorem proving, the program was able to automatically find the derivation for 38 of the 52 propositional calculus theorems given in Russell and Whitehead's seminal book *Principia Mathematica*. In addition, in one case a shorter proof was found compared to the original.

So many different and sometimes surprising opinions and assessments have been expressed in the literature about this undoubted achievement that we consider it permissible to give our conclusions on universal programs for automatic proving of theorems, and therefore on universal mental programs, using the example of the logic-theoretical program in general (see also paragraph 0).

1. **Automatically proven theorems contain no new mathematical insights:** in the case of the `Logic Theorist` program, these are simple technical theorems of propositional calculus. Their validity can easily be checked by creating truth tables. The only task is to find a formal derivation (sequence of formulas) in a given axiomatic system with given rules of inference. The search for a conclusion does not require any new ideas or methods but relies on fairly routine techniques. Among the derivations discussed, there are no derivations shorter than three applications of the inference rules, and no derivations longer than two dozen applications of the inference rules. The results of the `Logic Theorist` program have no practical meaning.

2. **The author's long-term observations on students studying propositional calculus,** who in the process of education are forced to seek and find similar conclusions, allow us to assert that the average person "off the street" without special training will not find any of the formal proofs found by the `Logic Theorist` program. A person "off the street" simply will not understand what to do, because obviously they have never done anything like this. In this art, then, the unprepared is inferior to the `Logic Theorist` program. At the same time, after three or four practice sessions with the teacher, diligent students can find any of these conclusions, as well as the conclusions that the program could not find. It should be noted that the conclusions found by the students may not be as elegant as those of Russell and Whitehead and may not be found very quickly. Still, it can be argued that a person who is able to pass the entrance exams to the university can also learn to look for formal inferences no worse than the `Logic Theorist` program.

3. **From a qualitative point of view, the results of the `Logic Theorist` program have not improved significantly over the past half century.** The point is that the problem of automatically searching for a derivation in propositional calculus is exhaustive in character (see Section 0). Modern computers are millions and billions of times more powerful than the computer used by Shaw, but modern universal inference search programs can only draw tens, at most hundreds of times more complex conclusions, so on a qualitative level the first two remarks in this list remain valid even today and apply not only to the `Logic Theorist` program but to any modern program that claims to automatically prove any theorem in a sufficiently rich calculus.
