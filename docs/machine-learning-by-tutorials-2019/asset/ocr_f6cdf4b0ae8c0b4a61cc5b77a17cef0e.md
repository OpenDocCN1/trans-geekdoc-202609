# # Chapter 13: Sequence Classification
By Chris LaPollo

**Update Note:** Apple loves to keep us waiting. As of writing, the CoreML APIs needed to update this chapter weren't quite ready. As Apple releases new APIs, we'll continue to update this chapter. We'll also notify you and let you know how to access the updated versions.

If you've followed along with the last couple chapters, you've learned some things about how working with sequences differs from other types of data, and you got some practice collecting and cleaning datasets. You also trained a neural network to recognize gestures from iPhone sensor data. Now you've trained your model in a game where players have just a few seconds to perform an activity announced by the app. When you've finished, you'll have learned how to feed data from your model to classify user activity.

This chapter picks up where the last ended — just after you added your classification model to the GestureIt project. If you didn't go through the previous chapter and train your own model, don't fret! You can always use the GestureIt starter project in the chapter resources. Either way, once you have the project in Xcode, you're ready to go!

# ## Classifying human activity in your app

You trained a model and added it to the GestureIt project in the last chapter, and you learned a bit about how model works. Now take a quick look through the project to see what else is there. The project's **Info.plist** file already includes