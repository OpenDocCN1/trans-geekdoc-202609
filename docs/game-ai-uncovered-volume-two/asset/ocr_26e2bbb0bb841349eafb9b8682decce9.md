recommender system. The model suggests the next n most likely shot configurations of a scene given the previous shot from which the user can select. Before this, it is important to declare some terminology used in cinematography.

# 12.3.1 Movie

A film/movie/video is defined as an ordered sequence of scenes, composed of shots, which are themselves composed of individual images (frames).

# 12.3.2 SCENE

A scene is a notional collection of shots across a specific aspect of the story. For example, a scene where two characters are drinking and talking in a bar, where the scene has multiple different viewpoints expressed in different shots, but the scene itself encompasses all the shots that make up this phase of the story.

# 12.3.3 SHOT

A shot is simply the sequence of images recorded via a given camera for a number of frames. Typically, this involves choices like camera lens, lighting, scene composition, and framing. You can think of the shot as the main unit of editing, with shot length in frames and shot timing and position in a scene being important attributes. An important feature of a shot is that the composition expressed within the sequence of frames can change over time. For the purposes of this discussion, everything will be discussed as though it is relative to the camera. For example, a character can enter the shot from the right (of the camera) and exit to the left (of the camera) over the duration of a shot.

# 12.3.4 The PROSE Cinematography Language

A cinematography domain-specific language called PROSE (Ronfard et al., 2015) is used to define a given scene and set of shot transitions. PROSE defines a context-free grammar (CFG), which allows the definition of a given sequence of shots with respect to a given camera. Rather than give specifics like lens specifications and camera fields of view, PROSE suggests a limited set of shot types and transitions.

# 12.3.5 The Movie Net Dataset

For a ML model to learn something, it typically must be given a lot of examples of the things it is trying to learn the distribution of. In this case, an existing dataset can be adopted and extended, which has collated information from 1,100 movies. The Movie Net dataset (Huang et al., 2020) and associated codebase can be accessed via the github (https://movienet.github.io/). The dataset itself consists of movies highly rated on IMDB with information on scene and shot start–end frame boundaries, bounding box detections for individual actors, subtitle and script information that is temporally aligned with the shot detection, and more.