# Generated score

![](bbox=[0.15, 0.13, 0.49, 0.22])

# Changing the style noise

![](bbox=[0.52, 0.13, 0.83, 0.22])

# Closest real score

![](bbox=[0.16, 0.27, 0.49, 0.37])

# Changing the melody noise
for the top line only

![](bbox=[0.52, 0.27, 0.83, 0.37])

# Changing the chord noise

![](bbox=[0.16, 0.43, 0.49, 0.53])

# Changing the groove noise
for the bottom line only

![](bbox=[0.52, 0.43, 0.83, 0.53])

Figure 11-16. Example of a MuseGAN predicted score, showing the closest real score in the training data and how the generated score is affected by changing the input noise

Let’s now play around with the input noise to tweak our generated score. First, we can try changing the chord noise vector—the bottom-left score in Figure 11-16 shows the result. We can see that every track has changed, as expected, and also that the two bars exhibit different properties. In the second bar, the baseline is more dynamic and the top line is higher in pitch than in the first bar. This is because the latent vectors that affect the two bars are different, as the input chord vector was passed through a temporal network.

When we change the style vector (top right), both bars change in a similar way. The whole passage has changed style from the original generated score, in a consistent way (i.e., the same latent vector is being used to adjust all tracks and bars).

We can also alter tracks individually, through the melody and groove inputs. In the center-right score in Figure 11-16 we can see the effect of changing just the melody noise input for the top line of music. All other parts remain unaffected, but the top-line notes change significantly. Also, we can see a rhythmic change between the two