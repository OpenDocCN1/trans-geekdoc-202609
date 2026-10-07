# Elderly Fall Detection using Deep Learning Enabled Internet of Healthcare Things

Ahona Ghosh, Azaharuddin Saikh, Sriparna Saha and Indranil Sarkar

# 20.1 INTRODUCTION

Human falls are a common problem in the present day. As people age, their ability to move around declines, and falls become increasingly common, resulting in serious injuries or even death (Wang et al., 2020). An automated system for detecting risk factors of falling and alarm generation is beneficial since early identification and reporting of human falls could save lives. Different modalities in the existing literature have used to detect falls, like wearable sensors, floor-mounted sensors, imaging data, etc., (Poturi et al., 2019). However, these approaches are complex and expensive (Panda et al., 2019). Computer vision methods combined with deep learning models to classify visual data represented by images providing solutions for automated fall detection.

To identify falls using sensor readings, classification is a machine learning (ML) technique that seeks to detect falls automatically in real-time (Ragosti and Singh, 2021). Several taxonomies on fall monitoring can be found in the research reduce false alarms and increase the precision of fall detection and prediction systems. The loopholes acting as our motivations behind this research are summarized:

+   i. People sometimes seem to agree that sensor fusion offers a more reliable method for identifying sensor fall. In certain scenarios, the usage of several sensors may be complementary to one another, but it increases the computational complexity leading to the rejection of such applications in sensitive healthcare scenarios where time complexity is a deciding factor (Rana et al., 2019). Also, it is difficult to set thresholds to detect falls for wearable-based applications.

+   ii. Of the methods, particularly those relying on vision-based sensors, operate in offline mode since they are unable to function in real-time. Due to this constraint, most of them are effective in local areas. Attention to IoT platforms with cloud-based trends can address the challenge of building