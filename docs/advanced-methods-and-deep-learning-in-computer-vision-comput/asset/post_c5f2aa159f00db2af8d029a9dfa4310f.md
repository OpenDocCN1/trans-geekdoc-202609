
![](img/fe161b7f6e96e35e7e853eece52c6dce_450_0.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_450_1.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_450_2.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_450_3.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_450_4.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_450_5.png)

(a) Samples at daytime with moving shadows

![](img/fe161b7f6e96e35e7e853eece52c6dce_450_6.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_450_7.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_450_8.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_450_9.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_450_10.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_450_11.png)

(b) Samples at daytime while the bird is moving

## FIGURE 12.14 Samples of Bahdanau attention weights visualized on input images.

We start by extracting relevant features (Section 12.5.1) from the raw frames in pixel space. The extracted features will be used as an input to the region proposal network and the prediction modules (Section 12.5.2). An energy function combines the prediction loss and the proposed regions (bounding boxes) to extract action tubes (Section 12.5.4) that are consistent when the object (or actor) performs actions that can transform their physical appearance. It is to be noted that these considerations can result in a large number of region proposals that require careful and robust selection but can yield higher chances of correct localization.

## 12.5.2 Hierarchical prediction stack

Similar to the approaches mentioned above, this framework learns a predictive function on the high-level features extracted by the encoder. A Long Short-Term Memory (LSTM) network is used to predict the next set of feature vectors, in a temporal sequence, given the encoded input and an internal model of the current event. The internal model effectively captures the spatial-temporal dynamics of the observed event. Similar to the previous attention model, the LSTM processes a set of feature vectors each time step, not a single feature vector. The spatial resolution of the feature maps is determined by the last convolution layer of the encoder.

The choice of an LSTM network is not arbitrary; while other approaches such as convolutional decoders (Jia et al., 2016) and mixture-of-network models (Vondrick et al., 2016) are viable alternatives for future prediction, we propose the use of recurrent networks for the following reasons. First, we want to model the temporal dynamics across all frames of the observed action (or event). Second, LSTMs can allow for multiple possible futures and hence will not average the outcomes of these possible futures, as can be the case with other prediction models. Imagine a sequence of frames I_a = (I_a^1, I_a^2, … I_a^n) corresponding to the activity a. Given the complex nature of videos such as those in instructional or sports domains, the next set of frames can be followed by frames of activity b or c with equal probability, given by I_b = (I_b^1, I_b^2,… I_b^m) and I_c = (I_c^1, I_c^2,… I_c^k) respectively. Using a fully connected or convolutional prediction unit is likely to result in the prediction of features that tend to be the average of the two activities a and b, i.e., I_avg^k = 1/2 (I_b^k + I_c^k) for the time k. This is not a desirable outcome because the predicted features can either be an unlikely outcome or, more probably, be outside the plausible manifold of representations. The use of recurrent networks such as RNNs and LSTMs allows for multiple futures that can be possible at time t + 1, conditioned upon the observation of frames until time t. Third, since we work with error-based localization, using LSTMs can ensure that the learning process aggregates the spatial-temporal error across time and can yield progressively better predictions, especially for actions of longer duration.

In contrast to the previous approaches, the prediction unit here consists of a stack of LSTMs. The output of one LSTM is used as the input to another LSTM. Each LSTM in the stack has its own parameters, defining a different internal model of the event based on its position in the hierarchy. This modification allows for modeling both spatial and temporal dependencies since each higher-level LSTM acts as a progressive decoder framework that captures the temporal dependencies captured by the lower-level LSTMs. The first LSTM captures the spatial dependency that is propagated up the prediction stack.

The updated hidden state of the first (bottom) LSTM layer (h_t^1) depends on the current observation f_t^S, the previous hidden state (h_{t-1}^1) and memory state (m_{t-1}^1). Each of the higher-level LSTMs at level l takes the output of the bottom LSTM’s output h_t^{l-1} and memory state m_t^{l-1} and can be defined as (h_t^l, m_t^l) = LSTM(h_{t-1}^l, h_t^{l-1}, m_t^{l-1}). Note this is different from a typical hierarchical LSTM model (Song et al., 2017) in that the higher LSTMs are impacted by the output of the lower level LSTMs at current time step, as opposed to that from the previous time step. Collectively, the event model $W_e$ is described by the learnable parameters and their respective biases from the hierarchical LSTM stack.

Hence, the top layer of the prediction stack acts as the decoder whose goal is to predict the next feature $f_{t+1}^S$ given all previous predictions $\hat{f}_1^S, \hat{f}_2^S, \dots \hat{f}_t^S$, an event model $W_e$ and the current observation $f_t^S$. We model this prediction function as a log-linear model characterized by

$\log p(\hat{f}_{t+1}^S | h_t^l) = \sum_{n=1}^{t} f(W_e, f_t^S) + \log Z(h_t)$
(12.9)

where $h_t^l$ is the hidden state of the $l$th level LSTM at time $t$ and $Z(h_t)$ is a normalization constant. The LSTM prediction stack acts as a generative process for anticipating future features.

## 12.5.3 Prediction loss

The attention map for this framework is extracted directly from the actual prediction loss (See Fig. 12.7) at the top of the prediction stack. The prediction loss is a factor of the quality of the predictions made and the relative spatial alignment of the prediction errors. The motion weighted loss from Eq. (12.8) is used to compute a weight $\alpha_{ij}$ associated with each spatial location $(i, j)$ in the predicted feature $\hat{f}_{t+1}^S$ as

$\alpha_{ij} = \frac{\exp(e_{ij})}{\sum_{m=1}^{w_k} \sum_{n=1}^{h_k} \exp(e_{mn})}$
(12.10)

where $e_{ij}$ represents the weighted prediction error at location $(i, j)$ (Eq. (12.8)). It can be considered to be a function $a(f_t^S, h_{t-1}^l)$ of the state of the top-most LSTM and the input feature $f_t^S$ at time $t$. The resulting matrix is an error-based attention map that allows us to localize the prediction error at a specific spatial location. And the average spatial error over time, $E(t)$, is used for temporal localization.

## 12.5.4 Action tubes extraction

The actions are extracted as tubes using an energy objective function that is minimized to ensure spatial and temporal consistency. The action localization module receives, as an input, a stream of bounding box proposals (several proposals per frame) and a stream of prediction loss maps (one per frame). An energy function is defined to extract coherent action tubes by filtering the proposals using the prediction loss map and returning the collection of proposals with a higher probability of action localization. This is achieved by assigning an energy term to each of the bounding box proposals $(\mathcal{B}_{it})$ at time $t$ and choosing the top $k$ bounding boxes with the least energy as our final proposals. The energy of a bounding box $\mathcal{B}_{it}$ is defined as

$E(\mathcal{B}_{it}) = w_{\alpha} \phi(\alpha_{ij}, \mathcal{B}_{it}) + w_t \delta(\mathcal{B}_{it}, \{\mathcal{B}_{j,t-1}\})$ 
(12.11)

where φ(·) is a function that returns a value characteristic of the distance between the bounding box center and location of the maximum error, δ(·) is a function that returns the minimum spatial distance between the current bounding box and the closest bounding box from the previous time step. The constants wα and w_t are scaling factors. Fig. 12.18 shows an example of extracted action tubes for a single activity in a stream of frames.

## 12.5.5 Results

### 12.5.5.1 Data

We use three publicly available datasets to evaluate our approach on the action localization task.

**UCF Sports** (Rodriguez et al., 2008) is an action localization dataset consisting of 10 classes of sports actions, such as skating and lifting, collected from sports broadcasts. It is an interesting dataset since it has a high concentration of distinct scenes and motions that make it challenging for localization and recognition. We use the splits (103 training and 47 testing videos) as defined in Lan et al. (2011) for evaluation.

**JHMDB** (Jhuang et al., 2013) is composed of 21 action classes and 928 trimmed videos. All videos are annotated with human-joints for every frame. The ground truth bounding box for the action localization task is chosen such that the box encompasses all the joints. This dataset offers several challenges, such as increasing amounts of background clutter, high interclass similarity, complex motion (including camera motion), and occluded objects of interest. We present all results as the average across all three splits.

**THUMOS'13** (Jiang et al., 2014) is a subset of the UCF-101 (Soomro et al., 2012) dataset, consisting of 24 classes and 3,207 videos. Ground truth bounding boxes are provided for each of the classes for the action localization task. It is also known as the **UCF-101-24** dataset. Following prior works (Li et al., 2018; Soomro and Shah, 2017), we perform the experiments and report results on the first split.

We also analyze the approach’s generalization ability on egocentric videos by evaluating it on the *unsupervised gaze prediction task*. There is ample evidence from cognitive psychology for a strong correlation between gaze points and action localization (Tipper et al., 1992). Hence, the gaze prediction task would be a reasonable measure of the generalization to action localization in egocentric videos. We evaluate the performance on the **GTEA Gaze** (Fathi et al., 2012) dataset, which consists of 17 sequences of tasks performed by 14 subjects, with each sequence lasting about 4 minutes. We use the official splits for the GTEA datasets as defined in prior works (Fathi et al., 2012).

### 12.5.5.2 Metrics and baselines

For the **action localization** task, we follow prior works (Li et al., 2018; Soomro and Shah, 2017) and report the mean average precision (mAP) at various overlap thresholds, obtained by computing the Intersection Over Union (IoU) of the predicted and ground truth bounding boxes. We also evaluate the quality of bounding box proposals by measuring the average, perframe IoU, and the bounding box *recall* at varying overlap ratios.

Since ours is an unsupervised approach, we obtain class labels by clustering the learned representations using the *k-means* algorithm. While more complicated clustering may yield
