# Algorithm 2: Extracted audio

**Input:** HD videos  
**Output:** Extracted audio from every video for audio processing having transcript and audio feature.

+   1. Import moviepy.editor.  
+   2. Read mp4 file with videoclip = VideoFileClip(<path>)  
+   3. Get wav file from mp4 using function audioclip = videoclip.audio  
+   4. Repeat step 2 and 3 for all videos.

# EXPERIMENTAL ANALYSIS

The proposed DBF method utilizes a straightforward weighted average approach to fusion but also highlights how performance may be enhanced by the use of sophisticated ensemble techniques, such as stacking, to discover the best values for fusion weights at the end of the process. In order for deep audio networks to acquire more informative representations of sound, they need to be put through their paces. Within our DBF framework, we can enhance retrieval accuracy by combining multiple models into a single one.

The pseudocode for the moment localization and content-based video retrieval is shown in Figure 3.

*Figure 3. Pseudocode of deep bimodal fusion*

```
```python
# Preprocessing
video_frames = preprocess_video_frames(video)
audio_signal = preprocess_audio_signal(audio)
# Feature Extraction
visual_features = extract_visual_features(video_frames)
audio_features = extract_audio_features(audio_signal)
# Bimodal Fusion
bimodal_features = bimodal_fusion(visual_features, audio_features)
# Moment Localization
moments = []
for t in range(total_frames):
    current_feature = bimodal_features[t]
    moment_score = evaluate_moment_score(current_feature)
    if moment_score > threshold:
        moments.append(t)
# Content-based Retrieval
retrieved_videos = []
for video in video_database:
    visual_features = extract_visual_features(video)
    audio_features = extract_audio_features(video)
    bimodal_features = bimodal_fusion(visual_features, audio_features)
    similarity_score = compute_similarity_score(bimodal_features, query_features)
    if similarity_score > retrieval_threshold:
        retrieved_videos.append(video)
# Evaluation
precision, recall, f1_score = evaluate_performance(retrieved_videos, ground_truth)
```
```

This pseudocode assumes that the video data is preprocessed, visual and audio features are extracted, and bimodal fusion is performed using a deep neural network architecture. The moment localization step involves evaluating the moment score for each frame, and if the score is above a certain threshold, the frame is considered to be part of a relevant moment. Content-based retrieval involves computing the