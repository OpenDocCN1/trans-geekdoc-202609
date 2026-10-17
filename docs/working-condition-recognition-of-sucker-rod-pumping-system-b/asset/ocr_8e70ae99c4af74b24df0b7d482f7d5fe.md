Similar to the construction of 4S-TFS and 4S-TFSM, the dynamometer card curves in Fig. 3(a) and (b) can also be split into 1, 2 and 8 segments to create the 1S-TFS, 2S-TFS, and 8S-TFS in Fig. 3(c), which in turn form the 1S-TFSM, 2S-TFSM and 8S-TFSM in Fig. 3(e), respectively. Section 4.2 of the experimental section contains the related experimental results.

# 3.3. Working condition recognition framework of SRPS

With the extraction of 4S-TFSM features, CNNs can be used for working condition identification of SRPS. The framework of the 4S-TFSM-CNN method proposed in this paper is shown in Fig. 4, and the general steps are summarized as follows.

+   1) Data collection. The data are measured by dynamometer sensors attached to the pumping rods and sent to the data center via wireless networks. The displacement data are obtained through the acceleration sensor by quadratic integration. Based on the collected displacement and load data, the DC can be generated. The dynamometer card reflects the running process of the sucker rod.
+   2) 4S-TFS feature extraction. The proposed 4S-TFS feature extraction method is employed to extract the time-frequency-domain features of each dynamometer card, and the data compression is performed at the same time as feature extraction, which effectively reduces the dimensionality of the data and solve the issue of high computational complexity caused by the DC as a two-dimensional image input to the neural network.
+   3) 4S-TFSM construction. The collected 4S-TFS data generated from multiple DCs are used to construct 4S-TFSM by relative normalization and matrix calculation, which can enhance the feature differences between different working conditions and solve the heterogeneity problem of training samples.
+   4) Working condition recognition. The optimal selection of features is accomplished by a specifically designed CNN model to automatically select 4S-TFSM features that are sensitive to the category of working conditions. Specifically, the dataset is

divided into a training set and a test set according to a certain ratio. The CNN model is used to obtain optimal parameters sensitive to task variation by the training set, and the test set is used for working conditions recognition.

# 4. Experimental evaluation

In this part, Section 4.1 describes the data collection and processing process. Section 4.2 presents the hyperparameter selection and performance evaluation of the 4S-TFSM-CNN method proposed in this paper. Section 4.3 compares the proposed 4S-TFSM-CNN and 4S-TFS-CNN with the traditional method image-CNN in four aspects of classification accuracy, model parametric number, algorithm complexity and training time to verify the effectiveness of the innovation points presented in this paper. Section 4.4 discusses the negative impact of the heterogeneity of training samples on the actual working condition recognition, and explains the rationality of the innovation point by comparing 4S-TFSM-CNN with some traditional machine learning and deep learning methods.

# 4.1. Data collection and processing

To demonstrate the effectiveness and performance of the proposed diagnostic method, more than 100,000 DCs were collected from an oilfield in northern China. The load and displacement data for each dynamometer card is composed of 200 point pairs. Generally, it is difficult to obtain multiple working conditions in a single well. Therefore, we gathered data from nearly 1300 wells over a period of more than 90 days. These data contained more than ten types of failures. To maximize the generality of the data, we screened 8 common types of working conditions from the sensor data of multiple wells, which are the insufficient liquid supply (ILS), traveling valve leakage (TVL), standing valve leakage (SVL), normal operation condition (NOC), gas interference (GIF), continuous pumping and spraying (CPS), oil pipe leakage (OPL) and upstroke pump bumping (UPB); the corresponding DCs are shown in Fig. 5. For each working condition, 3500 samples were selected from

![](bbox=[0.06, 0.62, 0.92, 0.88])

Fig. 4. Framework of 4S-TFSM-CNN method for working condition recognition.