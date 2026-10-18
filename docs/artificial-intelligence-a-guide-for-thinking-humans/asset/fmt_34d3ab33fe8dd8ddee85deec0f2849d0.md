
> If you yourself happened to use any kind of speech-recognition technology both before and after 2012, you will have also noticed a very sharp improvement. Speech recognition, which before 2012 ranged from horribly frustrating to moderately useful, suddenly became very nearly perfect in some circumstances. I am now able to dictate all of my texts and emails on my phone’s speech-recognition app; just a few moments ago, I read the “Restaurant” story to my phone, using my normal speaking speed, and it correctly transcribed every word.

> What’s stunning to me is that speech-recognition systems are accomplishing all this without any understanding of the *meaning* of the speech they are transcribing. While the speech-recognition system on my phone can transcribe every word of my “Restaurant” story, I guarantee you that it doesn’t understand a thing about it, or about anything else. Many people in AI, myself included, had previously believed that AI speech recognition would never reach such a high level of performance without actually understanding language. But we’ve been proven wrong.

> This being said, automated speech recognition is still not at “human level,” contrary to some reports in the media. Background noise can significantly hurt the accuracy of these systems; they’re much less effective inside a moving car than in a quiet room. In addition, these systems are occasionally thrown off by unusual words or phrases in a way that highlights their lack of understanding of the speech they are transcribing. For example, I said, “Mousse is my favorite dessert,” but my (Android) phone transcribed it as “Moose is my favorite dessert.” I said, “The bareheaded man needed a hat,” but my phone transcribed it as “The bear headed man needed a hat.” It’s not hard to find sentences that will confuse a speech-recognition system. However, for everyday speech in a quiet environment, I’d guess that the accuracy of such systems—measured by correct words—is probably around 90 to 95 percent of humans’ accuracy.^()

> There’s a famous rule of thumb in any complex engineering project: the first 90 percent of the project takes 10 percent of the time and the last 10 percent takes 90 percent of the time. I think that some version of this rule applies in many AI domains (hello, self-driving cars!) and will end up being true in speech recognition as well. The last 10 percent includes dealing not only with noise, unfamiliar accents, and unknown words but also with the fact that the ambiguity and context sensitivity of language can impinge on interpreting speech. What’s needed to power through that last stubborn 10 percent? More data? More network layers? Or, dare I ask, will that last 10 percent require an actual *understanding* of what the speaker is saying? I’m leaning toward this last one, but I’ve been wrong before.

> Speech-recognition systems are quite complicated; several different kinds of processing are needed to go from sound waves to sentences. Current state-of-the-art speech-recognition systems integrate several different components, including multiple deep neural networks.^()

> ## Classifying Sentiment

> As a first example, let’s look at the area called sentiment classification. Consider these short reviews of the movie *Indiana Jones and the Temple of Doom*:^()

> “The plot is heavy and the sense of humor is largely missing.”

> “A little too dark for my taste.”

> “It felt as if the producers tried to make it as disturbing and horrific as they possibly could.”

> “Temple of Doom’s character development and humor is intensely subpar.”

> “The tone is kind of weird and it has a lot of humor that wasn’t working for me.”

> “Without any of the charm or wit that is embodied in the others in this series.”

> In each case, did the reviewer like the movie?

> There is big money in using machines to answer such a question. An AI system that could accurately classify a sentence (or longer passage) as to its *sentiment*—positive, negative, or some other degree of opinion—would be solid gold to companies that want to analyze customers’ comments about their products, find new potential customers, automate product recommendations (“people who liked X also like Y”), or selectively target their online advertisements. Data on what movies, books, or other merchandise a person likes or dislikes can be surprisingly (and perhaps scarily) useful in predicting that person’s future purchases. What’s more, such information may have predictive power about other aspects of a person’s life, such as likely voting patterns and responsiveness to certain types of news stories or political ads.^()

> Putting aside the ethics of these applications of sentiment analysis, let’s focus on *how* AI systems might be able to classify the sentiment of sentences like the ones above. While it’s quite easy for humans to see that these mini-reviews are all negative, getting a program to do this kind of classification in a general way is much harder than it might seem at first glance.

> Some early NLP systems looked for the presence of individual words or short sequences of words as indications of the sentiment of a text. For example, you might expect words such as *dark*, *weird*, *heavy*, *disturbing*, *horrific*, *lacking*, and *missing*, or sequences such as *wasn’t working*, *without any*, *a little too*, as indicating negative sentiment in movie reviews. In some cases this works, but in many cases such sequences can be found in positive reviews as well. Here are a few examples:

> “Despite the heavy subject matter, there’s enough humor to keep it from becoming too dark.”

> “There’s nothing here that is disturbing or horrific as some people have suggested.”

> “I was a little too young to see this terrific movie when it first came out.”

> “If you don’t see it, you’ll be missing out!”

> Looking at single words or short sequences in isolation is generally not sufficient to glean the overall sentiment; it’s necessary to capture the semantics of words in the context of the whole sentence.

> Soon after deep networks started to excel in computer vision and speech recognition, NLP practitioners experimented with applying them to sentiment analysis. As usual, the idea is to train the network on many human-labeled examples of sentences with both positive and negative sentiment and have the network itself learn useful *features* that allow it to output a classification confidence for “positive” or “negative” on a new sentence. But first, how can we get a neural network to process a sentence?

> ## Recurrent Neural Networks

> Processing a sentence or passage requires a different type of neural network from those I have described in previous chapters. Recall, for example, the convolutional neural network from chapter 4 that classified an image as “dog” or “cat.” There, the network’s inputs were the pixel intensities of a fixed-size image (larger or smaller images had to be scaled to the proper size). In contrast, sentences consist of *sequences* of words and do not have a fixed length. Thus, we need a way for a neural network to process variable-length sentences.
