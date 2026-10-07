Machine Learning Chapter 11: Data Collection for Sequence Classification

problem, too, because they'll skew your evaluation results, making it more difficult to judge your model.

> Note: The rest_it activity takes up half of each dataset — you might want to remove some of those samples to bring it in with the other gutters, but it wasn't a problem when training the model included with the book.

The dataset included in the resources contains 216 actions for training, 24 for validation and 27 for testing. It's not a lot of data, but it's as the author's family was willing to put up with collecting. :[: Still, it's a reasonable balance, with about 80% of your data for training, and around 10% for validation and testing.

Once you're convinced your datasets are good to go, run the following code to save the cleaned SFrames for use:

```
train_sf.save('data/cleaned_train_sframe')
test_sf.save('data/cleaned_test_sframe')
valid_sf.save('data/cleaned_valid_sframe')
```

The method you use save SFrames in different formats, such as CSV and JSON. Here you're using a format that creates the given folder and stores various binary files in it. It's convenient it's smaller and loads faster than the others, but feel free to use any format you like. And remember, you still have your original files, so you can start over if you decide you don't like something about your cleaned data.

> Note: Turi creates many options for data exploration and manipulation, as Pandas and NumPy. And it provides methods to convert to and from the data structures used by these other libraries, so if there's something you prefer to do in one package over another, you can freely move back and forth. It's a good idea to spend some time looking through the documentation for these various frameworks to see what's available, but don't try to learn everything at once — as you do more with machine learning, you'll continue to discover new things about it and all these supporting frameworks.

# Key points

+   - Core Motion provides access to motion sensors on iOS and WatchOS devices.

![](bbox=[0.162, 0.922, 0.839, 0.956])