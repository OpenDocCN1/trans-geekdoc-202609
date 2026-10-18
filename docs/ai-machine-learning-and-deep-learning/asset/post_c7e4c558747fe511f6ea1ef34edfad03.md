
sample that has the most influence on the model can be found, and then the poisoning operation can be performed on it.

## 3.4 SPECIFIC ATTACKS IN THE REAL WORLD

### 3.4.1 Attacks on Natural Language Processing

Li et al. [29] proposed the TextBugger generic adversarial attack framework, which can generate adversarial text against state-of-the-art text classification systems in both white-box and black-box settings. After the evaluations, they stated that TextBugger has the following advantages:

- 1. *Effectiveness*: It significantly outperforms the state-of-the-art attack methods in terms of the attack success rate.
- 2. *Invisibility*: It retains most of the usability of the original normal text, where 94.9% of the adversarial text can be successfully recognized by human readers.
- 3. *Efficiency*: Its computational complexity of generating adversarial text is linearly related to the length of the text.

In the white-box scenario, the keywords in the sentences can be found by computing the Jacobian matrix; in the black-box scenario, the most important sentences can be found first, and then a scoring function can be used to find the keywords in the sentences. Adversarial samples are used in the real-world classifier, and good results are achieved. The principle of the algorithm is shown in Figure 3.2.

![](img/efffc69cb8cda75bcf341884e3396898_111_0.png)

**FIGURE 3.2** Flow of TextBugger algorithm.

TextBugger has five methods to fool the NLP model, which are insert, swap, delete, subword, and subcharacter. This slight change works in both black-box and white-box scenarios.

- 1. *White-box attack:* It finds the most important word by using Jacobian matrix, then generates five types of bugs and finds the best one according to the confidence level.

*Step 1:* Find the most important word. This is done through the Jacobian matrix with two parameters: *K* (the number of categories) and *N* (the length of the input). The derivative of each category with respect to the input at each time step is obtained to measure the degree of influence of each word in the input on the output label.

*Step 2:* Bug generation. In order to ensure that the generated adversarial samples are visually and semantically consistent with the original samples, the perturbations should be as small as possible. Two levels of perturbation are considered:

*Letter-level perturbation:* Simply changing the order of letters in a word at random can easily allow the model to determine the word as unrecognized, thus achieving the effect of attack.

*Word-level perturbation:* The closest word can be found in the word embedding layer. However, in the word2vec model,

some antonyms are also close in distance. This would then completely change the meaning of the utterance, and then the semantic preservation technique is used to experiment in the GloVe model.

The adversarial samples generated using the candidate words are fed into the model to calculate the confidence level of the corresponding category, and the word that gives the largest confidence drop is selected. If the semantic similarity between the adversarial sample after replacing the words and the original sample is greater than the threshold, the adversarial sample is generated successfully. If it is not greater than the threshold, the next word is selected for modification.

- 2. *Black-box attack:* In the black-box scenario, there is no indication of gradient. We first discover the important sentences and then discover the important words in the sentences.

Step 1: Find the important sentences. We can divide the document into multiple sentences and use sentence by sentence as the input to see the classification results. This filters out the sentences unimportant for the predicted labels, and the remaining sentences can be sorted according to the confidence level.

Step 2: Find the important words. Among all possible modifications, the most important words in the sentence should be found first and then slightly modified to ensure the semantic similarity between the adversarial sample and the original sample. To evaluate the importance of a word, the difference between the confidence level before and after removal can be used.

Step 3: Bug generation. This step is basically the same as the one in the white-box attack.

### 3.4.2 Attacks Using Data Poisoning

Chen et al. [30] consider a new type of attack called the Backdoor Attack, in which an attacker aims to create a Backdoor in a learning-based authentication system so that he can easily bypass the system by using Backdoor to inject toxic samples into the training set.

It first tries to achieve a high attack success rate on a set of backdoor instances that are similar to the input key. It can achieve this by changing the resolutions. In this strategy, it defines the set of backdoor instances as

where x is the vector of an input instance, H, W, and 3 are the dimensional vector of pixel; clip(x) is used to clip each dimension of x to the range of pixel values.

It then uses the pattern strategy to poison the input. Blended injection, accessory injection, and blended accessory injection are three potential strategies to achieve pattern strategy. The blended injection strategy generates poisoning instances and backdoor instances by mixing the benign input instances and key patterns. However, blended injection requires the entire input data to be perturbed during both training and testing, which may not be feasible for real-world attacks with some limitation. The accessory injection uses some pattern and its transformation to add into the input data. For instance, if the input data is a set of human face images, we can use two types of eyeglasses and its transformation to generate a poisoning instance. The last strategy is blended accessory injection, it takes advantage of the preceding two strategies by combining their pattern injection functions.

In [30], researchers used attack success rate, standard test accuracy, and attack success rate with a wrong key to evaluate the backdoor poisoning attacks. As the results showed, in the input-instance-key attack evaluation, by injecting as few as only five poisoning samples into the training set, they can successfully create backdoor instances with 100% attack success rate. In the other three strategies, with different injection poisoning samples, the model can achieve a 100% attack success rate separately. And the standard test accuracy of strategies is similar to the one trained using pristine training data, so that the approaches can achieve stealthiness. Furthermore, the attack success rate with a wrong key remains 0% in all strategies.

## 3.5 DISCUSSIONS AND OPEN ISSUES

Although many adversarial attacks have been proposed, the causality of adversarial examples remains unclear. Early research on this problem

attributed the emergence of adversarial examples to model structure and learning methods. Researchers believe that appropriate strategies and network structure will significantly improve the robustness of adversarial examples. Researchers have explored this line of thinking, especially the related research on fuzzy gradient generation [31]. On the contrary, recent studies have found that the appearance of the opposite is more likely to be the result of high-dimensional data geometry [32] and insufficient training data [33]. Specifically, the literature [32] proved that adversarial disturbances are scaled on several proof-of-concept data sets (such as concentric *n*-dimensional spheres). Ludwig et al. [33] showed that adversarial tasks require more data than ordinary machine learning tasks and that the required data size may be scaled.

Although many adversarial attack methods are defined under different indicators, there is no general robust decision boundary learned by a certain DNN for a specific training strategy [34].

For white-box attacks, we still have not seen a defense method that can balance the effectiveness and efficiency. In terms of effectiveness, adversarial training shows the best performance, but the computational cost is high. In terms of efficiency, the configuration of many defense/detection systems based on randomness and denoising takes only a few seconds. However, many recent papers [35] show that these defense methods are not as effective as they claim.

## 3.6 CONCLUSIONS

This chapter presented a comprehensive survey of the adversarial attacks on deep learning. The discovery that deep learning is at the heart of current developments in machine learning and artificial intelligence has led to a number of recent contributions that have designed adversarial attacks for deep learning. Despite their high accuracy for a wide variety of computer vision tasks, deep neural networks have been found to be susceptible to subtle input perturbations that cause them to completely change their output. This chapter reviewed these contributions, focusing mainly on the most influential and interesting works in the literature. It is evident that
