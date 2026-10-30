# Trustworthiness in deepfake detection using explainability

Shetanshu Parmar and C. Mala

National Institute of Technology, Tiruchirappalli, India

# 8.1 INTRODUCTION

Deepfakes are a type of synthetic media that use deep learning to manipulate or generate images, videos or audio. They have become a hot topic in recent years due to their potential to be used for malicious purposes such as spreading fake news, propaganda and misinformation. The ability to generate realistic fake content presents a significant challenge for multimedia forensics, as it becomes increasingly difficult to determine the authenticity of digital media. It is important to discuss deepfakes from the perspective of multimedia forensics to understand the potential impact on society and to develop methods for detecting and combating the spread of false information [1]. Deepfakes are generally created by using Generative Adversarial Networks (GANs) and Autoencoders (AEs). There are various open-source tools available to create deepfakes. Some examples of deepfakes are shown in Figure 8.1, which are screenshots from an app used to create deepfakes. This shows the ease with which anyone with limited technical knowledge can also make deepfakes.

The increasing prevalence of deepfakes and their potential to spread misinformation has prompted the need for effective deepfake detection techniques. Various deepfake detection techniques can be classified into categories based on either the type of media involved or the methods used, such as conventional or machine learning and deep learning based. They can also be classified based on explainability from a forensics perspective. These categories are shown in Figure 8.2.

Detection can be based on the type of deepfake, whether audio, image, video, or both audio and video, or all three together. Generally, such combination is also called multimodal deepfake detection, which takes into account different media types. Videos can have frame-level detection where individual frames are processed [2] or entire video-level detection [3] is done.

Another way to distinguish is based on the techniques used, which can be conventional approaches or machine learning and deep learning-based