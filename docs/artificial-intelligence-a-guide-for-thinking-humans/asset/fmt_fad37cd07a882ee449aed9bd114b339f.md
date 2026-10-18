
> Sentences 1 and 2 differ by only one word (`feared` / `advocated`), but that single word determines the answer to the question. In sentence 1 the pronoun `they` refers to the city council, and in sentence 2 `they` refers to the demonstrators. How do we humans know this? We rely on our background knowledge about how society works: we know that demonstrators are the ones with a grievance and that they sometimes advocate or instigate violence at a protest.

> Here are a few more examples:

> > SENTENCE 1: “Joe’s uncle can still beat him at tennis, even though he is 30 years older.”
> > QUESTION: Who is older?
> > A. Joe B. Joe’s uncle
> > SENTENCE 2: “Joe’s uncle can still beat him at tennis, even though he is 30 years younger.”
> > QUESTION: Who is younger?
> > A. Joe B. Joe’s uncle
> > SENTENCE 1: “I poured water from the bottle into the cup until it was full.”
> > QUESTION: What was full?
> > A. The bottle B. The cup
> > SENTENCE 2: “I poured water from the bottle into the cup until it was empty.”
> > QUESTION: What was empty?
> > A. The bottle B. The cup
> > SENTENCE 1: “The table won’t fit through the doorway because it is too wide.”
> > QUESTION: What is too wide?
> > A. The table B. The doorway
> > SENTENCE 2: “The table won’t fit through the doorway because it is too narrow.”
> > QUESTION: What is too narrow?
> > A. The table B. The doorway

> I’m sure you get the idea: The two sentences in each pair are identical except for one word, but that word changes which thing or person is referenced by pronouns such as `they`, `he`, or `it`. To answer the questions correctly, a machine needs to be able not only to `process` sentences but also to `understand` them, at least to a point. In general, understanding these sentences requires what we might call commonsense knowledge. For example, an uncle is usually older than his nephew; pouring water from one container to another means that the first container will become empty while the other one becomes full; and if something won’t fit through a space, it is because the thing is too wide rather than too narrow.

> These miniature language-understanding tests are called Winograd schemas, named for the pioneering NLP researcher Terry Winograd, who first came up with the idea.

> Several natural-language processing research groups have experimented with different methods for answering Winograd schema questions. At the time I write this, the program reporting the best performance had about 61 percent accuracy on a set of about 250 Winograd schemas.

> “I poured water from the bottle into the cup until the bottle was full.”
> “I poured water from the bottle into the cup until the cup was full.”

> Google conveniently reports the number of “results” (matches it finds on the web) for each of these sentences. When I did this search, the first sentence yielded about 97 million results, whereas the second yielded about 109 million results. The wisdom of the web correctly tells us that the second sentence is more likely to be correct. This is a nice trick if your goal is to do better than random guessing, and I wouldn’t be surprised if machine accuracy keeps inching its way up on this particular set of Winograd schemas. However, I doubt that such purely statistical methods will approach a human level of performance anytime soon on larger sets of Winograd schemas. Maybe that’s a good thing. As Oren Etzioni, director of the Allen Institute for AI, quipped, “When AI can’t determine what ‘it’ refers to in a sentence, it’s hard to believe that it will take over the world.”

## Adversarial Attacks on Natural-Language Processing Systems

> NLP systems face another obstacle to world domination: similar to computer-vision programs, NLP systems can be vulnerable to “adversarial examples.” In chapter 6, I described one method in which an adversary (here, a human trying to fool an AI system) can make a small change to the pixels of a photo of, say, a school bus. The new photo looks, to humans, exactly like the original, but a trained convolutional neural network classifies the modified photo as “ostrich” (or some other category targeted by the adversary). I also described a method by which an adversary can produce an image that looks to humans like random noise but that a trained neural network classifies as, say, “cheetah,” with close to 100 percent confidence.

> Not surprisingly, these same methods can be used to fool systems that do automated image captioning. One group of researchers showed how an adversary could make specific pixel changes to a given image, imperceptible to humans, that would cause an automated system to output an incorrect caption containing a set of words specified by the adversary. ![FIGURE 43: An example of an adversarial attack on an image-captioning system. At left are the original image and the computer-generated caption. At right is the modified image (which to humans looks identical to the original), along with the resulting caption. The original image was specifically modified by the authors to result in a caption that contains the words `dog`, `cat`, and `frisbee`.](images/Figure43.jpg)

> FIGURE 43: An example of an adversarial attack on an image-captioning system. At left are the original image and the computer-generated caption. At right is the modified image (which to humans looks identical to the original), along with the resulting caption. The original image was specifically modified by the authors to result in a caption that contains the words `dog`, `cat`, and `frisbee`.

> [Figure 43](#chapter13.xhtml#fig43) gives an example of such an adversarial attack. Given the original image (left), the system produced the caption “A cake that is sitting on a table.” The authors produced a slightly modified image, created purposely to result in a caption with the words `dog`, `cat`, and `frisbee`. While the resulting image (right) looks unchanged to humans, the captioning system’s output was “A dog and a cat are playing with a frisbee.” Obviously, the system is not perceiving the photo in the same way that we humans are.

> Perhaps more surprising, several research groups have shown that analogous adversarial examples can be constructed to fool state-of-the-art speech-recognition systems. As one example, a group from the University of California at Berkeley designed a method by which an adversary could take `any` relatively short sound wave—speech, music, random noise, or any other sound—and perturb it in such a way that it sounds unchanged to humans but that a targeted deep neural network will transcribe as a very different phrase that was chosen by the adversary.

> NLP researchers have also demonstrated the possibility of adversarial attacks on the kinds of sentiment-classification and question-answering systems that I described earlier. These attacks typically change a few words or add a sentence to a text. The “adversarial” change does not affect the meaning of the text for a human reader, but it causes the system to give an incorrect answer. For example, NLP researchers at Stanford showed that certain simple sentences added to paragraphs in the SQuAD question-answering data set will cause even the best-performing systems to output wrong answers, resulting in a large drop in their overall performance. Here’s an example from the SQuAD test item I gave above, but with an irrelevant sentence added (italicized here for clarity). This addition causes a deep-learning question-answering system to give an incorrect answer:
