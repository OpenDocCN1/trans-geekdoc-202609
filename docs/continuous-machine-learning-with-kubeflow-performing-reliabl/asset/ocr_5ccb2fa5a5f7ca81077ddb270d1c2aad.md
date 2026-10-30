# 8.4 Building the Framework for Streamlit for OpenCV models

To build a framework for Streamlit for OpenCV models, complete the following steps:

**STEP 1:** Load all the Dependency for the Computer Vision Model and Streamlit.

```
import streamlit as st
import cv2
import numpy as np
from PIL import Image
from matplotlib import pyplot as plt
import io
import cv2 as cv
import os
import glob
import requests
from bs4 import BeautifulSoup
import urllib.request
import random
import pandas as pd
from io import BytesIO
import ssl
ssl._create_default_https_context = ssl._create_unverified_context
```