Megatron-LM has been used for many large model training projects, such as BERT, GPT, and the Biomedical domain language model. Its scalable architecture can be used to train models with trillions of parameters.

# DeepSpeed overview

DeepSpeed is an open source training framework developed by Microsoft. Similar to Megatron-LM, DeepSpeed also supports tensor slicing (another name for splitting tensors) parallelism, pipeline parallelism, and data parallelism.

DeepSpeed implements micro-batched pipeline model parallelism, when a batch is broken into micro-batches to be processed by different devices in parallel. Specifically, DeepSpeed implements interleaved pipeline parallelism to optimize resource efficiency and utilization.

Similar to Megatron-LM, DeepSpeed can use data parallelism, pipeline model parallelism, and tensor parallelism to train extremely large deep neural networks. This is also known as DeepSpeed 3D parallelism.

One capability of the DeepSpeed framework is its Zero Redundancy Optimizer (ZeRO). ZeRO is capable of managing memory efficiently by partitioning parameters, optimizer states, and gradients across devices instead of keeping a copy in all devices. The partitions are brought together at runtime when needed. This allows ZeRO to reduce the memory footprint by eight times compared to regular data parallelism techniques. ZeRO is also capable of using CPU and GPU memory together to train large models.

The attention-based mechanism is widely adopted in DL models, such as the transformer model, to address text and image inputs. However, its ability to address long input sequences is limited due to its large memory and compute requirements. DeepSpeed helps alleviate this issue with its implementation of a sparse attention kernel – a technology that reduces the compute and memory requirements of attention computation by block-sparse computation.

One major bottleneck in large-scale distributed training is the communication overhead due to gradients sharing and updates. Communication compression, such as 1-bit compression, has been adopted as an effective mechanism to reduce communication overhead. DeepSpeed has an implementation of a 1-bit Adam optimizer, which can reduce the communication overhead by up to five times to improve the training speed. 1-bit compression works by representing each number using 1 bit, combined with error compensation, which remembers the error during gradient compression and adds the error back to the next step to compensate for the error.