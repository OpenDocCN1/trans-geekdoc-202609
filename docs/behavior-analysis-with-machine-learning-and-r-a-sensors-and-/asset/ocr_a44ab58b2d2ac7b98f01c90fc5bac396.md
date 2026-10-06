# CHAPTER 2. PREDICTING BEHAVIOR WITH CLASSIFICATION MODELS

![](bbox=[0.168, 0.133, 0.831, 0.348])

Figure 2.24: Triangle gesture.

Figure 2.24 shows the raw accelerometer values (dashed lines) for a triangle gesture. The solid line shows the resulting magnitude. This will also simplify things since we will now work with 1-dimensional sequences by just using the magnitude instead of the other 3 axes.

The gestures are stored in text files that contain the x, y, and z records. The script hand_gestures_auxiliary.R has some auxiliary functions to preprocess the data. Since sequences of each gesture are of varying length, storing them as a data frame could be problematic since data frames have fixed sizes. The gen.instances() function processes the files and returns all gestures as a list. This function also computes the magnitude (equation 2.16)). The following code (from hand_gestures.R) calls the gen.instances() function and stores the results in the instances variable which is a list. Then, we select the first and second instances to be the query and the reference.

```
# Format instances from files.
instances <- gen.instances("../data/hand_gestures/")

# Use first instance as the query.
query <- instances[[1]]

# Use second instance as the reference.
ref <- instances[[2]]
```

Each element in instances is also a list that stores the type and values (magnitude) of each gesture.