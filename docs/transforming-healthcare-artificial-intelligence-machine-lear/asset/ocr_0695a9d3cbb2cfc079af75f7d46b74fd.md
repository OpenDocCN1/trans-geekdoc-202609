on construction sites in the event of safety mishaps. Based on statistical
analyses, the most frequent causes of accidents are interactions with mov-
objects and incidents involving machinery. In addition, these figures
show that workplace accidents not only injure but also cost large
salary losses and decreased productivity for businesses. Utilizing cameras to
capture images of construction sites, the existing methods for PPE detection
only recognize helmets and vests; this project mainly focuses on the accu-
racy of model, as many existing projects do not produce 80%, and
we add boots for detection [2]. Health management agencies in many
countries require PPE equipment, as safety helmets, reflective vests,
boots, to safeguard the personal safety of workers since it plays a sign-
ificant role in accident prevention. As a result, monitoring employees who
are wearing PPE has become crucial for safety management. Conventional
techniques are unable to identify infractions in real time, which results in
mishapsaps, injuries, and monetary losses [3].

# 9.2 LITERATURE SURVEY

Gallo et al. [3] proposed system for real-time PPE detection that uses edge
computing to analyze video streams locally on an embedded Raspberry Pi
with an Intel Compute Stick 2, reducing reliance on cloud-based
solutions. It evaluates pre-trained convolutional neural networks for
detesting helmets, vests, and gloves, comparing their performance and
latency. The system ensures efficiency, reliability, and privacy by
aavoiding continuous cloud transmission.

The MAR-YOLO model enhances PPE detection by improving on
YOLO8s with a re-parameterizable backbone, R-C2F and RASFF mod-
for better speed and accuracy. Using a custom dataset of 2,750 images,
Bao et al. found that MAR-YOLO achieved a 6.7% improvement in AP50nna a 10.2% improvement in AP75, with a mean average precision (mAP)
of 74.7%, outperforming other lightweight models by 4.95% [4].

Liu Yepeng et al.'s improves PPE identification by developing a
unique dataset for luminous helmets and hard hats and refining the
YOLO5 model. The enhanced AL-YOLO5 model achieves a 0.4 mAP
implementation and a 0.9 AP increase in data-limited categories by
adding an attention mechanism and an advanced loss function. This greatly
lower false detections and improves the handling of overlapping frames [5].