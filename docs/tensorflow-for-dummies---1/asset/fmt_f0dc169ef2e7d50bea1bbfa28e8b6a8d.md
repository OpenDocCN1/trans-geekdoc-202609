
`return tf.train.SessionRunArgs(loss)`

`def after_run(self, run_context, run_values):`
`print("Loss: ", run_values.results);`

In this code, `before_run` returns a `SessionRunArgs` that identifies the name of the `loss` variable. When `after_run` is called, the `results` field of the `run_values` argument contains the current value of `loss`.

### Subclasses of SessionRunHook

You can create your own subclasses of `SessionRunHook` and add code for different life-cycle methods. But in most cases, it's easier to instantiate an existing subclass. [Table 5-2](#09_9788126592555-ch05.xhtml#c05-tbl-0002) presents the constructors of each session hook class in the `tf.train` package.

[TABLE 5-2](#09_9788126592555-ch05.xhtml#rc05-tbl-0002) Session Hook Classes

| **Class** || **Description** |
| --- | --- |
| `LoggingTensorHook(tensors, every_n_iter=None, every_n_secs=None, at_end=False, formatter=False)` || Logs values of a tensor after a given number of steps or after a given time |
| --- | --- |
| `CheckpointSaverHook(checkpoint_dir, save_secs=None, save_steps=None, saver=None, checkpoint_baseline='model.ckpt’, scaffold=None, listeners=None)` || Saves data to a checkpoint after a given number of steps or after a given time |
| `SummarySaverHook(save_steps=None, save_secs=None, output_dir=None, summary_writer=None, scaffold=None, summary_op=None)` || Generates summary data after a given number of steps or after a given time |
| `StepCounterHook(every_n_steps=100, every_n_secs=None, output_dir=None, summary_writer=None)` || Counts the number of steps per second |
| `StopAtStepHook(num_steps=None, last_step=None)` || Tells the session to stop after a number of steps have executed or a specific step has been reached |
| `NanTensorHook(loss_tensor, fail_on_nan_loss)` || Stops training if loss equals NaN |
| `GlobalStepWaiterHook(wait_until_step)` || Delays execution until the global step reaches a given value |
| `FinalOpsHook(final_ops, final_ops_feed_dict=None)` || Evaluates tensors at the end of a session |
| `FeedFnHook(feed_fn)` || Runs the given function and sets the session's feed dict |

The first three session hook classes automate the processes of logging messages, saving variables, and generating summary data. You can specify how often the operation should be performed by setting a training step interval (`every_n_iter` or `n_steps`) or the time interval (`every_n_secs` or `n_secs`). Naturally, you can't set both types of intervals in the same method.

A `StepCounterHook` tells you about the session’s performance by showing how many training steps are performed in the given time interval. To provide output, it generates summary data using a summary writer. In contrast, a `StopAtStepHook` tells the session to stop at a given global step value or after a specified number of training steps.

### Creating a MonitoredSession

A `MonitoredSession` isn't a `Session`, but it contains a `Session` instance and provides methods for interacting with the session. For example, you can launch a `MonitoredSession`'s session by calling `run` and close the session by calling `close`.

To create a `MonitoredSession`, you need to call its constructor:

`MonitoredSession(session_creator=None, hooks=None, stop_grace_period_secs=120)`

The first parameter is a `SessionCreator` instance, which configures the underlying session. TensorFlow provides two subclasses of `SessionCreator`: `ChiefSessionCreator` and `WorkerSessionCreator`. The terms *chief* and *worker* refer to different types of processes in distributed applications.

You can associate session hooks with a `MonitoredSession` by setting the `hooks` parameter to a list of session hooks. The last parameter, `stop_grace_period_secs`, sets the number of seconds that a session thread can continue executing after an application calls `close`.

The `MonitoredSession` class also provides a method called `should_stop`. Applications frequently employ this method to determine whether the session should continue running. A session hook can stop a session through its `request_stop` method, which calls the monitored session's `should_stop` method. The following code demonstrates how `should_stop` can be used:

```
with tf.train.MonitoredSession(hooks=[custom_hook]) as sess:
 while not sess.should_stop():
 sess.run(…)
```

This `should_stop` method becomes particularly important for distributed TensorFlow applications. I discuss distributed applications and their sessions in [Chapter 13](#19_9788126592555-ch13.xhtml).

### Putting theory into practice

The code in the `ch5/monitor_train.py` module performs the same training operation as in the `ch5/simple_train.py` module. The difference is that monitor_train.py uses session hooks to save variables and generate summary data. [Listing 5-3](#09_9788126592555-ch05.xhtml#c05-fea-0003) presents the code.

[LISTING 5-3](#09_9788126592555-ch05.xhtml#rc05-fea-0003) Monitoring a Session with Session Hooks

```
# Custom session hook
class CustomHook(tf.train.SessionRunHook):

 def begin(self):
 print('Beginning the session!')

 def before_run(self, run_context):
 return tf.train.SessionRunArgs(loss)

 def after_run(self, run_context, run_values):
 if run_context.original_args != 'init':
 print('Loss: ', run_values.results)

 def end(self, session):
 print('The session is about to end!')

# Define a trainable variable
x_var = tf.Variable(0., name='x_result')

# Define an untrainable variable to hold the global step
step_var = tf.train.create_global_step()

# Express loss in terms of the variable
loss = x_var * x_var - 4.0 * x_var + 5.0

# Find variable value that minimizes loss
learn_rate = 0.1
num_epochs = 40
optimizer = tf.train.GradientDescentOptimizer(learn_rate).minimize(loss, global_step=step_var)

# Initialize variables
init = tf.global_variables_initializer()

# Create summary operation
summary_op = tf.summary.scalar('x', x_var)

# Create hooks
custom_hook = CustomHook()
checkpoint_hook = tf.train.CheckpointSaverHook(checkpoint_dir='ckpt_dir',
 checkpoint_basename='output', save_steps=10)
summary_hook = tf.train.SummarySaverHook(save_steps=10, output_dir='log', summary_op=summary_op)
hooks = [custom_hook, checkpoint_hook, summary_hook]

# Launch session
with tf.train.MonitoredSession(hooks=hooks) as sess:
 sess.run(init)

 for epoch in range(num_epochs):
 sess.run(optimizer)
```

This module creates three session hook instances:

* `CustomHook`: Prints messages at different points in the session's execution
* `CheckpointSaverHook`: Saves checkpoint data to a directory named `ckpt_dir`
* `SummarySaverHook`: Saves summary data to a directory named log

After creating the session hooks, the module creates a `MonitoredSession` and configures it with the three hook instances. Then it initializes the session’s variables and optimizes the model.

## Part 2

# Implementing Machine Learning

IN THIS PART …

Explore different types of statistical regression, including linear regression, polynomial regression, and logistic regression.

Learn about perceptrons and neural networks, which consist of interconnected nodes.

Understand the theory of image processing and convolutional neural networks (CNNs), which make it possible to recognize images.

Explore the theory of recurrent neural networks (RNNs) and use them to analyze sequential data.

## Chapter 6

# Analyzing Data with Statistical Regression

IN THIS CHAPTER

![check](images/check.png)**Identifying trends with linear and polynomial regression analysis**

![check](images/check.png)**Classifying points with logistic regression analysis**

![check](images/check.png)**Modeling systems with the logistic and softmax functions**

![check](images/check.png)**Computing loss with log likelihood and cross entropy**
