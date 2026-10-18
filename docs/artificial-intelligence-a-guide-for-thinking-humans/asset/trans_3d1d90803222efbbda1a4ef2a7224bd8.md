

> 没有人知道那个成功的方法会是什么。的确，深度强化学习领域仍然相当年轻。本章中我描述的结果可以被视为原理证明：深度网络与 Q-learning 的结合在一些非常有趣（尽管狭窄）的领域效果出奇地好，尽管我的讨论指出了该领域的一些当前局限，但许多人正致力于将强化学习扩展到更广泛的应用。特别是 DeepMind 的游戏程序，在该领域点燃了巨大的新兴趣和热情；事实上，深度强化学习被 MIT 的 `Technology Review` 杂志评为 2017 年“10 大突破性技术”之一。在未来的岁月里，随着强化学习的成熟，我将热切期待一台能够自主学习装碗碟的机器人，也许它在空闲时还能踢足球和下围棋。

# Part IV

# Artificial Intelligence Meets Natural Language

# 11

# Words, and the Company They Keep

It’s time for a story.

# The Restaurant

> A man went into a restaurant and ordered a hamburger, cooked rare. When it arrived, it was burned to a crisp. The waitress stopped by the man’s table. “Is the burger okay?” she asked. “Oh, it’s just great,” the man said, pushing back his chair and storming out of the restaurant without paying. The waitress yelled after him, “Hey, what about the bill?” She shrugged her shoulders, muttering under her breath, “Why is he so bent out of shape?”^()

>

> Now let me ask you a question: Did the man eat the hamburger?

>

> I’m guessing that you’re quite confident of your answer, even though the story doesn’t directly address this question. It’s easy, at least for us as humans, to read between the lines. After all, understanding language—including the parts that are left `unsaid`—is a fundamental part of human intelligence. It’s no accident that Alan Turing framed his famous “imitation game” as a contest involving the generation and understanding of language.

>

> This part of the book deals with `natural-language processing`, which means “getting computers to deal with human language.” (In AI-speak, “natural” means “human.”) Natural-language processing (abbreviated NLP) includes topics such as speech recognition, web search, automated question answering, and machine translation. Similar to what we’ve seen in previous chapters, deep learning has been the driving force behind most of the recent advances in NLP. I’ll describe some of these advances, using the “Restaurant” story to illustrate a few of the major challenges machines face when it comes to using and understanding human language.

>

> ## The Subtlety of Language

>

> Suppose we want to create a program that can read a passage and answer questions about it. Question-answering systems are a central focus of current NLP research, because people want to use natural language to interact with computers (think about Siri, Alexa, Google Now, and other “virtual assistants”). However, in order to answer questions about a text such as the “Restaurant” story, a program would require sophisticated linguistic skills as well as substantial knowledge about the way the world works.

>

> Did the man eat the hamburger? To answer this confidently, a hypothetical program would need to know that hamburgers belong to the category “food,” and that foods can be `eaten`. The program should know that going into a restaurant and ordering a hamburger usually means that you plan to eat the hamburger. Moreover, in a restaurant, once your order has arrived, it is available to be eaten. A program would need to know that when a person orders a hamburger “cooked rare,” the person generally doesn’t want to eat it if it has been “burned to a crisp.” The program should recognize that when the man says, “Oh, it’s just great,” he is being sarcastic, and that “it” refers to the “burger,” which is another word for “hamburger.” The program would need to surmise that if you “storm” out of a restaurant without paying, it’s likely that you haven’t eaten your meal.

>

> It’s mind-boggling to think of all the background knowledge the program would need in order to give confident answers to basic questions about the story. Did the man leave the waitress a tip? The program would need to know about the custom of tipping in restaurants and its purpose of rewarding good service. Why did the waitress say, “What about the bill”? The program needs to figure out that by “bill,” the waitress is referring not to, say, the beak of a bird, or a banknote, or a written piece of legislation, but to the charge for the man’s meal. Did the waitress know that the man was angry? The program has to determine that in asking “Why is he so bent out of shape?” “he” refers to the man, and “bent out of shape” is an idiom that means “upset and angry.” Did the waitress know `why` the man left the restaurant? It would help if our program knew that the gesture “shrugging her shoulders” suggests that the waitress didn’t understand why he stormed out.

>

> Thinking about what our hypothetical program would need to know reminds me of trying to answer the endless questions my children would ask when they were very young. Once, when my son was four years old, I took him with me to go to the bank. He asked a simple question: “What’s a bank?” My answer prompted a seemingly endless cascade of “why” questions. “Why do people use money?” “Why do people want to have a lot of money?” “Why can’t people keep all their money at home?” “Why can’t I make my own money?” All good questions, but hard to answer without having to explain all sorts of things that lie beyond a four-year-old’s experience.

>

> The situation is much more extreme for machines. A child who hears the “Restaurant” story already has well-grounded concepts such as `person`, `table`, and `hamburger`. Children have basic common sense, knowing, for example, that when the man walks out of the restaurant, he is no longer `inside` the restaurant, but the tables and chairs are probably still there. Or when the hamburger “arrived,” someone brought it to the man’s table (it didn’t arrive on its own). Today’s machines lack the detailed, interrelated concepts and commonsense knowledge that even a four-year-old child brings to understanding language.

>

> It should come as no surprise, then, that using and understanding natural language are among AI’s most difficult challenges. Language is inherently ambiguous, is deeply dependent on context, and assumes a great deal of background knowledge common to the communicating parties. As with other areas of AI, the first several decades of NLP research focused on symbolic `rule-based` approaches—that is, programs that were given grammatical and other linguistic rules and applied these rules to input sentences. These approaches did not work very well; it seems to be impossible to capture the subtleties of language by applying a set of explicit rules. In the 1990s, rule-based NLP approaches were overshadowed by more successful `statistical` approaches, in which massive data sets were employed to train machine-learning algorithms. Most recently, this statistical data-driven approach has focused on deep learning. Can deep learning, along with big data, produce machines that can flexibly and reliably deal with human language?

>

> ## Speech Recognition and the Last 10 Percent

>

> Automated speech recognition—the task of transcribing spoken language into text in real time—was deep learning’s first major success in NLP, and I’d venture to say that it is AI’s most significant success to date in any domain. In 2012, at the same time that deep learning was revolutionizing computer vision, a landmark paper on speech recognition was published by research groups at the University of Toronto, Microsoft, Google, and IBM.^()

