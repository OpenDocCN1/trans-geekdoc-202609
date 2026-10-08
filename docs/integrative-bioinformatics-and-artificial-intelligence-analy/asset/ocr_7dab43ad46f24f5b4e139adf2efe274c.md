# Journal Pre-proof

173

F1 = 2 \cdot \frac{precision \cdot recall}{precision + recall}

174

ROC-AUC is the area under the error curve, which evaluates the quality of the model without being tied to a specific threshold. For building the ROC curve, TPR against the FPR is plotted, and then the area under the resulting curve was calculated.

175

TPR = \frac{TP}{TP + FN} \n FPR = \frac{FP}{FP + TN}

176

177

178

# 2.5. Feature selection using MI.

179

Transcriptomic data consists of a large number of genes (features) that are much more than the number of samples, which leads to overfitting in the classification tasks. The FS procedure is able to reduce the dimensionality of the data while preserving significant information. Considering that the number of features should be equal to or smaller than the sample size [30], the following options were chosen: First, the number of selected features was equal to the number of samples in the dataset, while the second option, the number of selected features was 80% of the number of samples. Several methods in the FS procedure (Figure 1.C) were chosen using PCA and SelectBest method with ANOVA F-value as a score function. Moreover, ML methods such as LR and RF were chosen to extract important features from trained models. The methods of important feature extraction are different for LR and RF. In the LR model, absolute weights for each feature were ranged in descending order and the top N of (N is chosen according to the options above) were selected for the next step. RF is a method that fits several decision tree classifiers on various splits of the dataset. The importance of each feature was calculated in several steps: First, the value of the decrease in impurity criterion for each node associated with the feature in each decision tree is calculated, then the sum of values of decrease impurity on all nodes is multiplied by the percentage of examples reaching these nodes. Weighted sum is a feature of importance in the RF model.

180

181

182

183

184

185

186

187

188

189

# 2.6. Machine Learning methods

190

191

192

193

194

195

196

197

198

199

200

201

202

203

Several ML models were shown as in Figure 1.C to distinguish between MDD patients and HCs based on selected features only. Different FS methods and parameter combinations inside the ML pipeline selection block including the GridSearchCV procedure (sklearn Python library, version 0.24.2) for fine-tuning the models. Estimation of the

Page 7 of 41