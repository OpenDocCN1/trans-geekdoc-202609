So, in the “main” function, the KFServingSampleModel Class will take the name of that deployment; keep a note of that and apply to the yaml file; here it is "kfserving-breast-model".

# Docker:

```
```docker
FROM python:3.7-slim-stretch
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get -y install gcc mono-mcs g++ git
curl bash && \
rm -rf /var/lib/apt/lists/*
RUN mkdir /app
WORKDIR /app
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
RUN python get-pip.py && rm get-pip.py && pip install --upgrade
pip
RUN apt-get update && yes | apt-get upgrade
RUN apt-get install -y libsm6 libxext6 libxrender-dev protobuf-
compiler python-pil python-lxml python-pip python-dev git protobuf-
compiler python-pil python-lxml
ADD requirements.txt /app/requirements.txt
RUN pip3 install -r requirements.txt
ADD brainserving.py /app/brainserving.py
COPY service_account_iam.json service_account_iam.json
ENV
GOOGLE_APPLICATION_CREDENTIALS="service_account_iam.json"
CMD ["python","brainserving.py"]
```
```