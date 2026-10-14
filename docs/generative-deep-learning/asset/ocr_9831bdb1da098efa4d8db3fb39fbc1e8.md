# Constant width italic

Shows text that should be replaced with user-supplied values or by values determined by context.

![](bbox=[0.16, 0.15, 0.24, 0.24])

This element signifies a tip or suggestion.

![](bbox=[0.17, 0.26, 0.24, 0.33])

This element signifies a general note.

![](bbox=[0.15, 0.36, 0.25, 0.43])

This element signifies a warning or caution.

# Codebase

The code examples in this book can be found in a GitHub repository. I have deliberately ensured that none of the models require prohibitively large amounts of computational resources to train, so that you can start training your own models without having to spend lots of time or money on expensive hardware. There is a comprehensive guide in the repository on how to get started with Docker and set up cloud resources with GPUs on Google Cloud if required.

The following changes have been made to the codebase since the first edition:

+   - All examples are now runnable from within a single notebook, instead of some code being imported from modules across the codebase. This is so that you can run each example cell by cell and delve into exactly how each model is built, piece by piece.
+   - The sections of each notebook are now broadly aligned between examples.
+   - Many of the examples in this book now utilize code snippets from the amazing open source Keras repository—this is to avoid creating a completely detached open source repository of Keras generative AI examples, when there already exist excellent implementations available through the Keras website. I have added references and links to the original authors of code that I have utilized from the Keras website throughout this book and in the repository.