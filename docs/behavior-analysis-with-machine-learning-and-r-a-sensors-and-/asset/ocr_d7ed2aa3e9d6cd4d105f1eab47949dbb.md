# CHAPTER 5. PREPROCESSING BEHAVIORAL DATA

Several of the methods presented here can lead to information injection which can cause overfitting. That is, transferring information from the train set to the test set. This is something that we do not want both sets need to be independent to accurately estimate the generalization performance. You can find more details about information injection in section 5.5 of this chapter.

# 5.1 Missing Values

Many datasets will have missing values and we need ways to identify and deal with them. The reasons for missing data could be due to faulty sensors, processing errors, unavailable information, and so on. In this section, I present some tools that ease the process of missing values identification. Later, some imputation methods can be used to fill the missing values are listed.

To demonstrate some of these concepts, the SHEEP GOATS dataset (Kamminga et al., 2017) will be used. Due to its size, the files of this dataset are not included with the accompanying book files but they can be downloaded from https://easy.dans.knaw.nl/ui/datasets/easy-dataset:76113. The data was released as part of a study about animal behaviors. The researchers placed inertial sensors on sheep and goats and tracked their behavior during one day. They also video-recorded the season and annotated the data with different types of behaviors such as grazing, fighting, scratch-biting, etc. The device was placed on the neck with random orientation and it collects acceleration, orientation, magnetic field, temperature, and barometric pressure. Figure 5.1 shows a schematic view of the setting.

We start by loading a .csv file that contains one of the sheep and check if there are missing values. The naniar package (Tierney et al., 2019) offers a set of different functions to explore and deal with missing values. The gg_miss_var() function allows you to quickly check which variables have missing values and how. The following code loads the data and plots the number of missing values in each variable.

```
library(naniar)

# Path to S1.csv file.
dapath <- file.path(datasets_path,
  "sheep_goats","S1.csv")
```