
| # | Cue | Captured by XAI | How? Or why not? |
|---|-----|------------------|------------------|
| 3 | Poor spelling and grammar (Jakobsson, 2007; Blythe et al., 2011) | Yes | Being treated as a regular text element they can be recognized by a detector |
| 4 | Specific group of senders and premises (Jakobsson, 2007; Blythe et al., 2011; Moody et al., 2017; Kim & Kim, 2013) | Partly | By being mentioned in the text to be analyzed |
| 5 | Style of the email (Blythe et al., 2011) | Yes | There exist ML methods that are able to analyze the style of a text. |
| 6 | Order in message (Kim and Kim, 2013) | Yes | Not only words but also the structure of a text can be analyzed. |
| 7 | Message quality elements (Kim & Kim, 2013) | Yes | By words semantically related to the cue |
| 8 | Trust and distrust, boredom proneness, lack of focus (Moody et al., 2017) | No | Depends on the email recipient and cannot be investigated by analyzing the email only |
| 9 | Time pressure (Kim & Kim, 2013) | Yes | Words indicating time pressure can also be detected as relevant for the classification of the email. |
| 10 | Semantic network analysis (Kim & Kim, 2013) | No | The algorithm does not take into account word frequency, proximity, and co-occurrence |
| 11 | Too much emphasis on security (Jakobsson, 2007) | Partly | By words semantically related to the cue |

Different groups and different aspects within these groups of cues necessitate the assignment of appropriate weights for their respective importance. The importance of an aspect cannot be generalized and varies depending on the email and its content. Therefore, the goal is to highlight and extract the relevant cues for each email individually. This has to be done in a way that users’ System 2 behavior is triggered by, on the one hand, their increasing phishing awareness and, on the other hand, decreasing phishing susceptibility, as described in the related works section.

ML models are known to pick up on stylistic and syntactic features. For stylistic features, words or groups of words can be detected that express a prompting or demand, and the sentiment and purpose for these prompting elements can be investigated [4, 24, 29]. An example is a prompt to a recipient to update his or her bank account where specific information can be expressed through different keywords such as “bank,” “account,” “update,” or “details.” The phishing detector can scan incoming emails for words or groups of words that are proven to be characteristic for phishing emails. Elements beyond plain text can be picked up by ML as long as they are in a form that is recognizable by ML. The category of the sender can be found through keywords that represent the industry, whereby the industry can be revealed by analyzing the prompting elements. Syntactic features such as the style of an email in terms of length or tone can be analyzed in an indirect way [4]. The length can be considered by counting words while the analysis of the tone is the same as for prompting elements. Generally, it can be stated that ML phishing detectors are able to capture the cues on a token-based approach, i.e., they catch relevant tokens that refer to specific groups of cue characteristics for the categorization of an email into phishing or nonphishing. Thus the score of a ML-based phishing detector depends on the presence or absence of traits.

## 19.5.4 Extracting Cues

To identify the cues and phrases in the email that best convey the suspicion to the user, an XAI system was designed that extracts this information (traits) from the underlying phishing detector. In terms of the XAI nomenclature, this can be considered a black-box outcome explanation problem [18]; that is, the aim is to explain the phishing detector’s score, not the detector’s inner workings [13, 34]. With the phishing detector assumed to be a black-box, the XAI algorithm has to be model-agnostic [33, 44]. This further allows for updates of the phishing detector and prevents compromise of its effectiveness [44]. Also, representation flexibility is required [44]; that is, parts of the actual email text are highlighted, which might be very different from the numerical machine learning model’s input. Another flexibility can be achieved through the extraction of phrases, instead of tokens, by connecting tokens and assigning an appropriate length to the connected tokens. A typical example that illustrates the advantage of using phrases is the negation of words such as “not good” that will not be recognized as “bad” if treated separately. When thinking about the implementation of a phishing detector and explainer in a real-world scenario, the aspect of efficiency is of high importance since it needs to run on the fly for massive amounts of emails coming in at a high frequency. The usage of a search-based approach, i.e., searching for relevant elements, can satisfy both characteristics of the artifact as being model-agnostic and efficient.

## 19.5.5 Examples of the Application of XAI for Extracting Cues and Phrases

The first characteristic listed in Table 19.1 is having links in an email where there is a demand from the sender of that email to click on the link. While Blythe et al. [4] and Kim & Kim [29] only emphasize the existence of links in emails, Moody et al. [36] and Canova et al. [7] differentiate between the different types of links. LIME and anchor explanations are only looking for words or phrases. Since LIME and anchor explanations do not recognize links, they cannot differentiate one type of link from another. A link can be recognized only if the explanation algorithm assigns importance to this link as a word or phrase for the classification of the email. Also, words such as “click” or “link” can provide information about the existence of a link. This is illustrated in Figure 19.5.

![](img/efffc69cb8cda75bcf341884e3396898_525_0.png)

**Figure 19.5** Example: click on link.

Figure 19.6 illustrates the second point in Table 19.1. Blythe et al. [4] state that a typical phishing email asks for a confirmation of banking details. This information can be captured by explanation algorithms, since this is often expressed by keywords such as “bank,” “account,” “update,” “details,” etc.

![](img/efffc69cb8cda75bcf341884e3396898_526_0.png)

**Figure 19.6** Example: banking details.

Another characteristic that can at least partly be found through explanation algorithms is poor spelling and grammar, an example of which is presented in Figure 19.7.

![](img/efffc69cb8cda75bcf341884e3396898_526_1.png)

**Figure 19.7** Example: error.

Most research on the detection of phishing emails mention the fifth characteristic listed in Table 19.2. This characteristic relates to phishing emails being exposed through a specific group of senders. For this analysis, only the bodies of the emails were considered. Though a separate focus on the sender was not included, the sender can still be investigated as a significant factor in the classification of the emails. In this case, the sender is also mentioned in the body and the subject of the text. Blythe et al. [4] and Kim and Kim [29] state that phishers most often pretend to be financial institutions. An example is presented in Figure 19.8.

![](img/efffc69cb8cda75bcf341884e3396898_527_0.png)

**Figure 19.8** Example: PayPal.

Logos of the sender as well as the style of an email can only be partly analyzed by the explanation algorithm. Just like links, the algorithm does not recognize the logo as a logo, but it can recognize it as a characteristic element in an email. Indirectly, the style of an email in terms of length or tone [4] can also be analyzed. The tone of an email can be categorized by finding relevant words. The length of an email, however, cannot be expressed through LIME or anchor explanations, though this might be important in neural networks. The email presented in Figure 19.9 is striking due to its short length and its being in mostly capital letters with a lot of exclamation marks. The capital letters and the exclamation marks evoke a tone of excitement in that email. The word “ignore” was used as an imputation method whenever the body of an email was empty so that the algorithm does not give an error message when working with an empty body, an empty subject, or both empty.

![](img/efffc69cb8cda75bcf341884e3396898_527_1.png)
