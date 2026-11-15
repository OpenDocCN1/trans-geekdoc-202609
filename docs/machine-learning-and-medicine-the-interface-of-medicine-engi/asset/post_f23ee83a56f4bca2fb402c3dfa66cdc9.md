
electronic health records analysis, SHAP has been instrumental in enhancing transparency and interpretability in healthcare AI.

Furthermore, interpretability techniques like LIME (Local Interpretable Model-agnostic Explanations) and LORE (Local Rule-Based Explanations) have seen wide adoption in the healthcare sector [1,23]. LIME’s approach to generating local explanations by approximating complex model decision boundaries complements LORE’s use of a genetic algorithm to create a synthetic neighborhood for a local interpretable predictor. This predictor, in turn, facilitates the generation of meaningful explanations that include decision rules and counterfactual scenarios, thereby illuminating the influence of specific factors on outcomes [1]. These techniques have been applied to a range of healthcare domains, from disease prediction to medical imaging and clinical decision support, demonstrating their versatility and impact.

Caruana et al.’s work on developing intelligible models for healthcare contexts, such as pneumonia risk prediction and hospital readmission, further highlights the progress in creating interpretable AI systems for clinical use [24]. By employing decision trees and rule-based models, their research has contributed significantly to the field, enhancing both the transparency and the adoption of AI in clinical practice.

The integration of domain knowledge and expert input into XAI approaches marks an evolving research direction, promising to enrich interpretability and align AI decision-making processes with established medical practices. This blend of technical innovation and domain expertise is crucial for advancing the application of local XAI methods in healthcare, ensuring that AI-assisted decision making is both transparent and grounded in clinical realities [25].

In conclusion, advancements in XAI for healthcare, particularly the focus on local methods, highlight a growing commitment to enhancing AI model transparency and interpretability. These efforts underscore the field’s progress towards developing AI systems that are not only technically proficient but also understandable and trustworthy for healthcare professionals and patients alike, fostering improved decision making, patient care, and adherence to regulatory standards.

## 3. Methodology

Before discussing the specific methodologies supporting our research, it is crucial to contextualize our work within the broader landscape of artificial intelligence technologies, particularly deep learning. Deep learning [26], a subset of machine learning, has emerged as a transformative force in various domains, including healthcare. It refers to the development of algorithms that can learn and make decisions or predictions based on data. These algorithms, known as neural networks, are designed to mimic the human brain’s architecture and function, processing vast numbers of data to identify patterns and insights that are not immediately apparent to human observers.

As outlined in the seminal work [27], deep learning involves multi-layered neural networks that learn and make inferences from data in a way that captures the complexity and subtlety of the information being processed. This capability makes deep learning particularly valuable in healthcare, where the ability to analyze and interpret complex medical data can lead to more accurate diagnoses, personalized treatment plans, and, ultimately, better patient outcomes.

The key methodologies used in the project are related to the LORE method, introduced by Guidotti et al. [1]. LORE is a powerful framework for generating local and interpretable explanations for machine learning models. LORE utilizes a genetic algorithm to create a synthetic neighborhood, which serves as the basis for training a local interpretable predictor. This predictor captures the underlying logic of the model’s decision-making process, enabling the derivation of meaningful explanations.

One of the key characteristics of LORE is its ability to provide transparent and understandable explanations for individual predictions. By focusing on local interpretability, LORE aims to explain the reasoning behind a specific prediction rather than the overall behavior of the model. This makes it particularly useful in situations where interpretability at the instance level is crucial, such as in healthcare and finance.

The explanations consist of two main components. First, a decision rule is derived from the logic of the local interpretable predictor. This decision rule sheds light on the factors that influenced the model's decision, providing insights into the important features and their corresponding weights. This information helps in understanding the key drivers behind the prediction. Additionally, LORE produces a set of counterfactual rules as part of the explanation. These counterfactual rules suggest modifications to the instance's features that would lead to a different outcome. By providing actionable suggestions for changing the input variables, LORE enables users to explore what-if scenarios and understand how small changes can influence the model's predictions.

The availability of the LORE framework, along with the accompanying code (https://github.com/riccotti/LORE, accessed on 14 March 2024), facilitates its adoption and implementation in various domains. In the next sections, different research projects are described. They leverage over the LORE methodology from different points of view.

## Detailed LORE Framework

LORE operates on the principle of providing instance-specific explanations by creating a local, interpretable model around a prediction of interest. It begins by selecting an instance for which an explanation is desired. Then, it generates a synthetic dataset that mimics the locality of the original instance through a genetic algorithm. This local dataset is used to train a simple, interpretable model, such as a decision tree, which serves to approximate the behavior of the complex model near the instance. The explanation is then derived from this interpretable model in the form of rules, which highlight the decision-making process for the specific instance.

- **Selection of Target Instance**: Choose the specific prediction or instance that requires explanation.
- **Synthetic Neighborhood Generation**: Utilize a genetic algorithm to generate a synthetic dataset that represents the local decision boundary around the target instance.
- **Training of Interpretable Model**: Train a simple model, like a decision tree, on this synthetic dataset to capture the local decision logic of the complex model.
- **Derivation of Explanation**: Extract rules from the interpretable model that explain the prediction of the target instance. These rules offer insights into which features and conditions influence the decision.

LORE's ability to provide clear, case-specific explanations makes it highly valuable in healthcare settings, where understanding the rationale behind AI-driven diagnostic or prognostic predictions is crucial. For instance, LORE has been applied to interpret AI decisions in predicting patient outcomes, understanding disease progression, and personalizing treatment plans. Its interpretability supports clinical decision making, enhances trust among medical practitioners, and facilitates patient communication.

LORE distinguishes itself from other XAI methods like LIME or SHAP primarily through its emphasis on generating a synthetic neighborhood around an instance. This approach allows LORE to provide highly localized explanations that are directly relevant to the specific case at hand. While LIME also focuses on local interpretability, it approximates the model's decision boundary linearly, which might not capture complex nonlinear relationships as effectively as LORE's method. SHAP, on the other hand, provides a global interpretation as assigning importance values to features based on their contribution to the model's output. LORE's advantage lies in its detailed, rule-based explanations that can be more intuitively understood by healthcare professionals for specific patient cases.

## 4. XAI Frameworks for Healthcare

### 4.1. DoctorXAI

An ontology-based approach, as described in “Doctor XAI: an ontology-based approach to black-box sequential data classification explanations” [28], aims to provide
