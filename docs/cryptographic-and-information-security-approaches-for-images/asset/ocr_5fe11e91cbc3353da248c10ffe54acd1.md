frames are removed. Therefore, by detecting (and quantifying) the degree of change in the Block Artifact Strength (BAS) of the recompressed video as compared to when the video was singly-compressed, presence of frame-removal forgeries can be revealed.

# Variation of Prediction Footprint:

The authors in Vázquez-Padín et al. (2012) proposed a novel and robust forensic feature called Variation of Prediction Footprint (VPF), which demonstrably appears in only those P-frames of recompressed video sequences that were I-frames when this video was first compressed. VPF was later used for the detection of recompression and inter-frame tampering in Labartino et al. (2013), Gironi et al. (2014), Sitara and Mehtre (2017).

# 3. Motion and Brightness Features Based Techniques

Although recompression artifacts can often provide valuable clues regarding the processing history of the video in question, to state that their presence is always indicative of tampering would be rather unwise, simply because perfectly authentic digital content that we come across in our day to day lives has often undergone multiple post-production compressions. All the tamper detection techniques we reviewed in the previous section relied much too heavily on the forensic evidence offered by recompression artifacts, and consequently failed to differentiate tampered videos from harmlessly recompressed ones.

Since recompression artifacts do not offer conclusive evidence of tampering in realistic forgery scenarios, alternative forensic artifacts have to be relied upon; these are discussed next.

# Motion Compensated Edge Artifacts (MCEA):

MCEAs are unique artifacts that have been shown to appear in videos that are compressed with the help of coding algorithms that utilize block based motion-compensated frame prediction (such as MPEG-2). During motion-compensated frame prediction, successive video frames are decoded with the help of previously decoded frames, which causes consecutive video frames to become dependent on one another. Inter-frame forgeries destroy such dependencies or correlations, thereby causing the existent block boundary artifacts in the video frames to become even more prominent. This increase in block boundary artifacts, which is referred to as MCEA, can help detect the presence of inter-frame forgeries. MCEAs have been used as discriminating features for the detection of videos suffering from frame-removal forgeries in Su et al. (2009), Dong et al. (2012).

# Motion/Prediction Residue:

At the time of its creation, a video exhibits an enormous amount of temporal redundancy, which the video encoder takes advantage of by predicting certain frames from other frames. Prediction residual or prediction error, which is the difference between the original video frame and frame predicted by the video encoder, follows a particular pattern for a series of consecutive frames in a natural video. These patterns are established when the video is first acquired, compressed, and saved. If this video