
# LIST OF FIGURES

- 6.1 AI is enhanced as more modalities are incorporated, so how can AI learns from novel modalities based on the ones it already know? 106
- 6.2 Learning framework of our OOM generalization. 111
- 6.3 Decomposition of $I(X^O, Y)$. 115
- 6.4 Two scenarios: (a) Semi-Supervised OOM Generalization and (b) Unsupervised OOM Generalization. 116
- 6.5 Connection effect on maximum mean discrepancy and accuracy across modalities. 122
- 6.6 Prediction accuracy of OOM data with modality disagreement and modalities agreement, respectively. (a) Before exploration. (b) After exploration. 123

# List of Tables

- 2.1 Comparison with typical OOD detections methods. Averaged AUROC (%) with standard deviations are computed over three independent trials. The best results are highlighted in bold. 21
- 2.2 Comparison with typical Open-set SSL methods. Averaged test accuracies (%) with standard deviations are computed over three independent trials. The best results are highlighted in bold. 22
- 2.3 Comparison with typical Open-set DA methods. Averaged test accuracies (%) with standard deviations are computed over three independent trials. The best results are highlighted in bold. 23
- 2.4 Ablation study on necessity of each module. 24
- 2.5 Averaged OOD scores on three applications. 28
- 2.6 Execution efficiency comparisons on three applications. 28
- 3.1 Quantitative comparisons on distribution-aware robust generalization setting. Averaged accuracy (%) with standard deviations is computed over three independent trials. 42
- 3.2 Quantitative comparisons on distribution-agnostic robust generalization setting. Averaged accuracy (%) with standard deviations are computed over three independent trials. 44
- 3.3 Quantitative comparisons on distribution-aware robust generalization setting on Snow corruption. Averaged accuracy (%) with standard deviations are computed over three independent trials. 45
- 3.4 Quantitative comparisons on distribution-agnostic robust generalization setting on snow corruption. Averaged accuracy (%) with standard deviations are computed over three independent trials.
- 3.5 Ablation study. "w/o data selection" denotes training without worst-case data selection, and "w/o sharp min" denotes training without sharpness minimization, which is the same as GroupDRO [125].
- 4.1 Comparison between OOD generalization methods and EVIL realization on some typical methods. Test accuracies on seven OOD generalization benchmarks from DomainBed. Best results and second best results are highlighted. † denotes results from [139].
- 4.2 Comparison between existing sparse invariant learning methods and EVIL varying sparsity levels. The test accuracies on seven OOD generalization benchmarks from DomainBed are provided. We highlight the best results and the second best results.
- 4.3 Results on additional invariant learning methods.
- 4.4 Results on various model architectures. ResNet50 is pre-trained on ImageNet, and other models are trained from scratch.
- 4.5 Comparison of SAM [137] and ERM under both ID and OOD situations on DomainBed.
- 4.6 Comparison of EVIL-SAM with other baseline methods on five datasets from DomainNet.
- 4.7 Performance on ImageNet, iWildCam, and FMoW using CLIP ViT-B/16 as backbone.
- 5.1 Classification accuracy (%) of baseline CLIP models and our method on 5 ID datasets and 5 OOD datasets. The baseline methods includes ViT-L from CLIP [225] and ViT-g from EVA [298], VQA, and Vanilla FT.
- 5.2 Classification accuracy (%) of baseline CLIP models and our method on 4 subsets of DomainBed datasets. The baseline methods include ViT-L from CLIP, ViT-g from EVA, VQA, and Vanilla FT.
- 5.3 Classification accuracy (%) of baseline CLIP models and our method with MMICL [280] and Otter [250] as the VLMs on 5 ID datasets and 5 OOD datasets. We compare the performance of our method, and the fine-tuned models supervised by our method with the baseline models, i.e., ViT-L from CLIP [225]. Fine-tuning with both MMICL and Otter improves the classification accuracy.
- 5.4 Classification accuracy (%) of baseline CLIP models and our method with MMICL [280] and Otter [250] as the VLMs on 4 subsets of DomainBase datasets, including VLCS, PACS, OfficeHome, and DomainNet. We compare the performance of our method and the fine-tuned models supervised by our method with the baseline models, i.e., ViT-L from CLIP [225]. Fine-tuning with both MMICL and Otter improves the classification accuracy.
- 5.5 Classification accuracy (%) of baseline CLIP models and our method on 5 ID datasets and 5 OOD datasets. We compare the performance of our method, and the fine-tuned models supervised by our method with the baseline models, including ResNet-50 and ViT-B/32. The supervisor MLLM is MMICL [280].
- 5.6 Classification accuracy (%) of baseline CLIP models and our method on 4 subsets of DomainBase datasets, including VLCS, PACS, OfficeHome, and DomainNet. We compare the performance of our method and the fine-tuned models supervised by our method with the baseline models, including ResNet-50 and ViT-B/32. The supervisor MLLM is MMICL [280].
- 5.7 Classification accuracy (%) of baseline CLIP models and our method with MMICL [280] as the VLM on 15 corruptions and 5 severities of ImageNet-C datasets. We compare the performance of our method and the fine-tuned models supervised by our method with the baseline models, i.e., ViT-L from CLIP [225]. The fine-tuned models with our MVT method have the best performance.
- 5.8 Performance comparison between MVT and CLIP on robustness against spurious correlation with Spurious dataset.
- 5.9 Class names for 12 chosen attributes.
- 5.10 Performance comparison between MVT and CLIP on recognizing fine-grained attributes using CelebA dataset. 97
- 5.11 Performance comparison between choosing noisy classes via transition matrix (MVT) and using Top-N predictions. 98
- 5.12 Comparison of classification accuracy (%) on 5 OOD datasets with Otter [250] and MMICL [280]. We compare the performance on CLIP ViT-L [225] backbone. 99
- 6.1 A comparison of different MML problems and their corresponding settings. 109
- 6.2 Classification performance comparison of different methods across multiple datasets with different OOM modalities. 120
- 6.3 Cross-modal retrieval performance comparison of different methods across multiple datasets with different OOM modalities. 121
- 6.4 Ablation study on various settings. 123

# CHAPTER 1
# Introduction

## 1.1 Background

Machine learning (ML) is one of the most effective approaches to Artificial Intelligence (AI), which leverages statistical tools to find, recognize, and utilize patterns in data, it has provided theoretical ground and practical tools that have led to the flourishing of AI. As a result, it has achieved tremendous success in a wide spectrum of applications, such as computer vision, natural language processing, speech recognition, autonomous driving, and robotics, significantly influencing human civilization.

The early AI revolution is led by deep neural networks [1], such as AlexNet [2], ResNet [3], and DenseNet [4], which have demonstrated that AI can achieve superior performance to human intelligence in visual recognition tasks. In 2017, Google introduced the Transformer architecture [5], which enabled models to handle vast amounts of text [6] as well as visual tokens [7] in parallel, thereby scaling up the magnitude of information processing. Based on such an architecture, it has become a common understanding that simply expanding the learning scale can always achieve improved performance, also known as the Scaling Law [8]. As a result, Large Language Models (LLMs) such as GPT [9], Llama [10], and Qwen [11] have been scaled-up to Bill of parameters, with many emergent capabilities In-Context Learning, Chain-of-Thought Reasoning, and Arithmetic Operation. Beyond language-only models, Multi-modal LLMs (MLLMs) that combine language and vision to allow advanced human-computer interaction have significantly increased their real-world capabilities, such as ChatGPT [12], Gemini [13], Claude [14], and DeepSeek [15]. Until now, most commercialized AI models are MLLMs and they play a vital role in boosting
