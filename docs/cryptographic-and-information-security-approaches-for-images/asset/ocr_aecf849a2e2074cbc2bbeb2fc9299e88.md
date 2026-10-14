![](bbox=[0.22, 0.12, 0.78, 0.42])

Figure 24.2 Classifications of tampering and detection techniques: (a) common image tampering techniques, classified as copy-move and splicing; (b) tampering detection techniques classified as active and passive based on the availability of prior-image information.

Image tampering detection techniques are plenty and are broadly classified into two based on of the availability of prior image information: active and passive. Active methods are those which use prior image information for detection of tampering. Passive or blind methods do not use prior image information. Considering the infeasibility of active techniques in most real crime investigation scenarios, blind techniques have gained more attention. These techniques do not depend on the availability of prior image information. Blind methods attempt to identify certain properties which are intrinsic to the test file, the variation of which may indicate a tampering activity (Figure 24.2).

Our focus in this chapter is on copy-move and splicing as they are the most common forms of image tampering techniques. We also discuss the various classification of them based on the detection mechanism like keypoint based, texture based, etc. A special section is devoted to the common copy-move detection pipeline. The latest works in image tampering detection using deep learning and big data are discussed, followed by suggestions on the future directions in this area.

# 24.2 Copy-move Forgery Detection

Copy-move forgery/tampering detection essentially involves looking for identical regions in the image based on some kind of matching. Based on this, we may generalize the steps in a copy-move tampering detection system as discussed below.