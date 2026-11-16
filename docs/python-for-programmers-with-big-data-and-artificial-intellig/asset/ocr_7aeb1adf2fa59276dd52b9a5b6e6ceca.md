![](bbox=[0.17, 0.02, 0.88, 0.31])

Looking at the digits, you can see why handwritten digit recognition is a challenge:

+   Some people write “open” 4s (like the ones in the first and third rows), and some write “closed” 4s (like the one in the second row). Though each 4 has some similar features, they’re all different from one another.

+   The 3 in the second row looks strange—more like a merged 6 and 7. Compare this to the much clearer 3 in the fourth row.

+   The 5 in the second row could easily be confused with a 6.

+   Also, people write their digits at different angles, as you can see with the four 6s in the third and fourth rows—two are upright, one leans left and one leans right.

If you run the preceding snippet multiple times, you can see additional randomly selected digits. 8 You’ll probably find that—if not for the labels displayed above each digit—it would be difficult for you to identify some of the digits. We’ll soon see how accurately our first convnet will predict the digits in the MNIST test set.

8If you do run the cell multiple times, the snippet number next to the cell will increment each time, as it does in IPython at the command line.

# 15.6.3 Data Preparation

Recall from the “Machine Learning” chapter that Scikit-learn’s bundled datasets were preprocessed into the shapes its models required. In real-world studies, you’ll generally have to do some or all of the data preparation. The MNIST dataset requires some preparation for use in a Keras convnet.

# Reshaping the Image Data

Keras convnets require NumPy array inputs in which each sample has the shape:

```
(width, height, channels)
```