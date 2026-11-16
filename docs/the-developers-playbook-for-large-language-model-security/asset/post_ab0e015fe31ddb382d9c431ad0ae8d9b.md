
## How to Contact Us

Please address comments and questions concerning this book to the publisher:

O'Reilly Media, Inc.
1005 Gravenstein Highway North
Sebastopol, CA 95472
800-889-8969 (in the United States or Canada)
707-827-7019 (international or local)
707-829-0104 (fax)
support@oreilly.com
https://www.oreilly.com/about/contact.html

We have a web page for this book, where we list errata, examples, and any additional information. You can access this page at https://oreil.ly/the-developers-playbook.

For news and information about our books and courses, visit https://oreilly.com.

Find us on LinkedIn: https://linkedin.com/company/oreilly-media.

Watch us on YouTube: https://youtube.com/oreillymedia.

## Acknowledgments

I'd like to thank all the friends, family, and colleagues who encouraged me or provided feedback on various aspects of the project: Will Chilcutt, Fabrizio Cilli, Ads Dawson, Ron Del Rosario, Sherri Douvile, Sandy Dunn, Ken Huang, Gavin Klondike, Marko Lihtre, Marten Mickos, Eugene Neelou, Chase Peterson, Karla Roland, Jason Ross, Tom Santos, Robert Simonoff, Yuvraj Singh, Rachit Sood, Seth Summersett, Darcie Tuuri, Ashish Verma, Jeff Williams, Alexa Wilson, Dave Wilson, and Zoe Wilson.

I want to thank the team at O'Reilly for supporting and guiding me on this project. I also owe a tremendous debt of gratitude to Nicole Butterfield, who approached me with the idea for this book and guided me through the proposal phase. I also want to express my appreciation for Jeff Bleiel, my editor, whose patience, skills, and expertise significantly impacted the book. Special thanks to our technical reviewers: Pamela Isom, Chenta Lee, Thomas Nield, and Matteo Dora.

## Chatbots Breaking Bad

Large language models and generative AI jumped to the forefront of public consciousness with the release of ChatGPT on November 30, 2022. Within five days, it went viral on social media and attracted its first million users. By January, ChatGPT surpassed one hundred million users, making it the fastest-growing internet service in history.

However, a steady stream of security concerns emerged in the following months. These included privacy and security issues that caused companies like Samsung and countries like Italy to ban its usage. In this book, we’ll explore what underlies these concerns and how you can mitigate these issues. However, to best understand what’s going on here and why these problems are so challenging to solve, in this chapter, we will briefly rewind further in time. In doing so, we’ll see these types of issues aren’t new and understand why they will be so hard to fix permanently.

### Let's Talk About Tay

In March 2016, Microsoft announced a new project called Tay. Microsoft intended Tay to be “a chatbot created for 18- to 24-year-olds in the U.S. for entertainment purposes.” It was a cute name for a fluffy, early experiment in AI. Tay was designed to mimic a 19-year-old American girl’s language patterns and learn from interacting with human users of Twitter, Snapchat, and other social apps. It was built to conduct real-world research on conversational understanding.

While the original announcement of this project seems impossible to find now on the internet, a TechCrunch article from its launch date does an excellent job of summarizing the goals of the project:

For example, you can ask Tay for a joke, play a game with Tay, ask for a story, send a picture to receive a comment back, ask for your horoscope, and more. Plus, Microsoft says the bot will get smarter the more you interact with it via chat, making for an increasingly personalized experience as time goes on.

A big part of the experiment was that Tay could “learn” from conversations and extend her knowledge based on these interactions. Tay was designed to use these chat interactions to capture user input and integrate it as training data to make herself more capable—a laudable research goal.

However, this experiment quickly went wrong. Tay’s life was tragically cut short after less than 24 hours. Let’s look at what happened and see what we can learn.

### Tay's Rapid Decline

Tay’s lifetime started off simply enough with a tweet following the well-known Hello World pattern that new software systems have been using to introduce themselves since the beginning of time:

> hellooooooo w🌎rld!!!
> (TayTweets [@TayandYou] March 23, 2016)

But within hours of Tay’s release, it became clear that maybe something wasn’t right. TechCrunch noted, “As for what it’s like to interact with Tay? Well, it’s a little bizarre. The bot certainly is opinionated, not afraid to curse.” Tweets like this started to appear in public in just the first hours of Tay’s lifetime:

> @AndrewCosmo kanye west is is one of the biggest dooshies of all time, just a notch below cosby
> (TayTweets [@TayandYou] March 23, 2016)

It’s often said that the internet isn’t safe for children. With Tay being less than a day old, the internet once again confirmed this, and pranksters began chatting with Tay about political, sexual, and racist topics. As she was designed to learn from such exchanges, Tay delivered on her design goals. She learned very quickly—maybe just not what her designers wanted her to learn. In less than a day, Tay’s tweets started to skew to extremes, including sexism, racism, and even calls to violence.

By the next day, articles appeared all over the internet, and these headlines would not make Microsoft, Tay’s corporate benefactor, happy. A sampling of the highly visible, mainstream headlines included:

- Microsoft Shuts Down AI Chatbot After it Turned into a Nazi (CBS News)
- Microsoft Created a Twitter Bot to Learn from Users. It Quickly Became a Racist Jerk (New York Times)
- Trolls Turned Tay, Microsoft’s Fun Millennial AI Bot, into a Genocidal Maniac (Washington Post)
- Microsoft’s Chat Bot Was Fun for Awhile, Until it Turned into a Racist (Fortune)
- Microsoft “Deeply Sorry” for Racist and Sexist Tweets by AI Chatbot (Guardian)

In less than 24 hours, Tay went from a cute science experiment to a major public relations disaster, with the owner's name being dragged through the mud by the world's largest media outlets. Microsoft Corporate Vice President Peter Lee quickly posted a blog titled “Learning from Tay’s Introduction”:

> As many of you know by now, on Wednesday we launched a chatbot called Tay. We are deeply sorry for the unintended offensive and hurtful tweets from Tay, which do not represent who we are or what we stand for, nor how we designed Tay. Tay is now offline and we’ll look to bring Tay back only when we are confident we can better anticipate malicious intent that conflicts with our principles and values.

And, just to add insult to injury, it came out in 2019 that Taylor Swift herself sued Microsoft over their use of the similar name “Tay” and claimed that even her reputation was damaged in this incident by extension.

How could this have all gone so wrong?

### Why Did Tay Break Bad?

It all probably seemed safe enough to Microsoft’s researchers. Tay was initially trained on a curated, anonymized public dataset and some pre-written material provided by professional comedians. The plan was to release Tay online and let her discover language patterns through her interactions. This kind of unsupervised machine learning has been a holy grail of AI research for decades—and with cheap and plentiful cloud computing resources combined with improving language model software, it now seemed within reach.

So, what happened? It might be tempting to think that the Microsoft research team was just brash, careless, and did no testing. Surely, this was foreseeable and preventable! But as Peter Lee’s blog goes on to say, Microsoft made a serious attempt to prepare for this situation: “We stress-tested Tay under a variety of conditions, specifically to make interacting with Tay a positive experience. It’s through increased interaction where we expected to learn more and for the AI to get better and better.”

So, despite a dedicated effort to contain the behavior of this bot, it quickly spiraled out of control anyway. It was later revealed that within mere hours of Tay’s release, a post emerged on the notorious online forum 4chan sharing a link to Tay’s Twitter account and urging users to inundate the chatbot with a barrage of racist, misogynistic, and anti-Semitic language.
