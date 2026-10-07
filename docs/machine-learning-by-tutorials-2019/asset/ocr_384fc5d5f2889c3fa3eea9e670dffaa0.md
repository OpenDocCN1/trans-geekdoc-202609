# Machine Learning Chapter 11: Data Collection for Session Classification

| sessionid | activity | roll | pitch | yaw |
|---|---|---|---|--|
| 2018-08-27T21:53:54-1 | 0 | -0.46852787368514 | 0.839558723867373 | 0.360557933720217 |
| 2018-08-27T21:53:54-1 | 0 | -0.4730921638702034 | 0.8445954704025691 | 0.366491810895234 |
| 2018-08-27T21:53:54-1 | 0 | -0.473067129260027 | 0.8480360582483503 | 0.3678960506423581 |
| rotX | rotY | rotZ | gravX | gravY |
|---|---|---|---|--|
| 0.1335017314305114 | -0.0004288538167395 | 0.0564703212703201 | -0.3016131904813414 | -0.7434482722977524 |
| 0.1342090649067288 | -0.0233093526191416 | -0.05202950326827517 | -0.3025361309141546 | -0.7476867921095522 |
| 0.1332143286053246 | 0.0094172192480915 | -0.0169887146338521 | -0.30168383144913419 | -0.75015641139972407 |
| accelX | accelY | accelZ | user | u2 |
|---|---|---|---|--|
| -0.595588363491817 | -0.01028877467193604 | -0.00128758300321345 | 0.008517651893249512 | u_02 |
| -0.591117007462689 | -0.02011099447679387 | -0.01724313868277508 | 0.02307224273668141 | u_02 |
| -0.5884237131505024 | -0.0211099444769337 | -0.013950156629201958 | 0.019051152785375244 | u_02 |

> **Note:** If you've included your own data in any of these datasets, your results may vary from those shown here. This is true for all the images in this section.

First three samples of training set

Notice there is a column named userId. This was added inside sframe_from_folder — the values are derived from the names of your data files. This only works if your files contain data from just one user, and others are prefixed with the user's ID followed by a hyphen (-).

For example, all data read from a file named 'bob-data.csv' would be assigned a userId value of 'bob'. You could have stored the user ID in each row when you are collecting the data, but saving each user's data into separate files keeps them smaller and makes them easier to organize. While, it's important to know the source of your data — you will see later.

Here is another thing about head — the values in the activity column are all Ø. That’s nothing to worry about — it’s because you’re looking at the first few rows, less than one hundred percent of activity. But what does Ø even mean?

Inside GestureRecorder, you stored activity types as numeric values. Turi Create can deal with just this one file, but some humans interpret words more easily than numbers.

To convert these integers into something more readable, follow the following code in a cell and run it:

```
# 1
```

![](bbox=[0.16, 0.923, 0.84, 0.953])