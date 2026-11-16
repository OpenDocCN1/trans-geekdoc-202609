
In February 2024, OpenAI announced Sora, a text-to-video model that creates incredibly realistic videos from short prompts. Shortly thereafter, in April 2024, Microsoft announced a new AI model called VASA that can create “lifelike talking faces of virtual characters with appealing visual affective skills (VAS), given a single static image and a speech audio clip.” With other open source text-to-video models being rapidly developed, we’re about to enter an age where the very nature of what’s real will be challenged. Recently, a company in Hong Kong lost $25 million when an employee was duped on a Zoom call by speaking to a deep fake of the company’s CFO. We’re about to enter a world where anyone can instantly and cheaply create a sophisticated deepfake video. It’s not hard to imagine that *The Matrix* is not far behind.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_181_0.png)

If your LLM application is multimodal and can read text from images or video, you’re opening up a whole new world of vulnerabilities. Consider that prompt injection attacks can now be launched by including malicious text in an image fed into your model as a prompt. Or your training data could be poisoned if you include images with text that mislead your model. These are just more vectors to watch for!

## Autonomous Agents

Just a few months after the introduction of ChatGPT, Auto-GPT was launched in March 2023 by Toran Bruce Richards of the software development company Significant Gravitas. Built on OpenAI’s GPT-4, Auto-GPT introduced the concept of autonomy, allowing LLM-powered agents to act toward a goal with minimal human guidance. This feature enabled Auto-GPT to generate prompts to achieve a user-defined goal autonomously, differentiating it from ChatGPT’s requirement for continuous human input. The Auto-GPT framework introduces expanded short-term memory capabilities, allowing agents to connect to the internet and call upon third-party services.

The introduction of Auto-GPT generated massive buzz at the time, quickly gaining traction and generating substantial discussion for its approach to AI autonomy. Thousands of users rapidly adopted the tool for various projects, leveraging its ability to tackle more complex tasks than ChatGPT could handle alone. This included creating and using unsupervised agents for software development, business operations, financial transactions, and even health care–related tasks.

The adoption of Auto-GPT faced challenges due to its architectural design and the operational costs associated with its inefficient use of OpenAI’s expensive API resources. The buzz around Auto-GPT soon died out. However, this isn’t the end of the story of autonomous agents built on LLMs.

In the wake of Auto-GPT, dozens of other open source and research projects have taken up that mantle, and we’ll surely see fast progress in making these concepts more generalizable and less expensive. Beyond that, mainstream players like OpenAI have introduced concepts like plug-ins that allow their LLMs to interact directly with third-party internet resources. These goal-completion-seeking, autonomous agent architectures already show massive potential in many applications. With the desire to use AI in this fashion, we’ll undoubtedly see rapid investment and progress.

However, the most critical lesson from Auto-GPT was the incredibly rapid pace at which it was deployed in the wild with little to no oversight. We discussed excessive agency back in Chapter 7: putting unsupervised power in the hands of a naive AI, with few guardrails in place, could be incredibly dangerous—and few stopped to think about it. The development community’s overall lack of caution shown in the rapid adoption of the technology demonstrates with some certainty that we must put better security and safety measures in place before the next leap in self-directed autonomous systems. We can’t trust the broad human population to supervise these capabilities independently. The task is too complex to leave to individuals; we must solve it as an industry.

## Responsibility

We’re on a curve showing a continued, dramatic increase in AI capabilities over the coming years. How do you plan for the future and make durable decisions today that will pay off and keep you, your customers, your employees, your organization, and society at large safe as things accelerate? How do you live up to the *great responsibility* of managing this *great power*?

The previous chapters of this book have been grounding to help you understand the possible. What risks exist today? What real-world examples have shown the impact of these vulnerabilities? We’ve even looked at some far-flung, fictional, but plausible examples of how these threats might manifest themselves in the future.

Throughout the book, I’ve offered you the best practical techniques to address these vulnerabilities by using state-of-the-art practice with the input of experts across the industry. However, with things moving quickly, your best defense is to have a generalized, flexible framework to build your defenses. In this book’s last section, I’ll give you a framework you can customize to fit your needs and that you can adapt as you grow and the technology moves forward.

## The RAISE Framework

Let’s walk through a framework I have built to help you plan, organize, and achieve your goals for a safe and secure project. As you can see in Figure 12-1, I call this six-step process the Responsible Artificial Intelligence Software Engineering (RAISE) framework. First, we'll review each step's meaning and why it matters. Then, we'll break it down into a manageable checklist your team can use to track your work along your journey.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_183_0.png)

Figure 12-1. The RAISE framework

The following list includes the six steps; let's take look at each of these in turn:

- 1. Limit your domain.
- 2. Balance your knowledge base.
- 3. Implement zero trust.
- 4. Manage your supply chain.
- 5. Build an AI red team.
- 6. Monitor continuously.

## Limit your domain

Constraining your application to focus on a limited functional domain is first on the list because it is so fundamental and solves a host of problems. ChatGPT is an example of an LLM application with nearly zero domain boundaries. Part of its appeal is that it was trained on almost the entire internet, and you can ask it almost anything. It doesn't matter if you want a dessert recipe or a block of Python code that calculates pi to a thousand digits. ChatGPT is here to help. It has an unconstrained domain.

The challenge with unconstrained domains is that the development team must build broad, general-purpose defenses. Rather than designing a short list of "allowed" activities, you must design and maintain a comprehensive and likely ever-growing list of "denied" activities. Imagine the job of being on the guardrails team at OpenAI. You're going to be constantly expanding this list that says:

- * Don't engage in hate speech.
- * Don't help hackers steal things.
- * Don't help people build weapons (even if they miss their grandma— see Chapter 4).
- * And on and on and on...

It’s like playing Whac-A-Mole. This explains why we see reports of new security issues with ChatGPT every month. But you’re not building ChatGPT, so how does this apply to you? If you’re using a general-purpose foundation model like GPT-4, you start with an unconstrained domain. In recent real-world examples, a shipping company and a car company both put support chatbots on their websites to help improve customer service and reduce costs. Great idea! However, they based these on general-purpose foundation models without sufficiently restricting their domain. Users quickly jailbroke them via prompt injection (see Chapters 1 and 4—this isn’t much different than Tay), causing them to engage in activities ranging from writing songs about the company’s poor customer service to writing Python code that the hacker requested, and all at the company’s expense. (See Chapter 8 for a discussion of DoW attacks.)

On the other hand, if your company wants to build an application for use on a specific use case, such as giving fashion advice, you can take advantage of that limited scope. It will be easier and more effective to drive laser focus for your LLM on the latest trends in fashion than enforcing a list of all the things not to do.

How do you do this? While this list may evolve as things accelerate, here are some tips on driving focus to limit the domain:

- • Where possible, start with a smaller, less-general-purpose foundation model. Whether you go the open source route or with an LLM-as-a-service provider, there are now thousands of specialized models. These models are usually trained on smaller, more focused datasets. If your model wasn’t exposed to hate speech, napalm recipes, or Python code while it was trained, it’s almost impossible for someone to trick it into straying into such territory. As a bonus, these smaller, special-purpose models may be dramatically cheaper to operate at scale.

- • If you start with a more general-purpose model, fine-tune it with a function that rewards it for staying on topic. Encoding the “desire” to stay on task and in scope can be more powerful and elegant than trying to build restrictive guardrails later—although you will probably need to add those, too. Use this to drive alignment between the model and your goals.

## Balance your knowledge base

You must maintain a dynamic balance regarding how much data you give to your LLM at runtime. Striking the right balance is one of the most important tasks in your system design and will be a significant factor in its safety and security.

If you give your model access to too little information, it may be prone to hallucinations. As discussed in Chapter 6, while hallucinations can be cute, they can leave your organization open to reputational, legal, and safety risks. Equipping your model with
