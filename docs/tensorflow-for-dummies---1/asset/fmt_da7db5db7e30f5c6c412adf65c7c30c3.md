
If your TensorFlow installation can access GPUs and TensorFlow recognizes a compliant GPU, your sessions will assign math operations to the GPU by default. You can configure how the CPU interacts with the GPU by setting the `gpu_options` field in a session’s `ConfigProto`. You must assign `gpu_options` to a `GPUOptions` buffer, and [Table 11-3](#17_9788126592555-ch11.xhtml#c11-tbl-0003) lists its fields.

[TABLE 11-3](#17_9788126592555-ch11.xhtml#rc11-tbl-0003) GPUOptions Fields

| **Field** || **Type** || **Description** |

| --- | --- | --- |

| `per_process_gpu_memory_fraction` || `double` || Configures the fraction of the GPU memory to allocate |

| --- | --- | --- |

| `allocator_type` || `string` || Sets the GPU allocation strategy |

| `deferred_deletion_bytes` || `int64` || Delays deletion to reduce driver processing |

| `allow_growth` || `bool` || Enables/disables pre-allocation of GPU memory |

| `visible_device_list` || `string` || Determines how GPU devices are mapped |

| `polling_active_delay_usecs` || `int32` || Configures the number of milliseconds that should elapse between polling when active |

| `polling_inactive_delay_msecs` || `int32` || Sets the number of milliseconds between polling when inactive |

| `force_gpu_compatible` || `bool` || Forces tensors to be allocated in GPU's pinned memory |

By default, TensorFlow pre-allocates all of a GPU’s memory for its operations. But if you set `allow_growth` to `True`, TensorFlow won't allocate any memory in advance. Instead, it will allocate memory only as it becomes necessary.

If you set `per_process_gpu_memory_fraction` to a value less than 1, TensorFlow will pre-allocate that fraction of the GPU’s visible memory. For example, the following code configures a session to pre-allocate 80 percent of the GPU’s memory for its operations:

```
gpu_opts = tf.GPUOptions( per_process_gpu_memory_fraction=0.8)
conf = tf.ConfigProto(gpu_options=gpu_opts)
with tf.Session(config=conf) as sess:
 …
```

You can improve performance by reducing the number of commands that the CPU sends to the GPU. One frequent command involves deleting objects in GPU memory. By default, the CPU will tell the GPU to delete objects when they occupy more than several megabytes of storage. You can customize this behavior by setting the `deferred_deletion_bytes` field of a `GPUOptions` to a desired memory size.

## Executing TensorFlow in a Cluster

In addition to running operations on GPUs, you can code distributed applications that execute on multiple computers. I found this topic very difficult to understand when I first encountered it, so I start by comparing it to a more familiar subject: web browsing.

When you browse the web, your browser (the client) sends a request to a remote machine called the *server.* To be precise, the server is a process on the remote machine (the server's host) that listens for requests on a specific port. When you send your request to a web server’s host and port, the server sends a response containing a web page. A host can execute multiple servers, but each server always listens for messages from a specific port.

In a distributed TensorFlow application, a client accesses multiple servers, which may run on separate systems or the same system. Like a web server, each TensorFlow server listens for messages directed to a specific host and port.

Each server executes a single unit of work called a *task*. A group of related tasks form a *job*. The collection of servers associated with an application is called a *cluster*.

If you’re comfortable with these terms (server, task, job, cluster), you’ll have no trouble coding distributed TensorFlow applications. In general, the development process requires three steps:

1. **Define the application’s jobs, tasks, and server hosts/ports in a `ClusterSpec`.**
2. **Create a `tf.train.Server` for each server in the cluster.**
3. **Define operations for each task.**

If your cluster executes on multiple computers, you don't have to rewrite the application for each computer. Just code the application once and pass different command-line arguments to each system. Alternatively, you can use a cluster manager like Kubernetes to manage the cluster and automatically define servers and tasks.

### Creating a ClusterSpec

A cluster specification defines the application’s jobs and tasks and associates each task with the network address of a server. Cluster specifications are represented by instances of `tf.train.ClusterSpec`. The class constructor accepts one argument that can take one of three forms:

* A dict that associates job names with a list of network addresses
* A dict that associates job names with dicts that associate task numbers with network addresses
* An existing `ClusterDef` protocol buffer

This discussion focuses on the first two forms. For example, suppose that you want your cluster to execute tasks in two jobs. The first job, `j1`, has one task, and the second job, `j2`, has two tasks. You could define your cluster with the following `ClusterSpec`:

```
spec = tf.train.ClusterSpec({
 'j1': ['sys1.ex.com:121'],
 'j2': ['sys2.ex.com:122', 'sys3.ex.com:123']})
```

For each network address, you need to provide a host name, such as `sys1.ex.com`, and a port, such as `123`. TensorFlow creates one task for each network address in the `ClusterSpec` and assigns each task a number corresponding to its order in the job's list. In the preceding example, TensorFlow assigns Task 0 to `sys1.ex.com`, Task 0 to `sys2.ex.com`, and Task 1 to `sys3.ex.com`.

You can assign your own task numbers by associating each job name with a dict that associates integers with addresses:

```
spec = tf.train.ClusterSpec({
 'j1': {3: 'sys1.ex.com:121'},
 'j2': {2: 'sys2.ex.com:122',
 1: 'sys3.ex.com:123'}})
```

For the sake of simplicity, the `ClusterSpec`s in this book allow TensorFlow to set task indices automatically.

### Creating a server

After you split your application's computation into tasks, you need to create servers to perform the tasks. You can create a server by calling the `tf.train.Server` constructor:

```
tf.train.Server(server_or_cluster_def, job_name=None, task_index=None, protocol=None, config=None, start=True)
```

You can set the first parameter to a `ServerDef`, which is a protocol buffer that defines a server's operating environment. But most applications assign the first parameter to a `ClusterSpec`. To tell the server which task it’s intended to perform, you need to set the `job_name` and `task_index` parameters. As an example, the following code creates a server to perform Task 1 of the job named `j2`:

```
server = tf.train.Server(spec, job_name='j2', task_index=1)
```

The constructor's `protocol` parameter identifies the communication mechanism that the `Server` will use to receive tasks. At the time of this writing, the only accepted protocol is `grpc`, which identifies the gRPC protocol. This is Google's free implementation of remote procedure calls (RPC), and you can find out more about gRPC by visiting [`http://grpc.io`](http://grpc.io).

The `config` parameter accepts a `ConfigProto` that configures all the sessions that run on the server. I present the `ConfigProto` and its many fields at the start of the chapter in the “[Configuring a new session](#17_9788126592555-ch11.xhtml#c11-sec-0003)” section.

The `start` parameter identifies whether the server should start immediately after it's created. If you set this parameter to `True`, the server will start processing tasks after it’s created. If you set it to `False`, you can start the server later by calling its `start` method.

### Specifying jobs and tasks

After you define your cluster and create your servers, you need to provide code for the cluster's tasks. You don’t need to write a separate program for each task. Instead, most developers write one program and partition its code so that different portions are executed by different tasks.
