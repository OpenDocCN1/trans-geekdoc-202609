| Speaker | Dialogue Act | Utterance |
|---|---|---|
| A | YES-NO-QUESTION | *So do you go college right now?* |
| A | ABANDONED | *Are yo-* |
| B | YES-ANSWER | *Yeah,* |
| B | STATEMENT | *It’s my last year [laughter].* |
| A | DECLARATIVE-QUESTION | *You’re a, so you’re a senior now.* |
| B | YES-ANSWER | *Yeah,* |
| B | STATEMENT | *I’m working on my projects trying to graduate [laughter]* |
| A | APPRECIATION | *Oh, good for you.* |
| B | BACKCHANNEL | *Yeah.* |

Figure 8.4: An example of dialogue act labeling (Stolcke et al., 2000)

# 8.6 Dialogue acts

The sequence labeling problems that we have discussed so far have been over sequences of word tokens or characters (in the case of tokenization). However, sequence labeling can also be performed over higher-level units, such as utterances. Dialogue acts are labels over utterances in a dialogue, corresponding roughly to the speaker’s intention — the utterance’s illocutionary force (Austin, 1962). For example, an utterance may state a proposition (it is not down on any map), pose a question (shall we keep chasing this murderous fish?), or provide a response (aye aye!). Stolcke et al. (2000) describe how a set of 42 dialogue acts were annotated for the 1,155 conversations in the Switchboard corpus (Godfrey et al., 1992).⁸

An example is shown in Figure 8.4. The annotation is performed over UTTERANCES, with the possibility of multiple utterances per conversational turn (in cases such as interruptions, an utterance may split over multiple turns). Some utterances are clauses (e.g., So do you go to college right now?), while others are single words (e.g., yeah). Stolcke et al. (2000) report that hidden Markov models (HMMs) achieve 96% accuracy on supervised utterance segmentation. The labels themselves reflect the conversational goals of the speaker: the utterance yeah functions as an answer in response to the question you’re a senior now, but in the final line of the excerpt, it is a backchannel (demonstrating comprehension).

For task of dialogue act labeling, Stolcke et al. (2000) apply a hidden Markov model. The probability p(w_m | y_m) must generate the entire sequence of words in the utterance, and it is modeled as a trigram language model (§ 6.1). Stolcke et al. (2000) also account for acoustic features, which capture the prosody of each utterance — for example, tonal and rhythmic properties of speech, which can be used to distinguish dialogue acts such

⁸Dialogue act modeling is not restricted to speech; it is relevant in any interactive conversation. For example, Jeong et al. (2009) annotate a more limited set of speech acts in a corpus of emails and online forums.