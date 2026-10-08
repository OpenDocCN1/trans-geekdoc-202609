# Emotion Assessment Using Feature Fusion Classification Based on Physiological Data: Are We There Yet?

Patricia Bota 1\*, Chen Wang 2, Ana Fred 1 and Hugo Silva 1

*

+   1 Institute Superior Técnico (IST), Department of Bioengineering (DBE) and Instituto de Telecomunicações (IT), Ar. Rovisco Pais 1, Norte-Portiso 10, 10409 Lisbon, Portugal; afred@ilx.it.pt (A.F.); hsilva@it.pt (H.S.).

+   2 Key Library of Media Content Production Technology and Systems, Xinhua News Agency & Future Media Convergence Institute (FMCI), Xinhua Net, Jinyuan Building, No. 129 Xuanrummen West Street, Beijing, 100031; wangchem@cn

* Correspondence: patricia.bota@technico.ulisboa.pt

Received: 28 July 2020; Accepted: 19 August 2020; Published: 21 August 2020

**Abstract:** Emotion recognition based on physiological data classification has been a topic of growing interest for more than a decade. However, there is a lack of systematic analysis in literature regarding the selection of classifiers, sensor features, and range of expected accuracy, just a few limitations. In this work we evaluate emotion in terms of low/high arousal and valence classification through Supervised Learning (SL), Decision Fusion (DF) and Feature Fusion (FF) using multimodal physiological data, Electrocardiogram (ECG), Electrodermal Activity (EDA), Res (RIF), or Blood Pulse Volume (BVP). The main contribution of our work is a systematic study across five public datasets commonly in the Emotion Recognition (ER) state-of-the-art, namely: (1) Classification performance of ER marking across the datasets (in the arousal/valence space); (2) Summarising the ranges of classification accuracy reported across the literature; (3) Comparing the results for different classifiers, sensor modalities and feature set combinations for ER accuracy and f1-score; (4) Exploration of an extended feature set for each modality; (5) Systematic analysis of multimodal classification in DF and FF approaches. The experimental results showed that FF is the most competitive technique in results to to the state-of-the-art for the selected datasets.

**Keywords:** emotion recognition; physiological signals; machine learning; signal processing



Emotion is an integral part of human behaviour, exerting a powerful influence in mechanisms such as perception, attention, decision making and learning. Indeed, when humans tend to notice and remember not unnoticed, commonplace events that those ones evoke of joy, sorrow, pleasure, or pain [1]. Therefore, understanding emotional is crucial to understand human behaviour, cognition and decision making. The computer science field dedicated to the study of emotions is Affective Computing, which modern potential applications include, (1) automated driver assistance–e.g., through an alert system monitoring for drowsiness or unhealthy states potentially hindering driving; (2) healthcare–e.g., through wellness monitoring applications identifying causes of stress, anxiety, depression or chronic diseases; (3) adaptive learning–e.g., through a teaching application to adjust the content delivery rate and iterations according to the user enthusiasm and frustration