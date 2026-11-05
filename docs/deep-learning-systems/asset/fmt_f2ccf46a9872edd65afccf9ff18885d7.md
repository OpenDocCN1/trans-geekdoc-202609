
Declarative programming enables the AOT compiler to do analysis and optimizations across the entire set of expressions. The runtime exploits buffer reuse and inter-op parallelism. A single static computation graph often represents the entire topology.

A static graph is suitable for production environments to get maximum performance in terms of speed and memory. Having the entire computation graph available provides the compiler information on what values to compute (and ignores graph nodes that are not necessary for the desired output), how much memory to allocate, and what subgraphs to execute in parallel.

Declarative programs follow a dataflow programming model, that is, the program is represented as a computational (symbolic) directed graph with nodes representing computations and edges representing data. Special nodes in the graph represent the control-flow.

Imperative programs implement control-flow in the native language, which facilitates specifying arbitrary control-flow in the program. For instance, in PyTorch, the Python native control-flow statements `if`, `for`, and `while` are used. In addition to being more intuitive, this explicit control-flow facilitates using models with complex dynamic graphs (non-DAGs) often used in NLP and RL research.

## 9.1.3 AUTOMATIC DIFFERENTIATION

A step in training is computing the gradient of the cost with respect to each weight and activation via backpropagation. Once a model and a cost function are defined, the frameworks determine the computations necessary for the backpropagation. This feature is native in all popular frameworks and known as *automatic differentiation* (AD).

AD computes the gradient of one node with respect to the previous node and uses the chain rule to compute the gradient of the cost with respect to each weight and activation. In symbolic programming, this is done by adding gradient computation nodes. In imperative programming, this is done by recording or tracing the flow of values as they occur and generating a dynamic graph; the programmer marks the layers needed for AD.

## 9.2 TENSORFLOW

TensorFlow is an open-source library, written in C++, developed by Google with several contributors outside of Google. It was released in November 2015 and has become the most popular framework in the industry. It supports over a thousand different operators \[SL19\]. In addition to Python, TensorFlow supports other language APIs (some maintained by the broader community at various degrees of support), including Swift, Julia, C++, Scala, Java, JavaScript, Rust, and Go. Models trained by TensorFlow can deploy across various inference engines.

TensorFlow v1 is designed as a declarative programming style library \[ABC+16\]. Programmers construct an AST (the graph), usually in Python using a low-level API, and then compile and interact with the graph using a TensorFlow `session`. However, this low-level API has a steep learning curve and does not let the programmer use native Python control-flow or debuggers. TensorFlow v1 uses control-flow nodes, such as loop condition, switch, and merge nodes to represent data flow, which increases the complexity of pattern matching required for optimizations \[YAB+18\]. To facilitate v1 usage, higher-level libraries and APIs were developed, such as TFLearn, Slim, SKflow, and Keras. TensorFlow v1 is under maintenance mode, and all new work is going into TensorFlow v2.

The most notable changes from TensorFlow v1 to v2 are: (1) the Keras APIs are default, (2) eager execution is default, and (3) improved organization for APIs, functions, and namespaces. TensorFlow provides a conversion tool to port the code from v1 to v2. To help determine whether an online document or code sample refers to v1 or v2, note that v1 uses the following objects not present in v2: `tf.enable_eager_execution`, `session.run`, `tf.placeholder`, and `feed_dict`.

The remainder of this section is as follows: We introduce the Keras APIs infrastructure, the Estimator API, and the tools to convert a dynamic graph constructed in Eager-style code to a static graph using `@tf.function` and `AutoGraph`. We highlight the tools for distributed training, the TensorBoard visualization tool, the Profiler tool, and the compilation TensorFlow infrastructure. Other TensorFlow libraries and tools with some adoption in industry are Tensor-Flow Hub, TensorFlow Extended (TFX), TensorFlow Lite (TFLite), and TensorFlow Probability (TFP). TensorFlow Hub provides an extensive service of prebuilt models; end-users can fine-tune them or use them as preprocessing layers (such as some of the embeddings available). TFX is an end-to-end series of connected libraries use to deploy DL pipelines; specifically, TFX provides the critical parts of the DL pipeline except for the model building and training (which is core TensorFlow). TFLite is a lite framework for on-device inference. TFP is a library for probabilistic reasoning and statistical analysis.

### 9.2.1 KERAS APIS

In TensorFlow v2, Keras is part of Tensor Flow (no need for a separate installation) and the default API. Keras is a widely adopted high-level API for defining and training models. Note that Keras has a reference implementation maintained as a separate project. TensorFlow includes a complete implementation of the Keras API (in the `tf.keras` module) with some enhancements.

A Keras model (and its superclass, `tf.Module`) is a way to store, access, and save variables. Keras is more opinionated than `tf.Module` about functionality; it provides abundant built-in support for ML/DL workflows. `tf.Module`, by contrast, is lightweight and unopinionated; it is used as the base class for Sonnet, DeepMind’s high-level API built on top of TensorFlow.

TensorFlow v2 provides the Keras Sequential API and Keras Functional API for declarative programming, and the Keras Subclassing API for imperative programming. The styles are interoperable, allowing the programmer to mix and match. The Keras API abstracts many of the complexities of the low-level APIs, facilitating prototyping and debugging models. Note that the Sequential and Functional APIs may feel imperative, and developers may not realize they are using a symbolic programming style. Note that Keras models, saved with the `SavedModel` format, contain (among other things) a `graphdef` and weights, so they serve the same function as the saved graphs in TensorFlow v1 for most uses. [Table 9.2](#19_Chapter09.xhtml#tab9-2) shows the pros and cons of these APIs.

The Keras Sequential API is used when the model does not have branches, and each layer has one tensor input and one tensor output. The Keras Functional API is used for directed acyclic graphs (DAGs), where each layer may have multiple tensor inputs or outputs, shared layers, or nonsequential data flow, such as in residual connections. The Keras Subclassing API is used for imperative programming; the programmer defines a new class that inherits and extends the Keras `Model` class defined by the framework. This class imperatively defines a function with the model and a function with the forward pass (the backward pass is generated automatically). The low-level API from TensorFlow v1 is still available to use in TensorFlow v2.

Table 9.2: Pros and cons of the programming styles offered in TensorFlow v2

| API || PROS || CONS |
| --- | --- | --- |
| Low-level || Maximum control || Difficult to debugNot pythonicSteep learning curve |
| Sequential || Simplest API || Sequential models only |
| Functional || Simple API  
Widely adopted || Static graphs only |
| Subclassing || PythonicHigh flexibilityDynamic and static graphs`@tf.function` ([Section 9.2](#19_Chapter09.xhtml#sub9-2).3)Similar to PyTorch API || Slightly more complex API |
