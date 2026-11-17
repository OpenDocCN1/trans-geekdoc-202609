# Batch transform job

In this **scenario**, you have a large dataset, and you want to perform batch inference on the entire dataset using a trained model.

# Solution

Use SageMaker batch transform to process the entire dataset in a batch.

# Steps

+   1. Create a SageMaker transformer.
+   2. Start the batch transform job.

# Example code snippet

```
from sagemaker.transformer import Transformer
transformer = Transformer(model_name='your-model-name',
                        instance_count=1,
                        instance_type='ml.m4.xlarge',
                        strategy='SingleRecord',
                        assemble_with='Line',
                        output_path='s3://your-s3-bucket/output')
transformer.transform('s3://your-s3-bucket/input/data.csv', content_type='text/csv')
transformer.wait()
```

# Multi-model endpoint deployment

In this **scenario**, you have multiple versions of a model, and you want to deploy them on a single endpoint for A/B testing or gradual rollout.

# Solution

Use SageMaker multi-model endpoints to deploy and manage multiple models on a single endpoint.

# Steps

+   1. Create and train multiple models.
+   2. Create a SageMaker multi-model.
+   3. Deploy the multi-model to an endpoint.

# Example code snippet

```
from sagemaker.multimodel import MultiModel
```