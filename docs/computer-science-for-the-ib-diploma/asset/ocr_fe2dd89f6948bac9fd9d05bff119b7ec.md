◆ Stereo: a method of sound reproduction that uses two or more audio channels to create the perception of sound coming from different directions, enhancing the sense of spatial depth and dimension.

compression attempts to reduce the file size by removing parts of the audio signal that are less noticeable to human senses, in this case the ears. There are both lossy and lossless types of compression used with audio. Lossless algorithms compress the data without any loss of quality, whereas lossy algorithms permanently remove audio that is less noticeable to the human ear on the recording.

+   - WAV (Waveform Audio File Format): uncompressed
+   - AIFF (Audio Interchange File Format): uncompressed
+   - MP3 (MPEG Audio Layer III): compressed (lossy)
+   - FLAC (Free Lossless Audio Codec): compressed (lossless)

# REVIEW QUESTIONS

+   1. What is the main difference between an analogue signal and a digital signal in the context of audio?
+   2. What is the process of converting an analogue audio signal into a digital signal called, and what does it involve?
+   3. Calculate the storage needed per minute for a 44.1 kHz, 16-bit stereo audio file.
+   4. Explain the difference between lossy and lossless audio compression and give an example of each type of format.

# PROGRAMMING EXERCISE

Explore audio files further using the code below. This will allow you to analyse the amplitude of any MP3 file. You will need to install the following libraries:

+   - soundfile
+   - numpy
+   - matplotlib
+   - scipy.

Run this command in your terminal: pip install soundfile numpy matplotlib scipy

```
```python
import soundfile as sf
import numpy as np
import matplotlib.pyplot as plt
from scipy.fftpack import fft
# Load the audio file
samples, sample_rate = sf.read("name_of_file.mp3")
# If stereo, select one channel
if samples.ndim > 1:
    samples = samples[:, 0]
# Visualize the waveform
plt.figure(figsize=(12, 6))
plt.plot(samples)
plt.title("Audio Waveform")
```
```