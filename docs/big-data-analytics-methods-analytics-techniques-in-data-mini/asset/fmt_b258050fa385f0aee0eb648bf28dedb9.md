
## 附录 D：Oracle 程序

Oracle 程序是监督模块，用于选择 AUC 值最高的集成模型。该程序使用 R 语言编写，R 是一个开源统计软件包（Wang 2012），并在 1,073 个数据集及所有集成模型上进行了测试。源代码如下。程序计算每个 ANN 算法和集成模型相对于实际真值（疾病存在或不存在）的 AUC 值。第一列为实际真值，后续列为 ANN 算法和集成模型的数据。

```
######################################
###### R code for computing AUC   ######
###### Peter Ghavami – Adapted   ######
######   From Wang 2012    `######
######################################
```

```
### Load library packages ###
```

```
install.packages("verification")
library(verification)
```

```
### Import the input data file ###
```

```
## select the data file in the pop out window
data<-read.csv(file.choose(),header=T) # Import data from csv file
```

```
### Purpose: write a R function to compute AUC ###
### function name: getAUC
### function input:
###   D: true disease status
###   T: continuous test results of ANN and Ensembles
### function output: AUC value for this test
```

```
getAUC<-function(D, T){
roc.area(D, T)$A
}         # Call the getAUC function.
```

```
### compute the AUC values for each test in the data
```

```
### result for MLP
getAUC(data[,1],data[,2]) #MLP data is in the 2nd column
```

```
### result for PNN
getAUC(data[,1],data[,6])  #PNN data is in the 6th column
```

```
### result for GFF
getAUC(data[,1],data[,10])  #GFF data is in the 10th column
```

```
### result for SVM
getAUC(data[,1],data[,14])  #SVM data is in the 14th column
```

```
### result for Ensemble1
getAUC(data[,1],data[,18])  #Ensemble1 data is in the 18th column
```

```
### result for Ensemble2
getAUC(data[,1],data[,22])  #Ensemble2 data is in the 22nd column
```

```
### result for Ensemble3
getAUC(data[,1],data[,26]) #Ensemble3 data is in the 22nd column
```

```
### result for Ensemble4
getAUC(data[,1],data[,30])  #Ensemble4 data is in the 30th column
```

```
### result for Ensemble5
getAUC(data[,1],data[,34])  #Ensemble5 data is in the 34th column
```

# 参考文献

Aamodt, A., Plaza, E., “Case-Based Reasoning: Foundational Issues, Methodological Variations, and System Approaches,” *AI Communications*, Vol. 7, No. 1, March 1994. [→](#bodymatter-002.xhtml#xref_d23682e5073)

Adams, J. B., Wert, Y., “Logistic and Neural Network Models for Predicting a Hospital Admission,” *Journal of Applied Statistics*, Vol. 32, No. 8, 861–869, 2005. [→](#bodymatter-002.xhtml#xref_d23682e5260)

Allison, P. D., *Survival Analysis Using the SAS System*, SAS Institute publication, Cary, NC, 1995. 

AMA 2010. CPT 2011 Professional Edition, Michelle Abraham, *American Medical Association*, American Medical Association Press, Oct. 20, 2010. 

Arthi, K., Tamilarasi, A., “Prediction of Autistic Disorder Using Neuro Fuzzy Systems by Applying ANN Technique,” *International Journal of Developmental Neuroscience*, Vol. 26, 699–704, 2008. [→](#bodymatter-002.xhtml#xref_d23682e5339)

Baxt, W. G., “Use of an Artificial Neural Network for the Diagnosis of Myocardial Infarction,” *Annals of Internal Medicine*, Dec, 1, Vol. 115, No. 11, 843–848, 1991. 

Bewick, V., Cheek, L., Ball, J., “Statistics Review 13: Receiver Operating Characteristic Curves,” *Critical Care*, Vol. 8, No. 6, December 2004. [a](#bodymatter-002.xhtml#xref_d23682e25388), [b](#bodymatter-002.xhtml#xref_d23682e25790)

Blount, M., Ebling, M. R., Eklund, J. M., James, A. G., McGregor, C., Percival, N., Smith, K. P., Sow, D., “Real-time Analysis for Intensive Care. Development and Deployment of the Artemis Analytic System,” *IEEE Engineering in Medicine and Biology Magazine*, March/April 2010. [→](#bodymatter-002.xhtml#xref_d23682e5217)

Bourdes, V., Ferrieres, J., Amar, J., Amelineau, E., Bonnevay, S., Berlion, M., Danchin, N., “Prediction of Persistence of Combined Evidence-based Cardiovascular Medications in Patients with Acute Coronary Syndrome after Hospital Discharge Using Neural Networks,” *Medical & Biological Engineering Computing*, Vol. 49, 947–955, 2011. [→](#bodymatter-002.xhtml#xref_d23682e9898)

Bottaci, L., Drew, P. J., Hartley, J. E., Hadfield, M. B., Farouk, R., Lee, P. WR., Macintyre, I. MC., Duthie, G. S., Monson, J. RT, “Artificial Neural Networks Applied to Outcome Prediction for Colorectal Cancer Patients in Separate Institutions,” *The Lancet*, Vol. 350, No. 9076, 469–472, Aug. 16, 1997. [→](#bodymatter-002.xhtml#xref_d23682e5241)

Breiman, L., Friedman, J. H., Olshen, R. A., Stone, C. J., *Classification and Regression Trees*. Monterey, CA: Wadsworth & Brooks/Cole Advanced Books & Software, 1984. 

Brown, S.W., Strong, V., “The Use of Seizure-alert Dogs,” *Seizure*, Vol. 10, 39–41, 2001. 

Center for Evidence Based Medicine website, EBM Tools, [http://www.cebm.net/index.aspx?o=1023](http://www.cebm.net/index.aspx?o=1023), accessed March 22, 2012. [→](#bodymatter-002.xhtml#xref_d23682e4990)

Coble, J., Hines, J. W., “Identifying Optimal Prognostic Parameters from Data: A Genetic Algorithms Approach,” Annual Conference of the Prognostics and Health Management Society, 2009. 

Coble, J., Hines, J. W., Fusing Data Sources for Optimal Prognostic Parameter Selection, Sixth American Nuclear Society International Topical Meeting on Nuclear Plant Instrumentation, Control, and Human-Machine Interface Technologies NPIC & HMIT 2009, Knoxville, Tennessee, April 5–9, 2009. 

Collett, D., *Modeling Survival Data in Medical Research*. London: Chapman & Hall, 1994. 

Daley, M., Narayanan, N., Leffler, C. W., “Model-derived Assessment of Cerebrovascular Resistance and Cerebral Blood Flow Following Traumatic Brain Injury,” *Experimental Biology and Medicine*, Vol. 235, April 2010. 

Davenport, R.J., Dennis, M.S., Wellwood, I., Warlow, C., “Complications After Acute Stroke,” *Stroke*, Vol. 27, 415–420, 1996. 

Dayhoff, J. E., DeLeo, J. M., “Artificial Neural Networks, Opening the Black Box,” *Cancer*, Vol. 19, 1615–1635. Presented at the Conference on Prognostic Factors and Staging in Cancer Management: Contributions of Artificial Neural Networks and Other Statistical Methods, 2001. 
