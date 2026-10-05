image with compilers and other build tools, but then you have another stage where you copy the compiled app into a slim image for production. The builder can even run different stages in parallel for faster builds.

Figure 8.6 shows a high-level workflow. Stage 1 builds an image with all the required build and compilation tools. Stage 2 copies the app code into the image and builds it. Stage 3 creates a small production-ready image containing only the compiled app and anything needed to run it.

![](bbox=[0.198, 0.477, 0.802, 0.658])

Figure 8.6

Let’s look at an example!

We’ll work with the code in the multi-stage folder of the book’s GitHub repo. It’s a simple Go app with a client and server