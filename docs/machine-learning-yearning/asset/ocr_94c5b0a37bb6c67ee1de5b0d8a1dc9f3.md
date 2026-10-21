+   - If you have worked on a important application for a long time, then you might have intuition about how much more progress you can reasonably make in the next quarter/year.

Add the desired level of performance to your learning curve:

![](bbox=[0.24, 0.19, 0.73, 0.36])

You can visually extrapolate the red “dev error” curve to guess how much closer you could get to the desired level of performance by adding more data. In the example above, it looks plausible that doubling the training set size might allow you to reach the desired performance.

But if the dev error curve has “plateaued” (i.e. flattened out), then you can immediately tell that adding more data won’t get you to your goal:

![](bbox=[0.24, 0.56, 0.77, 0.73])

Looking at the learning curve might therefore help you avoid spending months collecting twice as much training data, only to realize it does not help.