data) [25]. Its wide range of applications include object detection and tracking and facial recognition.
Figure 19.1 represents the data points plotted for a hand gesture with each data point having a corresponding integer for distinguishing each points and storing the data points to learn the position of the hand during each sign.

![](bbox=[0.175, 0.205, 0.745, 0.615])

Figure 19.1 Media pipeline graph.

# Key Components of Mediapipe:

+   1. Graphs: Mediapipe graph is implemented using a Directed Acyclic Graph (DAG), which represents the processing pipeline. The graph consists of a collection of nodes that perform operations on an input and produce an output data. The connection of the nodes can give the flow of data through the system.

+   2. Nodes: These nodes are the building blocks of the Mediapipe graph. Every single node represents an input operation such as video decoding, image filtering, and feature extraction. Nodes can consume and produce data by utilizing the input and output streams.