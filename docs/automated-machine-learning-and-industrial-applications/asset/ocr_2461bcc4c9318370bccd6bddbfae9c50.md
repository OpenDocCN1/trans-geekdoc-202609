sentiment analysis. These three equations correspond to adjectives/verbs of positivity. Similarly, equations to handle adjectives/verbs of negativity were also framed.

```
S(T_X)=S(T)+(1-S(T))*W(X)       (7.1)
S(T_Y)=S(T)+(1-S(T))*W(Y)       (7.2)
S(T_Z)=S(T)+(1-S(T))*W(Z)       (7.3)
```

A part of the pseudocode developed for sentiment polarity detection is presented below:

```
Input: Customer's inquiry(I) to chatbot
Output: Polarity(P) of the sentiment present in the inquiry text and Sentiment score(S)
Let X denote an enhancer-type modifier,
Let Y denote a emphasizer-type modifier
Let Z denote a reducer-type modifier

For every sentiment-bearing term(T) present in I do
If any adverb/verb(M) associated with T then
Switch(Type of M)
Case X and T is a positive sentiment:
Customer sentiment = “Extremely strong positive”
Compute S using equation(1)
Case Y and T is a positive sentiment:
Customer sentiment = “Strong positive”
Compute S using equation(2)
Case Z and T is a positive sentiment:
Customer sentiment = “Almost positive”
Compute S using equation(3)
......
End of switch
Else
Assign the score S from SentiwordNet lexicon according to the positivity or negativity of the Sentiment-bearing term T.
End for
```