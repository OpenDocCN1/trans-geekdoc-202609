a spectogram and worked with these spectogram images.

By now there is no package we can directly import but we can install the audio module with pip directly from the github repo. We’ll also need torchaudio.

```
!pip install git+https://github.com/rbracco/fastai_audio.git
```

Collecting git+https://github.com/rbracco/fastai_audio.git Cloning https://github.com/rbracco/fastai_audio.git to /tmp/pip-req-build-21aqvo91 Running command git clone -q https://github.com/rbracco/fastai_audio.git /tmp/pip-req-build-21aqvo91 Username for ‘https://github.com’: ^C

![](bbox=[0.16, 0.35, 0.88, 0.7])

# 20.2 The Audio Dataset

We will use a free audio dataset that contains about 2000 recordings from 4 different speakers saying each digit 5 times. First we need to download the data and build a custom extract function.

You can download the dataset from this url: https://public- datasets.fr a1.cdn.digitaloceanspaces.com/recordings.tar.gz