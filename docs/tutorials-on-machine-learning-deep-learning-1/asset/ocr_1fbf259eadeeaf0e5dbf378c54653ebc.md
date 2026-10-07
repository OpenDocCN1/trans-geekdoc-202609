Example: Let's see an example how Cross Entropy function can be applied: Here p is the value of the range i.e. 1 or . And we put the output-probability into q. The figure shown above.

![](bbox=[0.106, 0.076, 0.893, 0.246])

# 9.4.5 Cross Entropy function calculates NNs performance more accurately

Now we consider two neural networks and we pass three images of a Dog, a Cat and another animal (which is actually another dog if you look closely, but difficult to recognize). Those NNs don't know about animals.

+   - In following the boxed and and 1 represents the actual values being Cat/Dog. So we want to see the performances of these two NNs.
- Below the values inside the "Red-Circle" are the predicted values from these two NNs.

![](bbox=[0.295, 0.426, 0.742, 0.715])

The key is here that even both NNs got it wrong in the last case, BNI shows better performance than NN2. Because in last case NN1 gave a dog 40% vote where NN2 gave 10%.

+   - Different functions to measure performance of NNs: Now we're going to look at the different functions that they can measure
- In tables: "Dog" and "Cat" columns represent the predicted values. "Dog" and "Cat" columns represent the actual values.
- Notice that though NN2 was correct for first two trials but its performance was poor.
  - NN2 votes 60% for Dog where NN1 votes 90% in first trial.
  - NN2 votes 70% for Cat where NN1 votes 90% in second trial.
  - In the last trial both NN1, NN2 are incorrect, but NN1's performance was better in this case. In NN1 gave a dog 40% vote where NN2 gave 10%.