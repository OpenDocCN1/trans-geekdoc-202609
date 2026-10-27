
## 15 Health Analysis by Digital Doctor Using Deep Neural Network

Amruta Khot  
Walchand College of Engineering

## Contents

- 15.1 Introduction ........................................................ 254
- 15.2 Overview and Problem Statement ........................................................ 254
- 15.2.1 Motivation ........................................................ 255
- 15.2.2 Contributions of This Work ........................................................ 256
- 15.3 Terminology ........................................................ 258
- 15.3.1 Natural Language Understanding ........................................................ 258
- 15.4 Objectives ........................................................ 259
- 15.4.1 To Develop a Video-Calling Web Application ........................................................ 259
- 15.4.2 To Develop a Video-Calling Web Application ........................................................ 259
- 15.4.3 To Implement Feature Extraction so as to Extract the Patient’s Details to Develop a Video-Calling Web Application ........................................................ 260
- 15.4.4 To Build a Recommender System Similar for Patients Based on the Features Extracted ........................................................ 260
- 15.5 Proposed Method/Algorithm ........................................................ 260
- 15.5.1 Problem Definition ........................................................ 261
- 15.5.2 Proposed Idea/System ........................................................ 261
- 15.6 System Architecture ........................................................ 262
- 15.6.1 System Analysis and Design ........................................................ 263
- 15.6.2 Requirement Specification ........................................................ 263
- 15.6.3 Design and Test Steps ........................................................ 264
- 15.6.4 Algorithms and Pseudo Code ........................................................ 265
- 15.7 Performance Study ........................................................ 266
- 15.7.1 Implementation ........................................................ 266
- 15.7.2 Video Calling ........................................................ 267
- 15.7.3 Speech to Text ........................................................ 267
- 15.7.4 NLP ........................................................ 268
- 15.7.5 Recommender System ........................................................ 270
- 15.8 Results and Analysis ........................................................ 270
- 15.8.1 Summary of Performance Study ........................................................ 272
- 15.9 Conclusions and Future Work ........................................................ 273
- References ........................................................ 274

### 15.1 INTRODUCTION

Technology is improving its applications and the way we communicate with the rest of the world constantly. An efficient health-care system is important to a country’s development, economy and industrialization. Health care is also an important determinant in ensuring the general physical and mental health and well-being of all the people around the globe. Medical records have to be stored appropriately. Also, all the prescriptions have to be stored properly. Thus, a developed application stores patients’ past medical interactions in summary form. Also, it stores the prescriptions given by the doctor digitally.

Here, a developed video-calling web application enables digital interaction between the doctor and the patient using WebRTC (Web Real-Time Communications). WebRTC enables easy communication with transferring real-time audio, video and data in web. WebRTC is an open-source application programming interface (API) that enables peer-to-peer communication. Speech during the video call is converted into text in real time using Google Cloud Speech API. Google Cloud uses deep learning method to convert speech to text. Streaming speech-to-text API recognition is designed to capture the audio in real time and convert that audio to text, i.e. capturing and recognition of audio is done in real time [1].

Spoken language understanding refers to making machines understand human speech. It refers to targeted understanding for machines by converting inputs from the user into task-specific semantic representation. Slot filling is a technique in semantic parsing in spoken language understanding. It is a classification problem where every word from sentence has label. Recurrent neural network (RNN) is primarily built to implement slot-filling technique. Slot filling enables understanding the semantic context of words and filling in the slots to extract semantic concepts. Thus, for slot-filling technique, input is sequence of words that gives output as sequence labels of those words or slots filled for each corresponding word. Goal of our work is to find slot sequence for word sequence which has maximum posterior probability. The labels help to extract important keywords. Extracted keywords are used to generate summarized report for the patients. This report is stored in database thus enabling the patient to view report whenever required.

Recommendation system is used to display with similar symptoms of patients’ health condition to doctor and also medicines prescribed to those patients. This enables the doctors to view what medicines were prescribed to patients earlier and thus doctor can prescribe appropriate medicines. Content-based recommendation system has been developed to recommend similar patients to doctor. Content-based systems hypothesize that if a patient has been prescribed a medicine in past, it may also be recommended to other similar patients in future. The designed module is content-based retrieval system that helps in recommendation that work on data given by the user explicitly or implicitly. Input to recommendation system is report generated of patient.

### 15.2 OVERVIEW AND PROBLEM STATEMENT

Academic study of natural language is a new discipline in science today. Doctors have to treat diseases as well as the patients, and thus language is an essential part of science. There are deficiencies in record keeping process of patients. Getting appointments and visiting doctor is tumultuous process. Critical information has to be stored properly. This information can further be required to perform diagnosis in future interactions during follow-ups. Thus, information about the previous interactions has to be stored safely. However, diagnosis information is stored by the patient in paper format. Thus, there is risk of losing the information due to various reasons.

Digital interactions can reduce the hassle of visiting the hospitals every time especially regular follow-ups. The patients need to meticulously maintain the prescriptions in paper format. The doctor should also have the details of the patient so that the doctor can review them whenever necessary. Many a time, patients may have to switch from one doctor to another. So, it becomes inconvenient for doctor as well as patient as doctor does not know the history of every patient. Video-calling web application will help patients and doctors to interact with each other. Speech extracted from the video conversations is converted into text in real time. Thus, conversations are converted into text format. Clinical information from the narrative medical interactions is extracted and saved for the patient. Thus, concepts will be extracted from the conversations. It would help to classify the relationships between the concepts (for example, symptoms and duration of the symptoms) and identify the nature of assertions about the concepts (for example, assertive questions such as does patient have headache and answer for this can be yes or no only). This keyword or information extraction will be stored for the patient so that it will always be available to him.

Numerous medications are available for a particular disease or symptom. However, not all medications work for all the patients. Thus, doctor will be recommended patients, similar to the current patient based on information extracted and also the medications or prescriptions provided to those patients. Doctor can then prescribe medicines to the patients accordingly by referring the similar patients. Also, these prescriptions will be available on patients’ profile which will save the patients’ efforts of saving the prescriptions in paper format.

#### 15.2.1 MOTIVATION

Medical dialogues between doctor and patient play a crucial part in medical diagnosis. Studies have shown that 80% of diagnostic assessments are based on the medical interactions. Also, there have been tremendous advancements in medical domain.

Significant amount of time of patients is spent in visiting the hospitals for normal routine follow-up. Also, there may be a case when the doctor is not available. Thus, patients have to wait for the doctors to get back in town. Hence, to make significant use of technological advancements, a developed web application will enable the patients to reach out to the doctors easily and conveniently.

Unprecedented amount of information relating to patient’s symptoms, diseases and treatments is produced through the interactions. However, not all information can be considered to be significant. Natural language processing (NLP) can help in processing that enormous information and extracting only the relevant information from the conversations. Thus, audio from the video interactions is converted to text in real time and processed。
