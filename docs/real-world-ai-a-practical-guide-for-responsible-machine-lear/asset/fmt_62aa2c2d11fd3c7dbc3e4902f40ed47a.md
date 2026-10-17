
As you’re making these choices about the scope of your model, it’s important to consider the ethical implications of its decisions. If you’ve decided to optimize your model to the point where it’s 90 percent accurate, that means that 10 percent of the time, it’s getting the decision wrong. If your model is classifying support tickets as higher or lower priority, maybe that 10 percent isn’t such a big deal. But if it’s identifying reports of sexual assault, misclassifying 10 percent could represent a significant ethical failure, not to mention the introduction of substantial liability. Take the example of Uber®, which uses a system called COTA (Customer Obsession Ticket Assistant) to classify its support tickets. COTA uses machine learning and NLP (Natural Language Processing) to quickly evaluate whether a ticket is about a technical issue with the app, a fare dispute, or any of the other thousands of possible types of issues that commonly arise for customers and drivers on the platform. Once it knows what type of issue it’s dealing with, COTA routes the ticket to the correct team in order to get it addressed. While human agents are backing up COTA, it’s still crucial that the system avoids misclassification as much as possible—the risk of even one sexual assault complaint getting routed to the technical support team is far too great. In the development of a tool like COTA, business-focused roles like that of Product Manager are key. The data science team is focused on making the model faster and more accurate across the board—but the person focused on business objectives is going to be the crucial voice when it comes to defining how to balance speed, risk, and accuracy.

If you’re introducing a model that used to do something that relied on humans making ethical decisions, you’ll want to guard against your data science team being too homogeneous. The job of the data scientist is essentially to encode intentional bias into the model to make a decision; that’s how decisions are made. If the humans supplying the data and creating the algorithms introducing that bias don’t consider enough context on sensitive areas that usually rely on human judgment, they could introduce unintentional bias.

Also, recall Microsoft’s Twitter chatbot, Tay, which used reinforcement learning to get better at conversation, but whose training wasn’t secured against bad actors. Tay was a research project by two teams at Microsoft to explore conversational understanding. The chatbot used AI and content written by a dedicated human staff to form its responses and develop conversational patterns. But Tay’s biggest source of data was relevant, public data that had been anonymized and filtered. In essence, Tay was supposed to learn how to converse with humans through Twitter by studying the user-generated dialogues tweeted at her. As Microsoft stated when launching Tay, “The more you chat with Tay, the smarter she gets.”[10](#Alyssa-Simpson-Rochwerger_Real-World-AI_PRODUCTION_v101-4.xhtml#footnote-004) Unfortunately, there was no filter on exactly what Tay could or would learn from fellow Twitter users. As a result, Tay was fed a million malicious conversation examples by 4chan. It ended up becoming an extremist chatbot that promoted Nazism. In many cases, Tay was simply repeating inflammatory lines that had been tweeted at it. However, the more racist and profane content fed to Tay, the more racist and profane it became by virtue of her programming and lack of any filter applied to what was relevant conversation and what was trash or moderation of data inputs.

AI isn’t magic. It’s a collection of technologies that can be harnessed to make decisions that serve a set of goals. We all use AI in our everyday lives, so the way models are designed matters. The results you get matter. A lot more than just data science goes into a model’s creation—business decisions make up the most significant portions of the work involved. Choosing the model’s parameters and scope and determining when its accuracy is good enough to support the business case, when and how to deploy it, and how to monitor its performance are crucial to its success.

Consider a healthcare scenario of matching patient records. When a person shows up at a hospital, it’s helpful and sometimes critical in order to deliver life-saving care for doctors to have the patient’s medical history at their fingertips so they can better understand their current medical condition. Consider the scenario where perhaps the patient has changed addresses since their last visit to the hospital, or perhaps they got married and changed their name, or perhaps they simply abbreviated their address on the intake form slightly different from the last time they were at the hospital.

|  || Record 1 || Record 2 || Record 3 |

| --- | --- | --- | --- |

| Name || John Doe || John Doe || Jon Doe |

| --- | --- | --- | --- |

| Date of Birth || 1/1/1980 || 01/1/1980 || 01/01/1980 |

| Address || 1500 Main Street || 1500 Mn St || 1500 Maine St |

| City || NY || New York || New York |

| State || NY || NY || NY |

Hospitals commonly use machine learning based models to do patient record matching. In this case, you can see that the three records are not an exact match, but as a human evaluating this, you can tell that it’s highly probable that the three records are from the same person. A machine learning system might not have the same level of confidence. As a businessperson working with AI, it’s appropriate for you to ask questions like, “What is the risk if we accidentally match up records where it wasn’t the same person?” Or, “Is it riskier not to match up records when it was likely the same person, causing the doctor to miss a key piece of historical medical data?”

Business logic, data transformation, and confidence thresholds must be set up to make a series of decisions that lead to the logical machine learning based conclusion that all three records are of the same person. It’s critical to be a part of these decisions and talk about the business and customer implications of how they are weighted and decided.

Like everything else in business, AI is only a tool. It’s only as valuable as what it can do for your business.

# A Failure of Objectives

It’s not uncommon—in fact, it’s shockingly common, even among businesses seasoned in AI work—that a huge investment of money and resources is made in an AI solution, only to have it produce the wrong result or even fail completely. A company can do all the “right” things, hire smart and experienced people, and have the best intentions, and still wind up expensively spinning their wheels rather than achieving objectives.

Case in point: in October of 2013, IBM announced an exciting partnership with the University of Texas’s MD Anderson Cancer Center. The alliance would use Watson’s cognitive computing system to take cancer research to new heights. After more than three years of work and more than $62 million spent by MD Anderson, the project was put on hold, having never actually used the technology on a patient.

One of the reasons was that the MD Anderson team incorrectly identified and failed to deeply understand the specific problem that AI had the potential to impact. Applying machine learning to an objective as broad as “cure cancer” will quickly reveal the limitations of the technology. An AI model needs a specific problem to solve in the present, not a faraway future goal. This is partly because AI isn’t a “set it and forget it” type of system that will keep churning out results without human intervention. It requires constant maintenance, management, and course-correction to continue to provide meaningful, desired output. Without having a clear idea of the objectives, success measurements, carefully defined expectations, milestones, and guidelines when embarking on a project, the chances of success are slim—as MD Anderson discovered.
