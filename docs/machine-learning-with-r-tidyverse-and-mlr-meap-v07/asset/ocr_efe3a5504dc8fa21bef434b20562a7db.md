It isn't necessary for you to memorize the softmax function, so feel free to skip this, but the softmax function is defined as:

Where p_a is the probability of a case belonging to class a, e is Euler's number (a fixed constant ~ 2.718), and logit_a, logit_b, and logit_c are the logits for this case for being in classes a, b, and c, respectively.

If you're a math-buffer, then this can be generalized to any number of classes using the equation:

Where p_j is the probability of being in class j, and k=1 F04 12b means to sum the e^logits from class 1 to class K (where there are K classes in total).

Write your own implementation of the softmax function in R and try plugging other vectors of numbers into it. You'll find it always maps the input to an output where all the elements sum to one.



Imagine you're a historian interested in the RMS Titanic, which famously sank in 1912 after colliding with an iceberg. You want to know whether socioeconomic factors influenced a person's probability of surviving the disaster. Luckily, such socioeconomic data is publicly available!

Your aim is to build a binomial logistic regression model to predict whether a passenger would survive the Titanic disaster or not, based on data such as their gender and how much they paid