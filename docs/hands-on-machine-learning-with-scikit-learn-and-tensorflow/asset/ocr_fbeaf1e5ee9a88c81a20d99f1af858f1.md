1. First you would look at what spam typically looks like. You might notice that some words or phrases such as “4U,” “credit card,” “free,” and (“amazing”) tend to come up a lot in the subject. Perhaps you would also notice a few other patterns in the sender's name, the email's body, and so on.

2. You would write a detection algorithm for each of the patterns that you noticed, and your program would flag emails as spam if number of these patterns are detected.

3. You would test your program, and repeat steps 1 and 2 until it is good enough.

![](bbox=[0.142, 0.285, 0.857, 0.506])

Figure 1-1. The traditional approach

Since the problem is not trivial, your program will likely become a long list of complex rules—pretty hard to maintain.

In contrast, a spam filter based on Machine Learning techniques automatically learns which words and phrases are good predictors of spam by detecting unusually frequent patterns of words in the spam examples compared to the ham examples (Figure 1-2). The program is much shorter, easier to maintain, and most likely more accurate.