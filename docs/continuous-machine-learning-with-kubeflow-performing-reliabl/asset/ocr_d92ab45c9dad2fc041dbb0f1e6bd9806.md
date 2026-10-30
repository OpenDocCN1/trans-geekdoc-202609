![](bbox=[0.12, 0.06, 0.88, 0.31])

# Figure 2.11: Service account cloud storage selection

The preceding screenshot shows the role we will give for the service account.

Similarly, we will create the Docker Image, and add the service account json key.

# Docker:

```
FROM python:3.7-slim-stretch
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get-y install gcc mono-mcs g++ git curl && \
rm-rf /var/lib/apt/lists/*
RUN mkdir/app
WORKDIR /app
COPY service_account_iam.json
```