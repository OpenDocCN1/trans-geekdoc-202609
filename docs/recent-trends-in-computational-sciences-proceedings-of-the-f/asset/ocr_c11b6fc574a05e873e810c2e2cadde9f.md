# A review of tracking concept detection in machine learning

Nail Adeeb Ali Abdu
Information Technology Department, Faculty of Engineering & Computing, University of Science and Technology, Aden, Yemen

Khaled Omar Basulaim
Information Technology Engineering Department, Faculty of Engineering, University of Aden, Jemen
ORCID ID: 0000-0002-4519-1133

ABSTRACT: The availability of time streaming data has decreased dramatically in recent years. Since the last decade, there has been a growing interest in learning from real time data. While extracting significant information from data streams, online learning faces changes in distribution. Concept drifts hide data contexts that learning systems are unaware of. Using previous instances from the data stream, the classifier categorizes new instances. In this regard, it is obvious to have considerable methods to discover the similarity or diversity of the present streaming data compared to the buffered data. This paper was initiated to identify the constraints of the contemporary methods devised to handle the concept drift in data streams in relation to supervised learning, we also review and categorize the concept detectors with their key points. Eventually, the article presented observations provide decision boundary detection at improved levels and discussing research challenges and possible new research direction.

Keywords: concept drift, concept defense, detection methods

# 1 INTRODUCTION

Data mining approaches are used across multiple dynamic and real-time applications such as financial transactions, sensor networks, mobile communications, etc. However, the scalability of implementing these models in real-time applications which produce voluminous data in short periods of time is repeatedly challenged. The information generated in such applications is dynamic and forms data-streams with voluminous instances, storing information prior to processing is not feasible. Further, specific applications require instant and real-time solutions. One of the most prominent issues faced by researchers in the mining process is that data-streams in such instances can be non-stationary and concept drifts along the infinite length [1,2]. Due to the infinite and voluminous characteristics of these data-streams, storing information and utilizing the historical patterns for model training is not possible in the practical sense. Accordingly, new methods that can process the information through a single scan and employ limited resources such as storage and time are required. For a stream with significant learning, the order of observation determines how the data are organized. Therefore, it is necessary to identify any changes in data distribution. One of the biggest problems with data stream mining is this detection, as the quality of prediction is affected if the changes are not noticed. [3]