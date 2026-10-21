# CHAPTER

# 9

# Visual tracking

Tracking in scenes containing multiple moving objects

Michael Felsberg^{a,b}

^{a}Computer Vision Laboratory, Department of Electrical Engineering, Linköping University, Linköping, Sweden ^{b}School of Engineering, University of KwaZulu-Natal, Durban, South Africa

# CHAPTER POINTS

+   - Visual object tracking.
+   - Discriminative tracking approaches.
+   - Correlation filters.
+   - Deep features.
+   - Deep learning of tracking.
+   - Video object segmentation.
+   - Discriminative segmentation.

# 9.1 Introduction

Tracking is a highly ambiguous term, and even for visual tracking, many different interpretations exist. Therefore, this chapter starts with a thorough definition of the problem addressed to delineate this chapter from other interpretations and to make all assumptions explicit.

# 9.1.1 Problem definition

In this chapter, we will consider the problem of generic visual tracking, in the sense as defined in the visual object tracking (VOT) challenges 2013–2020 (Kristan et al., 2013, 2015a,b, 2016, 2017, 2019,b, 2020), which also coincides with the online tracking benchmark (OTB) definition (Wu et al., 2013). The tracking is performed in the image domain and no prior knowledge about object classes is available: generic means class agnostic.