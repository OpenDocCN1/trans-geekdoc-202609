# # 1 Basic principles of tomography

This is an introductory chapter that presents the fundamental concepts in tomography. It first defines what the tomography is and shows how a tomographic image can be obtained from its measurements using two simple examples. The concept of projection is then explained. Next, the filtered backprojection (FBP) image reconstruction method is introduced using a point source example. Finally, the concept of backprojection is discussed.

# ## 1.1 Tomography

The Greek word tomos means a section, a slice, or a cut. Tomography is the process of imaging a cross section. For example, if you are given a watermelon and would like to see inside, the easiest way to do so is to cut it open (Figure 1.1). Clearly, this approach to obtain a cross-sectional image is not a good idea in medicine. Nobody wants to be cut open in order to see what is inside.

![](bbox=[0.1, 0.45, 0.44, 0.645])

Fig. 1.1: Cutting open to see what is inside.

Let us look at another example. You are visiting a small park, which is closed for maintenance. You walk around the park and take a few pictures of it. After you get home, you can use your pictures to make a map of the park. To make your life easier, let us assume that there are two large trees in the park, and you take two pictures from the east and the south (Figure 1.2, left). Using these two pictures, you can map out where these two trees are (Figure 1.2, right). This can be done by positioning the pictures at the original orientations at which the pictures were taken, drawing a line from each tree, and finding the intersections. If you have enough pictures, it is not hard to find out where the trees are.