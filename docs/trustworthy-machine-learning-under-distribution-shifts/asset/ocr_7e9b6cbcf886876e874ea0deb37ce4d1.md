# 5 MACHINE VISION THERAPY

![](bbox=[0.125, 0.147, 0.477, 0.258])

![](bbox=[0.523, 0.147, 0.875, 0.258])

# Common MLLM Solution to Vision Tasks

# Denoising In-Context Learning

![](bbox=[0.125, 0.298, 0.477, 0.408])

| | |
|---|---|
| is a | hound ? Answer: True;
| is a | hound ? Answer: False;
| is a | | hound ? Answer:output |

![](bbox=[0.523, 0.413, 0.565, 0.438])

: Maybe basket hound (Wrong).
: It's different from basket hound, so the output is False!

> FIGURE 5.1. Illustration of our methodology: Upper row: Comparison between common fine-tuning and fine-tuning via Machine Vision Therapy. Our method potentially eliminates the necessity for human-annotation by leveraging the knowledge from MLLMs. Lower row: Comparison between previous MLLM solution to vision tasks and Denoising-In-Context Learning strategy. Instead of considering all classes, our method makes predictions using a pair of positive and negative examples.

used thanks to their strong generalization performance while effectively avoiding training vision models from scratch. When deployed to Out-of-Distribution (OOD) scenarios [235, 236, 28, 237, 238, 46, 219, 240], their recognition performance could be seriously degraded [241]. Downstream fine-tuning has been a common practice to regain the generalizability [242, 243, 247], but it requires additional label acquisition by human labor, which is undesirable for large-scale applications.

Fortunately, by training Multi-modal Large Language Models (MLLMs) [245, 246, 247, 248, 249, 250, 251, 252, 253], which take advantage of the few-shot learning ability of Large Language Models (LLM) [254, 255, 256, 257, 258, 259, 260, 261, 262], they have manifested powerful capabilities on understanding visual information with language interpretations, and excelled at recognizing novel objects in multimodal tasks such as image captioning, visual