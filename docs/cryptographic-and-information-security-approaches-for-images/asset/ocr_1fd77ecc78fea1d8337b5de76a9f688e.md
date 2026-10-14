authentication for biometrics. The chapter uses fingerprint as a biometric modality to demonstrate several important case studies. With rapid growth in technology and digitization, personal data is available on the Internet. A strong user authentication mechanism [1] is required to prevent illegal access, e.g., a key based cryptographic system. A decryption key is used to establish user authenticity. However cryptographic keys are long and random, and they are difficult to memorize, e.g., 128 bits for the advanced encryption standard (AES) [2,3]. As a result, these keys are stored in a computer or a smart card and released based on alternative authentication mechanism (e.g., password). A password by ordinary users is very simple and it can be easily guessed or broken by dictionary attacks [4]. Thus, multimedia data protected by a cryptographic algorithm are only secure as a password.

Following are major problems with password based user authentication:

+   1. Some users store passwords at easy and accessible locations.
+   2. Most people use the same password across different applications. An impostor on finding this fact can access multiple applications with the same password.
+   3. In a multiuser case where the same password is available with many users it is very difficult to nail a culprit who caused security breach.

Many limitations of a password based mechanism indicate a need for a better and robust user authentication mechanism. As a result biometric based authentication [5–7] became popular. They establish an identity based on the physical and behavioral characteristics of an individual. Many countries, and recently even India, have started using biometrics like fingerprints and iris on a large scale through the Unique Identification Authority of India (UIDAI) [8]. Advantages of a biometric trait for human identification are as follows: (1) They are inherently more reliable as they cannot be lost or forgotten; (2) biometric traits are difficult to copy, share, and distribute; (3) they require presence of the person at point of data collection; and (4) they are difficult to forge.

A typical biometric system has four imporant modules. Their functions are as follows:

+   1. A sensor module captures biometric data. For example, a fingerprint sensor images ridge, minutiae and valley structure of a finger.
+   2. Feature extraction module which pulls out salient points from a sample. For example, position and orientation of minutiae points, local ridge and valley singularities in a fingerprint image.
+   3. Matcher module compares extracted and stored features to generate a matching score. For example, number of matching minutiae between the input and the stored fingerprints are determined and a score is reported. It also encapsulates a unit which rolls out identification decision.
+   4. System database module stores biometric templates of enrolled users.

Each module of a system is connected by a communication channel. Some channels are internal to a system e.g., channel between feature extractor and a matcher