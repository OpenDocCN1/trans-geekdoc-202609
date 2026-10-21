to human-centered sensing. This happens in several ways: Systems should adapt to the environment that is shaped for humans – and since vision is humans’ dominating sense involved in about 80% of our perception, learning, cognition, and activities (Ripley and Politzer, 2010), they need visual sensors. There are many examples for such environments, for instance, in the traffic scenario the highway code defines many signs and symbols that guide the driver visually. Also systems that share their workspace with humans for interaction and collaboration need visual capabilities. The appearance is a strong cue for behavior as well as intentions and humans use this actively by communicating in terms of, e.g., gestures. Finally, in order to be capable to predict human actions, their perception needs to be predicted as well – which is mostly based on vision.

# 9.1.4 Historical development

Many of the older approaches to visual tracking go back to problems within augmented reality, where visualization and sensing are combined into the same coordinate system to generate a mixed reality environment. Tracking is important here for two purposes: the relative head pose in the scene (Neumann et al., 1999) and the pose of moving objects (Neumann and Park, 1998).

Some major steps in the history of visual tracking as well as key works of the author are

+   - 1981: Lucas-Kanade algorithm (Lucas and Kanade, 1981)
+   - 1984: Phase-only matched filter (Horner and Gianino, 1984)
+   - 1994: “Tracking is a solved problem” (from the presentation of Shi and Tomasi, 1994)
+   - 1998: Phase only matched filters and equivariances (Felsberg, 1998)
+   - 2004: “Lucas-Kanade 20 Years On: A Unifying Framework” (Baker and Matthews, 2004)
+   - 2007: MATRIS project: L1-tracker and covariance (Skoglund and Felsberg, 2007)
+   - 2013: New tracking challenges OTB (Wu et al., 2013), VOT (Kristan et al., 2013), and a generative holistic tracker (Felsberg, 2013)
+   - 2014: Discriminative tracker (DSST) winner in VOT2014 (Danelljan et al., 2014a; Kristan et al., 2015a)
+   - 2018: Discriminative holistic trackers dominate VOT2018 with 75% (Kristan et al., 2019)
+   - 2020: Siamese trackers and segmentation methods gain importance (Kristan et al., 2020).

In the subsequent sections, several major developments during this period of 40 years are described in some detail, with a particular focus on discriminative and learning-based methods.

# 9.2 Template-based methods

Before looking deeper into the learning-based methods, we will briefly discuss relevant methods that build entirely on the initial annotated bounding-box, often called the template.