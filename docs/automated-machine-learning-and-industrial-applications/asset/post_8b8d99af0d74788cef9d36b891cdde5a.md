
![](img/5510bd7390ed7002b5774fe8c2be9eff_169_0.png)

Figure 7.5 Trilateral modifiers.

modifiers into three groups (Enhancers, Emphasizers, and Reducers) based on the extent to which they are capable of amplifying the associated sentiment. Enhancers increase the strength of the sentiment expressed to the fullest extent, denoting the exciting point on the scale. For example, “I am totally impressed with your response”, where “totally” is an enhancer-type modifier that strengthens the degree of positivity to the completest extent.

Emphasizers are the modifiers that increase the strength of the associated sentiment, but to a certain level, but not to the fullest level as that of enhancers. Consider the user inquiry, “I’m very happy with your answer.” Here, “very” acts as an emphasizer, which increases the positivity of the sentiment expressed by the user toward a chatbot.

Reducers are the adverbs that decrease the strength of the sentiment present in the dialog. For example, consider the user query, “I have a mild headache now.” The term “mild” turns as a reducer that decreases the strength of the sentiment. The trilateral categorization of modifiers is shown in Figure 7.5.

## 7.3.3 Sentiment Polarity Detection

In the proposed methodology, sentiment polarity is detected by using a nonary scale proposed in ref. [23]. In the existing works on sentiment polarity [18–21], a binary or ternary classification is accomplished either (positive, negative) or (positive, negative, neutral). By using the trilateral modifiers, it is still possible to detect the sentiment polarity accurately so that the chatbot can get the real tone behind the user text and can act accordingly.

For example, consider the user text to the Siri Chatbot: “I am completely depressed.” From the text, it can be clearly understood that the user is in an extreme case of depression, depressed to a higher extent, which is revealed by the presence of the enhancer-type modifier “completely.” So, by giving proper weight to the presence of modifiers, it is possible for the chatbot to come to a proper level of understanding of the user’s situation and thereby provide an appropriate response. If the modifiers are not given due weight, then it may lead to an improper understanding of the real tone behind the user text. The nonary scale developed in the proposed methodology is presented in Figure 7.6.

The nonary scale has been framed by the association of three types of modifiers with the adjectives or verbs of positivity or negativity. For instance, when an enhancer-type adverb accompanies an adjective or verb of positivity, the polarity of the sentiment is classified as extremely strong positive. Similarly, if the same modifier is associated with an adjective or verb of negativity, the polarity of the sentiment is classified as extremely strong negative.

## 7.3.4 Workflow of Customer Service Inquiry–Chatbot Response

Figure 7.7 shows the workflow of chatbot sentiment polarity detection. The text present in the customer service inquiry is fetched through the chatbot user interface and fed as input to the pre-processing module, where various subtasks of pre-processing, such as case conversion, stop word removal, tokenization, and stemming, are carried out to make the text ready for analysis. The pre-processed text is fed into the subjectivity detection module, wherein the text is tagged using a PoS tagger to tag the tokens with their appropriate grammatical counterparts, such as nouns, adjectives, verbs, etc. In this module, it is identified whether the text is subjective or not. Subjective texts are the source of sentiments. The next task is to use trilateral modifiers to find the types of adverbs associated with the sentiment. Based on the intensifying capability of the modifiers, the real tone of the sentiment can be understood. Finally, the chatbot sentiment polarity detection is carried out by applying the framed nonary scale that detects the accurate tone or polarity of the sentiment expressed in the text.

![](img/5510bd7390ed7002b5774fe8c2be9eff_171_0.png)

Figure 7.7 Workflow of chatbot sentiment polarity detection.

![](img/5510bd7390ed7002b5774fe8c2be9eff_172_0.png)

Figure 7.8 Sentiment detection in a sample chatbot–customer interaction.

A sample chatbot–customer conversation and detecting the polarity of the sentiment with proposed methodology is illustrated in Figure 7.8.

## 7.3.5 Scoring

Scoring is done to assign a value to the sentiment-bearing term based on its positivity or negativity, accompanied by the modifier, if any. A sentiment score is a numerical representation of the polarity of the sentiment-bearing term. Existing works related to the task of scoring used a simple method to arrive at the value for a sentiment-bearing term. First, the score for the adjective or verb is obtained from a lexical resource such as SentiWordNet. Next, the obtained score plus or minus one (according to the presence of modifiers) gives the appropriate score. To understand the logic, consider a sentiment-bearing term that is positively oriented and has a score of 0.42 as obtained from the lexical resource. If the sentiment-bearing term is accompanied by a modifier that tends to increase the strength of the specific term, then the score is updated by incrementing the original score by 1, obtaining 1.42 as far as this example is concerned. Alternatively, if the term is associated with a modifier that tends to reduce its strength, then the updated score is obtained by decrementing the original score by 1, obtaining −0.58, in this case. Now, the problem is that this approach to scoring the sentiment-bearing terms does not take into account the trilateral modifiers introduced in the proposed methodology for chatbot sentiment analysis. With respect to improving the chatbot’s understanding of the customer’s inquiries, it is necessary to analyze the customer’s text in a fine-tuned manner so that the chatbot can provide a tailored response satisfying the customer. To accomplish this task, the proposed trilateral modifiers must also be considered while computing the scores. A few examples of trilateral modifiers are shown in Table 7.5.

The proposed methodology for chatbot sentiment analysis has framed equations for calculating sentiment scores by extending the work of ref. [22].

- Let T denote the sentiment-bearing term.
- Let X denote an enhancer-type modifier.
- Let Y denote an emphasizer-type modifier.
- Let Z denote a reducer-type modifier.
- Let T_X denote a sentiment-bearing term associated with an enhancer-type modifier.
- Let T_Y denote a sentiment-bearing term associated with an emphasizer-type modifier.
- Let T_Z denote a sentiment-bearing term associated with a reducer-type modifier.

Let S denote the sentiment score and W denote the weight of the modifier, which ranges between 0 and 1. The Equations 7.1–7.3 below are sample equations developed as part of the proposed methodology for chatbot

Table 7.5 Few examples of trilateral modifiers.

| Enhancers | Emphasizers | Reducers |
|---|---|---|
| Completely | Very | A little |
| Perfectly | Really | Mildly |
| Absolutely | Remarkably | Somewhat |

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
Assign the score S from SentiWordNet lexicon according to the positivity or negativity of the Sentiment-bearing term T.
End for
```
