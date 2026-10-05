entry_point= "inference.py",
framework_version= "1.12"

predictor = model.deploy(instance_type="ml.m5.large")

# 5. Monitoring and auto-scaling:

+   - Amazon CloudWatch tracks inference latency,
  throughput, and failures.
- SageMaker Auto Scaling dynamically adjusts
  instances based on request volume.

# AI tool benefits (supporting layer)

While not part of the direct workflow steps, AI-powered
tools like ChatGPT and GitHub Copilot significantly
accelerate the development and deployment process:

+   - ChatGPT plays a key role in enhancing reliability and
  developer productivity across the deployment pipeline
  through the following capabilities:
  - Generates preprocessing handlers.
  - Troubleshoot container runtime errors.
  - Creates secure IAM policies.

+   - GitHub Copilot supports rapid prototyping and
  seamless integration by providing intelligent code
  suggestions and development assistance in the
  following ways:
  - Assists with SageMaker SDK integration.
  - Autocompletes boilerplate code.
  - Helps configure logging and monitoring.

# Comparison of use cases

The two deployment examples illustrate different control,
scalability, and automation trade-offs. The following table