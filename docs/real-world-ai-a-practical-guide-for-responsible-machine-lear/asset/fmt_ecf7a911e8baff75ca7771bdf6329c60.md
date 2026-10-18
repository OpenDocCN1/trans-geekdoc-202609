
Meanwhile, more and more industries had started to embrace AI and adopt machine learning solutions. As I watched people face new challenges to make AI work in the real world, I realized that I could make an impact by helping to accelerate the AI journey of businesses. This led me to join Appen as its Chief Technology Officer. Appen is the industry leader in the AI data field, and our mission is to create large volumes of high-quality training data faster, which solves the biggest challenge for AI practitioners—the lack of high-quality training data. We work with companies from all types of industries to help them deploy AI confidently. At Appen, our average pilot-to-production deployment rate for the past two years has been 67 percent—far better than the 20 percent general average. Building in AI responsibility and good data management from the beginning creates machine learning systems that are both more adaptable and more successful over the long-term.

# What You’ll Learn in This Book

AI represents a massive shift in technology, as revolutionary as electricity or the internet. Machine learning technology promises to reshape everything throughout the business world. Ten years ago, it was rare to find a restaurant that had a social media strategy; now, it’s hard to find one that doesn’t. Within a few years, it will be just as hard to find a company without an AI strategy. Companies that aren’t working toward developing an AI strategy today are likely to fare as well as companies that decided not to pursue a web strategy in 2002 or a mobile strategy in 2008. It’s absolutely required if you want to compete in the market.

We understand how overwhelming this can feel because we’ve been there. That’s why we wrote this book: to demystify how to think about AI and provide an action plan for how to get started. Drawing on extensive multi-industry research, interviews with dozens of machine learning practitioners in startups and big companies, and our own real-world experience, we will help you design an AI system that serves your business case while remaining flexible and adaptable to changing circumstances. We won’t teach you how to be a data scientist or select an AI model; you should hire experts to help with that. What we will do is help you understand what the best path to a successful strategy looks like and how to participate meaningfully as a business owner or decision-maker, setting you on a path for success.

This book will also provide line-of-business owners (like product managers) and team members on the more technical side (like engineers and data scientists) a starting place for a common language. We aim to bridge the gap between teams, providing business specialists and the C-level enough context to converse efficiently with technical implementers.

The path to responsible AI isn’t straightforward, but with the aid of the best practices you’ll learn in these pages, your chances of success are much higher. Using machine learning in your business to drive down costs and increase revenue doesn’t have to be an overwhelming prospect. On the contrary, it’s highly achievable. It’s also a great motivator for any organization—it’s interesting, fun, and produces big-impact outcomes. All it requires is a cross-functional team and an innovative spirit. You’ll see dozens of examples of how it’s been done well at companies around the world.

The key is to start small and make consistent progress. From there, success with AI is more within reach than you think.

* * *

[1](#Alyssa-Simpson-Rochwerger_Real-World-AI_PRODUCTION_v101-3.xhtml#footnote-000-backlink) Jeopardy!® is a registered trademark of Jeopardy Productions, Inc.

# Chapter 1

# 1\. The Basics of AI—and Where It Breaks Down

“Artificial intelligence is the science and engineering of making computers behave in ways that, until recently, we thought required human intelligence.”

—Andrew Moore, Former Dean of Computer Science at Carnegie Mellon University

In August 2019, both Apple® and Goldman Sachs® were searching for solutions to an unforeseen problem after the launch of a hotly anticipated new product: the Apple credit card.

The card, with its touted ultra-security and sleek aesthetic, immediately saw a flood of applications, and by November, Goldman Sachs reported in its regulatory filings that it had issued $10 billion in credit to Apple Card holders.[2](#Alyssa-Simpson-Rochwerger_Real-World-AI_PRODUCTION_v101-4.xhtml#footnote-012) But while early adoption by consumers was robust, a problem soon emerged: the Apple Card approval process was offering smaller lines of credit to women than to men. Basecamp Co-Founder David Heinemeier Hansson launched a series of tweets that went viral, claiming the Apple Card approved him for a credit limit twenty times higher than the one offered to his wife, even though they filed joint tax returns and his wife had a higher credit score. Apple Co-Founder Steve Wozniak shockingly tweeted back, “The same thing happened to [my wife and me]. I got 10x the credit limit. We have no separate bank or credit card accounts or any separate assets.”

At first, no one at Apple seemed able to explain how the approval algorithm worked in order to analyze the output it was producing. Goldman Sachs claimed there was no gender bias in the approval process, the algorithm had been checked by a third party before the card was launched, and gender wasn’t even an input on the application, so how could a gender bias affect the outcome?

Hansson countered, “Goldman and Apple are delegating credit assessment to a black box. It’s not gender-discrimination intent, but it is a gender-discrimination outcome.”

Wired wrote in a November 2019 breakdown of the situation:[3](#Alyssa-Simpson-Rochwerger_Real-World-AI_PRODUCTION_v101-4.xhtml#footnote-011)

“A gender-blind algorithm could end up biased against women as long as it’s drawing on any input or inputs that happen to correlate with gender. There’s ample research showing how such “proxies” can lead to unwanted biases in different algorithms…other variables, such as home address, can serve as a proxy for race. Similarly, where a person shops might conceivably overlap with information about their gender.”

In attempting to avoid bias by omitting gender as an input in the application, the Apple Card model builders accidentally set themselves up for the exact bias they were trying to avoid. If the input includes gender, the output can be tested to see if female and male inputs are treated differently by the model. However, without the critical “gender” input, the “gender-blind” model becomes just that: blind. There’s no way to figure out what’s going on with an obviously biased outcome.

Beyond illustrating the need for robust testing and monitoring of any AI model, this example also illustrates a fundamental truth of responsible AI: it’s difficult. Even the biggest companies on the planet, with all the resources they have at their disposal, can run into big challenges. So if you’re feeling like your company is struggling to understand how to enter the AI waters without taking on too much risk, you’re not alone. As you’ll see in the chapters that follow, not just Apple, but companies as large as Google, Walmart®, Tesla®, Microsoft, and dozens of others have had to continually overcome challenges as they went.

As a business expert, not a data scientist, you’ll be most helpful in building any AI model by clarifying the importance of the inputs and deciding on the acceptable levels of confidence to meet business objectives. It’s incumbent upon the data scientist to ask the right questions. Accuracy can suffer if the model tries to account for some variable that isn’t actually important to the business case, but choosing to ignore that variable may be a business decision you can make to move things along.
