
Input 1: 10x10 grid, black background. Objects: continuous random object, of shape 'B' with symmetric shape along both axes with upper left corner in position (2,1), of size 3x4, monochromatic of color cyan. continuous random object, of shape 'B' with symmetric shape along both axes with upper left corner in position (7,5), of size 3x4, monochromatic of color cyan. continuous random object, of shape 'A', with symmetric shape along both axes with upper left corner in position (1,7), of size 3x3, monochromatic of color cyan.

Output 1: 10x10 grid, black background. Objects: continuous random object, of shape 'B' with symmetric shape along both axes with upper left corner in position (2,1), of size 3x4, monochromatic of color blue. continuous random object, of shape 'B' with symmetric shape along both axes with upper left corner in position (7,5), of size 3x4, monochromatic of color blue. continuous random object, of shape 'A', with symmetric shape along both axes with upper left corner in position (1,7), of size 3x3, monochromatic of color red.

Figure 7.5: Textual description for the first input output pair of the task shown in Figure 7.1. The complete task description includes all pairs in combination with the input for the test image. The missing output has to be completed by the language model.

Language Module The language module receives a textual description for each task consisting of all input output pairs as well as the input test image. The description of the missing output image has to be predicted by the language model. We can use any pre-trained generative language model in a black-box fashion as part of our pipeline. We summarize all evaluated language models in Table 7.3. Throughout our evaluation, none of the used models were fine-tuned and have not seen ARC descriptions. Note, that even though multiple input output image descriptions are provided, the language model has no access to entire previous task descriptions which makes this a zero-shot setting. We include minimal pre- and post-processing steps of the textual descriptions such as trimming trailing text and skipping lengthy descriptions. To reduce variance resulting from the stochastic text generation process of the language models, we allowed 10 guesses per model and count a task as solved if at least 1 of the guesses is correct.

## 7.4 Results

To empirically evaluate our framework and implemented pipeline, we carried out experiments using various language models of different sizes of

![](img/c742333bcb21933724ca00794dbfb657_108_0.png)

Figure 7.6: A collection of ARC tasks that were solved using our approach but not by the top performing solutions [287, 7, 131]

the open-source Bloom architecture [227] as well as GPT-3 [28], namely text-davinci-003.

Note that for all our experiments, we generate the solutions in a zero-shot setting and did not fine-tune any of the language models. We evaluate our pipeline on the ARC training set and report the accuracy in Figure 7.7. Without ever encountering an ARC task during training, even the smallest language models can solve a non-trivial amount of tasks. However, most notably, the accuracy increases roughly linear with the logarithm of the number of parameters of the LLM.

Therefore, using our proposed framework it is possible to solve entire ARC tasks in an automated fashion that leverages pre-trained learned models. Moreover, larger models seem to perform better which hints at a potential increase in their capabilities. However, another key aspect of this approach compared to hand-crafted program searches is that the priors can be implicitly learned and are not fixed by the designer. This has the advantage that we could solve novel tasks which cannot be captured by existing approaches, as they do not match their specified priors exactly. We compare the set of successfully solved tasks of our approach with the top performing solutions of the original Kaggle competition [287, 7, 131]. We find that using our approach, we were able to solve tasks which could not be solved by any of the mentioned top performing solutions. A selection of such newly solved examples is shown in Figure 7.6.

![](img/c742333bcb21933724ca00794dbfb657_109_0.png)

Figure 7.7: Accuracy of our approach using language models of different sizes on the ARC training set. The accuracy follows a log-improvement as the number of parameters increases.

## 7.5 Conclusion

Current learning based approaches to solve ARC fail to be competitive, one reason being the limited number of tasks. We motivate to focus on natural language as a source of important human aligned priors to alleviate this lack of data. We present a general framework to combine visual abstraction and leverage language as a reasoning tool in order to tackle ARC. Furthermore, we implement a pipeline to solve tasks in an automatic end-to-end fashion based on large language models as zero-shot reasoners. The obtained results are a promising demonstration of the framework and indicate the viability of our approach. In particular, we were able to solve new tasks compared to state-of-the-art DSL approaches. Moreover, we highlight that there exist many possibilities for extensions such as a learned encoding or decoding step, fine-tuned LLMs or even end-to-end training of the entire pipeline.

## A Benchmark for Neural Algorithmic Reasoning

### Abstract

Algorithmic reasoning is a fundamental cognitive ability that plays a pivotal role in problem-solving and decision-making processes. Reinforcement Learning (RL) has demonstrated remarkable proficiency in tasks such as motor control, handling perceptual input, and managing stochastic environments. These advancements have been enabled in part by the availability of benchmarks. In this chapter we introduce PUZZLES, a benchmark based on Simon Tatham's Portable Puzzle Collection, aimed at fostering progress in algorithmic and logical reasoning in RL. PUZZLES contains 40 diverse logic puzzles of adjustable sizes and varying levels of complexity; many puzzles also feature a diverse set of additional configuration parameters. The 40 puzzles provide detailed information on the strengths and generalization capabilities of RL agents. Furthermore, we evaluate various RL algorithms on PUZZLES, providing baseline comparisons and demonstrating the potential for future research.

## 8.1 Introduction

Human intelligence relies heavily on logical and algorithmic reasoning as integral components for solving complex tasks. While Machine Learning (ML) has achieved remarkable success in addressing many real-world challenges, logical and algorithmic reasoning remains an open research question [234, 60, 162, 272, 185, 137, 15]. This research question is supported by the availability of benchmarks, which allow for a standardized and broad evaluation framework to measure and encourage progress [161, 273, 251].

Reinforcement Learning (RL) has made remarkable progress in various domains, showcasing its capabilities in tasks such as game playing [193, 258, 243, 13, 290], robotics [142, 145, 224, 216] and control systems [278, 288, 29]. Various benchmarks have been proposed to enable progress in these areas [263, 17, 26, 70, 259, 55, 153]. More recently, advances have also been made in the direction of logical and algorithmic reasoning within RL [136, 88, 183]. Popular examples also include the games of Chess, Shogi, and Go [152, 241]. Given the importance of logical and algorithmic reasoning, we propose a benchmark to guide future developments in RL and more broadly machine learning.

Logic puzzles have long been a playful challenge for humans, and they are an ideal testing ground for evaluating the algorithmic and logical reasoning capabilities of RL agents. A diverse range of puzzles, similar to the Atari benchmark [17], favors methods that are broadly applicable. Unlike tasks with a fixed input size, logic puzzles can be solved iteratively once an algorithmic solution is found. This allows us to measure how well a solution attempt can adapt and generalize to larger inputs. Furthermore, in contrast to games such as Chess and Go, logic puzzles have a known solution, making reward design easier and enabling tracking progress and guidance with intermediate rewards.

In this chapter, we introduce PUZZLES, a comprehensive RL benchmark specifically designed to evaluate RL agents' algorithmic reasoning and problem-solving abilities in the realm of logical and algorithmic reasoning. Simon Tatham's Puzzle Collection [262], curated by the renowned computer programmer and puzzle enthusiast Simon Tatham, serves as the foundation of PUZZLES. This collection includes a set of 40 logic puzzles, shown in Fig-
