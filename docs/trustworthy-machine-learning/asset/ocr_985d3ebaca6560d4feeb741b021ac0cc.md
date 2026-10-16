Toolkit,⁸ which lists eight different broad consequences of the machine learning system that you should ponder:

+   1. Disinformation: the system helps subvert the truth at a large scale.
+   2. Addiction: the system keeps users engaged with it beyond what is good for them.
+   3. Economic inequality: the system contributes to income and wealth inequity by serving only well-heeled users or by eliminating low-income jobs.
+   4. Algorithmic bias: the system amplifies social biases.
+   5. Surveillance state: the system enables repression of dissent.
+   6. Loss of data control: the system causes people to lose control of their own personal data and any monetization it might lead to.
+   7. Surreptitious: the system does things that users don’t know about.
+   8. Hate and crime: the system makes bullying, stalking, fraud, or theft easier.

Links to case studies accompany each of these checklist items in the Ethical OS Toolkit. Some of the case studies show when the item has happened in the real-world, and some show actions taken to prevent such items from happening. Another source of case studies is the continually-updated AI Incident Database.⁹ Part 6 of the book, which is focused on purpose, touches on some of the items and case studies as well.

Starting with the checklist, your first step is to decide which items are good and which items are bad. In practice, you will read through the case studies, compare them to the Alma Meadow use case, spend some time thinking, and come up with your judgement. Many people, including you, will mark each of the eight items as bad, and judge the overall system to be too bad to proceed if any of them is true. But values are not universal. Some people may mark some of the checklist items as good. Some judgements may even be conditional. For example, with all else being equal, you might believe that algorithmic bias (item 4) is good if economic inequality (item 3) is false. In this second case and in even more complicated cases, reasoning about your preferences is not so easy.

CP-nets are a representation of values, including conditional ones, that help you figure out your overall preference for the system and communicate it to the machine.¹⁰ (The ‘CP’ stands for ‘conditional preference.’) CP-nets are directed graphical models with each node representing one attribute (checklist item) and arrows indicating conditional relationships. Each node also has a conditional preference table that gives the preferred values. (In this way, they are similar to causal graphs and structural equations you learned about in Chapter 8.) The symbol > represents a preference relation; the argument on the left is preferred to the one on the right. The CP-net of the first case above (each of the eight items is bad) is given in Figure 14.1. It has an additional node at the bottom capturing the overall preference for working on the problem, which is conditioned on the eight items. There is a simple, greedy algorithm