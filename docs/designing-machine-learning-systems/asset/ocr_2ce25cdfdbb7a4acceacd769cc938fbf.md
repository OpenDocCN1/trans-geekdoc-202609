Batch prediction is a workaround for when online prediction isn't cheap enough or isn't fast enough. Why generate one million predictions in advance and worry about storing and retrieving them if you can generate each prediction as needed at the exact same cost and same speed?

As hardware becomes more customized and powerful and better techniques are being developed to allow faster, cheaper online predictions, online prediction might become the default.

In recent years, companies have made significant investments to move from batch prediction to online prediction. To overcome the latency challenge of online prediction, two components are required:

+   - A (near) real-time pipeline that can work with incoming data, extract streaming features (if needed), input them into a model, and return a prediction in near real time. A streaming pipeline with real-time transport and a stream computation engine can help with that.
+   - A model that can generate predictions at a speed acceptable to its end users. For most consumer apps, this means milliseconds.

We’ve discussed stream processing in Chapter 3. We’ll continue discussing the unification of the stream pipeline with the batch pipeline in the next section. Then we’ll discuss how to speed up inference in the section “Model optimization” on page 216.

# Unifying Batch Pipeline and Streaming Pipeline

Batch prediction is largely a product of legacy systems. In the last decade, big data processing has been dominated by batch systems like MapReduce and Spark, which allow us to periodically process a large amount of data very efficiently. When companies started with ML, they leveraged their existing batch systems to make predictions. When these companies want to use streaming features for their online prediction, they need to build a separate streaming pipeline. Let’s go through an example to make this more concrete.