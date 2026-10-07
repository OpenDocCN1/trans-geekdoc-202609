# Structure

In this chapter, we will discuss the following topics:

+   - Creating a Decision Tree
  - Using Gini index to form a Gini Tree
    - Understanding Gini index
    - Forming the Decision Tree using the CART algorithm
    - Malware detection in JPEG files
  - The need
  - About JPEG files
  - The strategy
  - Building the model
    - Extracting EXIF tags from JPEG files
    - Cleaning the data
    - Forming the TF-IDF vectors
    - Reducing the number of features
    - Balancing the dataset
    - Building the Decision Tree model
- Testing the model
  - Finding the training accuracy score
  - Finding the test accuracy score

# Objectives

After reading this chapter, you will understand how decision trees are formed using Gini Index. The complete mathematics has been explained. We apply the Decision Tree algorithm to classify good and bad JPEG files in this chapter. You will also understand how to extract features from JPEG files.

# Creating decision tree tree

We mainly use two techniques to create decision trees. They are Gini index and using Entropy. We will discuss both methods. However, we will make the decision tree using the Gini index. The technique used to create decision trees using Gini index can be replicated by Entropy to create decision trees.