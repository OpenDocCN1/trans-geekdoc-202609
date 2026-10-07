+   Incorrect data types. For example, strings where there should be numbers.

+   Missing values. It's common for some rows to have values missing. You'll need to decide how to handle them — remove rows or insert unreasonable values. The choice depends on your project, and there are many options to fill the values if you go that route. For example, you might use feature's mean, median or mode value, or perhaps calculate a new value based on values from nearby rows.

+   Outliers. *Some variation* is required to make a good dataset, but there are cases when a few samples may be too rare to worth including in your dataset. Training with them can confuse the model, reducing its overall performance, and it's sometimes better to accept that there are some things your model won't handle.

> **Note: You don't have** to remove such samples — you may well want your model to support them. But it's something to consider.

You'll work with Python for the rest of this and the next chapter, so no more Xcode for a while. You'll also need Jupyter and T Create, so if you don't already have an environment that includes these from earlier in the book, create one now using the file at `projects/notebooks/turienv.yaml`. If you're unsure how to do so, take a look at Chapter 4, "Getting Started with Python & T Create."

> From here on, we'll assume your environment with T Create is named `turienv`, so keep that in mind when you see it mentioned.

Launch Jupyter from within your `turienv` environment. Create a new notebook in the `notebooks` folder of the chapter resources. Or if you'd prefer to follow along in a completed notebook, you can open `notebooks/Data_Exploration_Complete.ipynb` instead.

Get started by entering the code in a cell and running it with **Shift+Return:**

```
%matplotlib inline
import turicreate as tc
import activity_detector_utils as utils
```

This gives you access to the `turicreate` package as well as some helper functions