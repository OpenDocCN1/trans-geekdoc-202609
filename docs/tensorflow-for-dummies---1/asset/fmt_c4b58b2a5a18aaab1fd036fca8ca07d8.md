
You can associate code with a specific task by calling the `tf.device` function discussed earlier in the “[Assigning operations to devices](#17_9788126592555-ch11.xhtml#c11-sec-0014)” section. For example, the following code executes only on Task 0 of Job `j1`:

```
with tf.device('/job:j1/task:0'):
  const_a = tf.constant(3.6)
  const_b = tf.constant(1.2)
  total = const_a + const_b
```

You can also partition your code using `if` statements:

```
if job_name == 'j1' and task_num == 0:
  …
elif job_name == 'j1' and task_num == 1:
  …
```

When you define a cluster, you can create as many jobs and tasks as you like. But many distributed TensorFlow applications have only two jobs:

* **Parameter server (`ps`):** Stores the application's variables
* **Worker replica (`worker`):** Performs the application’s computation, including the processing that updates the variables

You can define these jobs in a cluster specification with code like the following:

```
spec = tf.train.ClusterSpec({'ps': [..], 'worker': [..]})
```

This section introduces parameter servers and workers and shows you how to create them in code.

### Parameter servers

In a distributed application, TensorFlow recognizes that variables with the same name on the same device represent the same data. That is, if Tasks X and Y both operate on a variable named `weight_var`, TensorFlow understands that they should access the same `weight_var` variable. These tasks run in different processes, so TensorFlow replicates the variables between the processes.

A *parameter server* (PS) serves as a central location for storing, saving, and retrieving variables. In many applications, a PS task will simply declare variables and then block until the application is complete. To demonstrate this, the following code defines a parameter server that declares two variables, `weights` and `biases`, and then blocks until the application is complete.

```
server = tf.train.Server(cluster, job_name='ps', task_index=0)
if job_name == 'ps':
  weights = tf.Variable(…)
  biases = tf.Variable(…)
  server.join()
```

After the parameter server declares the `weights` and `biases`, other tasks can access these variables and update them as needed. The `join` method tells the server to block indefinitely.

### Workers

Generally speaking, any job that performs computation is considered a *worker job.* Each task in a worker job is called a *worker replica* or just a *worker*. To perform its computation, each worker needs to create and launch a session.

This requirement presents a problem: You can't create regular sessions in a distributed application. You need to run each session in the appropriate server process. To understand how to run a session in a server, you need to be familiar with server targets.

Just as web servers communicate using HTTP, TensorFlow servers communicate using gRPC. Each server has a gRPC address determined by its host and port. For example, if you configure a server to execute a task whose address is localhost:123, the server’s gRPC address will be given as follows:

```
grpc://localhost:123
```

This gRPC address is called the server’s *target*. You can access this target through the `target` property of the `Server` instance.

To create a session to run inside a server, you need to set the first parameter of `tf.Session` to the server's target. The following code creates a `Server` and then creates a session that connects to it:

```
server = tf.train.Server(spec, job_name='worker', task_index=1)
with tf.Session(server.target) as sess:
  …
```

Here’s a question: If workers in a distributed application need to access the same variable data, how can the variables be initialized? The parameter server can’t initialize its variables because it doesn’t run a session. But if every worker initializes the variables separately, TensorFlow won’t be able to replicate the data between processes.

The answer is that one of the workers needs to handle initialization, and the other workers need to wait until the initialization is complete. The worker that handles initialization is called the *chief*. You can assign the chief’s operations in a session by calling `tf.train.MonitoredTrainingSession`.

#### Workers and monitored sessions

[Chapter 5](#09_9788126592555-ch05.xhtml) presents the fascinating topic of session hooks and explains how to associate hooks with a `MonitoredSession`. You can configure `MonitoredSession`s for distributed applications by calling a function called `tf.train.MonitoredTrainingSession`:

```
MonitoredTrainingSession(master='', is_chief=True, checkpoint_dir=None, scaffold=None, hooks=None, chief_only_hooks=None, save_checkpoint_secs=600, save_summaries_steps=USE_DEFAULT, save_summaries_secs=USE_DEFAULT, config=None, stop_grace_period_secs=120, log_step_count_steps=100)
```

This function looks like a class constructor, but it returns a `MonitoredSession`, not a `MonitoredTrainingSession`. If a worker invokes this function with `is_chief` set to `True`, the `MonitoredSession` will perform the session's initialization when it’s launched. Therefore, only one worker (the chief) should call this function with `is_chief` set to `True`. When other workers call this function, the returned `MonitoredSession` will wait until the chief's session has performed initialization.

The first argument, `master`, serves the same purpose as the `target` argument in the `Session` constructor. That is, it identifies the gRPC location of the worker intended to run the session, such as `grpc://localhost:123`.

The `MonitoredTrainingSession` function accepts general session hooks (`hooks`) and session hooks intended for the chief's session (`chief_only_hooks`). In addition, the function accepts parameters for setting checkpoints and generating summary data. By setting these parameters, you don’t need to create `CheckpointSaverHook`s or `SummarySaverHook`s.

### Running a simple cluster

The code in the `ch11/cluster.py` module provides a simple example of a distributed TensorFlow application. The module doesn't perform any machine learning, but demonstrates how a set of worker tasks can combine their efforts to update a variable.

To be specific, the application creates four workers and uses them to approximate *π*. This approximation involves summing together the areas of the rectangles under the function y = (1 + x²)^(\-1) as x runs from 0 to 1 and multiplying the sum by 4. In [Figure 11-1](#17_9788126592555-ch11.xhtml#c11-fig-0001), the graph divides the area under the function into 30 regions.

![FIGURE 11-1: An application can approximate π by splitting the area under the function into rectangles and adding the areas together.](images/9788126592555-fg1101.png)

[FIGURE 11-1:](#17_9788126592555-ch11.xhtml#rc11-fig-0001) An application can approximate *π* by splitting the area under the function into rectangles and adding the areas together.

The `ch11/cluster.py` module generates four workers to perform the approximation. [Listing 11-1](#17_9788126592555-ch11.xhtml#c11-fea-0001) presents the code.

[LISTING 11-1](#17_9788126592555-ch11.xhtml#rc11-fea-0001) Approximating Pi in a Distributed Application

```
# Session hook to print output
class OutputHook(tf.train.SessionRunHook):

  def before_run(self, run_context):
    return tf.train.SessionRunArgs(pi_var)

  def after_run(self, run_context, run_values):
    print('Pi approximation:', run_values.results)

# Define a cluster with two jobs and five tasks
spec = tf.train.ClusterSpec({'worker':
  ['localhost:31415', 'localhost:31416', 'localhost:31417', 'localhost:31418']})

# Perform task-dependent operations
flags = tf.flags
flags.DEFINE_string('task', '', '')
if not flags.FLAGS.task:

  # Launch the worker processes
  subprocess.Popen('python cluster.py --task=0', stderr=subprocess.STDOUT)
  subprocess.Popen('python cluster.py --task=1', stderr=subprocess.STDOUT)
```
