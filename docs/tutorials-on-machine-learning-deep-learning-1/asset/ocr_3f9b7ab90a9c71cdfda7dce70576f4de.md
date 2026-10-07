[4]. We're going to calculate visible output nodes, again initially it will be some random starting weights. This process is called decoding.

That's the forward propagation. We've just put the information, the data through our Auto Encoder from left to right.

![](bbox=[0.365, 0.038, 0.875, 0.233])

[5]. We're going to compare the results to the actual ratings for those six movies. And then we'll calculate the error.

![](bbox=[0.365, 0.253, 0.875, 0.417])

[6]. And then we will propagate it back through the network, we'll adjust the weights accordingly.

![](bbox=[0.365, 0.423, 0.875, 0.593])

[7]. We will take the next row in our data set. And we'll do the same thing and so on. We'll continue through all the rows.

![](bbox=[0.365, 0.613, 0.875, 0.783])

[8]. It means we've finished a whole epoch.

And then we just repeat these epochs.
Hopefully, our training converges to some sort of value.

![](bbox=[0.365, 0.803, 0.875, 0.973])