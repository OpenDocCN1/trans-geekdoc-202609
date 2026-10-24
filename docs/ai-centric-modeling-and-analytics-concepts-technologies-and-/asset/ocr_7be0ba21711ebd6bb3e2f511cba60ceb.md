Bayes theorem calculates the probability of the target variable given the independent variables, as in Equation 17.6:

P(Y|X1,X2...X11)=P(X1,X2...X11|Y)*P(Y)/P(X1,X2...X11) (17.6)

To further simplify the model, we can assume that the prior probability of Y (P(Y)) is equal to the proportion of phishing URLs in the training data.

We can also assume that the conditional probabilities of each independent variable, given the response variable (P(Xi|Y)), can be estimated using the training data.

With these assumptions, we calculate the probability of a URL being phishing as Equation 17.7 or not with Equation 17.8:

P(Y=1|X1,X2...X11)= P(X1|Y=1)*P(X2|Y=1)*...*P(X11|Y=1)*P(Y=1)/P(X1,X2...X11) (17.7)

P(Y=0|X1,X2...X11)= P(X1|Y=0)*P(X2|Y=0)*...*P(X11|Y=0)*P(Y=0)/P(X1,X2...X11) (17.8)

To classify a new URL, we compared its probability of being phishing (P(Y=1|X1,X2...X11)) to the probability of it not being phishing (P(Y=0|X1,X2...X11)).

If the probability of it being phishing is high, it is classified as phishing; otherwise, it is classified as not phishing.

Note that the denominator P(X1,X2...X11) is the same for both Equations 17.9 and 17.10, so it can be omitted when comparing the probabilities.

# 17.3.3.1.1 Logarithm Approach

log(P(Y=1|X1,X2,...,X11))=log(P(X1|Y=1))+log(P(X2|Y=1))+...+log(P(X11|Y=1))+log(P(Y=1)) (17.9)

log(P(Y=0|X1,X2,...,X11))=log(P(X1|Y=0))+log(P(X2|Y=0))+...+log(P(X11|Y=0))+log(P(Y=0)) (17.10)

# 17.3.3.1.2 Frequency Count Approach

To estimate the conditional probabilities of each independent variable given the response variable as Equation 17.11:

P(Xi|Y=j)=count(Xi=j and Y=j)/count(Y=j) (17.11)

where count(Xi=j and Y=j) is the number of times Xi=j and Y=j occur together in the training set; count(Y=j) is the number of times Y=j occurs in the training data.

If count(Xi=j and Y=j) is zero, Laplace smoothing is used to avoid zero probabilities as Equation 17.12:

P(Xi=j|Y=j)=(count(Xi=j and Y=j)+