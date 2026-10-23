is far too little for neural networks.

BUT: If we pair two photos and decide if the images in the tuples are the same or not, we get 120 different pairs of images.
If you do not know how we have calculated the amount of images – here is the tip:

We have 5 images of 3 different categories, a total of 15 images. How many distinct pairs of 2 images can we build (if we can use the same image twice within a pair)?

This is what is mathematically called a combinatory problem with repetition.
Formula for the binomial coefficient (This means you form pairs of size m out of a total amount of n elements):
(n) n! (19.1)m= (n −m)! ·m!
Now if we use repetition we have to adapt our m and n to: