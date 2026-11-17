![](bbox=[0.125, 0.09, 0.87, 0.2])

Figure 9.13 – Finding the best set of hyperparameters

As you can see, SageMaker is very intuitive, and once you know the main concepts behind model optimization, playing with SageMaker should be easier. Now, you understand how to use SageMaker for our specific needs. In the next section, you will explore how to select the instance type for various use cases and the security of our notebooks.

# Choosing instance types in Amazon SageMaker

SageMaker uses a pay-for-usage model. There is no minimum fee for it.

When you think about instances on SageMaker, it all starts with an EC2 instance. This instance is responsible for all your processing. It’s a managed EC2 instance. These instances won’t show up in the EC2 console and cannot be SSHer either. The names of this instance type start with ml.

SageMaker offers instances of the following families:

+   • The t family: This is the burstable CPU family. With this family, you get a balanced ratio of CPU and memory. This means that if you have a long-running training job, then you lose performance over time as you spend the CPU credits. If you have very small jobs, then they are cost-effective. For example, if you want a notebook instance to launch training jobs, then this family is the most appropriate and cost-effective.
+   • The m family: In the previous family, you saw that CPU credits are consumed faster due to their burstable nature. If you have a long-running ML job that requires constant throughput, then this is the right family. It comes with a similar CPU and memory ratio as the t family.
+   • The r family: This is a memory-optimized family. When do you need this? Well, imagine a use case where you have to load the data in memory and do some data engineering on the data. In this scenario, you will require more memory and your job will be memory-optimized.
+   • The c family: c-family instances are compute-optimized. This is a requirement for jobs that need higher compute power and less memory to store the data. If you refer to the following table, c5.2x large has 8 vCPU and 16 GiB memory, which makes it compute-optimized with less memory. For example, if a use case needs to be tested on fewer records and it is compute savvy, then this instance family is the to-go option to get some sample records from a huge DataFrame and test your algorithm.
+   • The p family: This is a GPU family that supports accelerated computing jobs such as training and inference. Notably, p-family instances are ideal for handling large, distributed training jobs that result in less time required for training and are thus much more cost-effective. The p3/p3dn GPU compute instance can go up to 1 petaFLOP per second compute with up to 256 GB of GPU memory and 100 Gbps (gigabits) of networking with 8x NVIDIA v100 GPUs. They are highly optimized for training and are not fully utilized for inference.