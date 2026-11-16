'es-US_SofiaVoice' to speak Spanish text. Watson provides many male and female voices across various languages. 8

8 or a complete list, see https://www.ibm.com/watson/developercloud/text-to-speech/api/v1/python.html?python#get-voice.Try experimenting with other voices.

Watson's DetailedResponse contains the spoken text audio file, accessible via get_result. We access the returned file's content attribute to get the bytes of the audio and pass them to the audio_file object's write method to output the bytes to a .wav file.

# Function record_audio

The pyaudio module enables you to record audio from the microphone. The function record_audio (lines 124–154) defines several constants (lines 126–130) used to configure the stream of audio information coming from your computer’s microphone. We used the settings from the pyaudio module’s online documentation:

+   FRAME_RATE—44100 frames-per-second represents 44.1 kHz, which is common for CD-quality audio.

+   CHUNK—1024 is the number of frames streamed into the program at a time.

+   FORMAT—pyaudio.paInt16 is the size of each frame (in this case, 16-bit or 2-byte integers).

+   CHANNELS—2 is the number of samples per frame.

+   SECONDS—5 is the number of seconds for which we’ll record audio in this app.

lick here to view code image

```
124 def record_audio(file_name):
125     """Use pyaudio to record 5 seconds of  audio to a WAV file."""
126     FRAME_RATE = 44100  # number of frames per second
127     CHUNK = 1024  # number of frames read at a time
128     FORMAT = pyaudio.paInt16  # each frame is a 16-bit (2-byte) into
129     CHANNELS = 2  # 2 samples per frame
130     SECONDS = 5  # total recording time
131
```