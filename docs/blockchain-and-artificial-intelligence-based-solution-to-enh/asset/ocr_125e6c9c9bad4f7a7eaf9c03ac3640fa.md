identified. Also, this model identifies both trolls and real users, like user @JackPosobiec and troll @TEN GOP, involved in the spread of disinformation.

Another study (Alhazbi, 2020) was based on features from over 500 posts, needed to classify the account if it is a troll or not. Because few posts are needed, disinformation will be detected in real time. Moreover, this general model is capable of identify these without the need to analyze the contents of their post, which requires using natural language processing that will vary from one language to another.

All those studies proposed detecting tools to eliminate disinformation from trolls and bots. It's less effective than preventive measures though.

# 7.6.3 DEEPFAKES’ AUTHENTICATION AND DETECTION

We summarized a short review of work on deepfakes. One study is based on an authentication method and the two others are detection methods.

The goal of authenticated video or image is to track the provenance and the history of digital content to its source. It proves that the video or image is authentic, and not fake. It is what we call “blockchain technology.” Cryptocurrency is based on

TABLE 7.2
Proposed Approaches on Authenticating and Detecting Deepfakes 2018–2019
| no | 1 | 2 | 3 |
|---|---|---|---|n| Title of the study | Combating deepfake videos using blockchain and smart contracts, 2019 (Hasan & Salah, 2019) | Exposing Deepfakes Using Inconsistent Heads, 2019 (Yang et al., 2019) | Deepfake video detection using recurrent neural networks, 2018 (Güera & Delp, 2018) |
| Objective | Decentralized Proof of Authenticity system using the technology blockchain contracts | Solution for the detection of fake video | Solution for the detection of fake video |
| Dataset | No tests | 241 real images and 252 deepfakes 2019 | 600 videos that are half fakes |
| Period of data collection | NA | | 2018 |
| Features | NA | Support Vector Machines (SVM)-method to detect deepfake videos: comparing face landmarks between the real images and fake images | Two-stage analysis composed of a CNN to extract features and Recurrent Network (RNN) to capture inconsistencies |
| Result Advantages | NA Authentication of source. No deepfakes | 84% of detection Features extracted from 68 landmarks of the facial region of 3D head | 97% of detection With less than 2 seconds of video, the solution can accurately predict fake video |