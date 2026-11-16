Lines 103–109 could be replaced with the more concise statement

lick here to view code image

```
return translated_text['translations'][0]['translation']
```

but again, we prefer the separate simpler statements.

# Function text_to_speech

To access the Watson Text to Speech service, function text_to_speech (lines 113–122) creates a TextToSpeechV1 object named tts (short for text-to-speech), passing as the argument the API key you set up earlier. The with statement opens the file specified by file_name and associates the file with the name audio_file. The mode 'wb' opens the file for writing (w) in binary (b) format. We'll write into that file the contents of the audio returned by the Speech to Text service.

lick here to view code image

```
113 def text_to_speech(text_to_speak, voice_to_use, file_name):
114     """Use Watson Text to Speech to convert text to specified voice
115     and save to a WAV file."""
116     # create Text to Speech client
117     tts = TextToSpeechV1(iam_apikey=keys.text_to_speech_key)
118
119     # open file and write the synthesized audio content into the fi
120     with open(file_name, 'wb') as audio_file:
121         audio_file.write(tts.synthesize(text_to_speak,
122             accept='audio/wav', voice=voice_to_use).get_result().cont
123
```

Lines 121–122 call two methods. First, we invoke the Speech to Text service by calling the TextToSpeechV1 object's synthesize method, passing three arguments:

+   text_to_speak is the string to speak.

+   the keyword argument accept is the media type indicating the audio format the Speech to Text service should return—again, 'audio/wav' indicates an audio file in WAV format.

+   the keyword argument voice is one of the Speech to Text service's predefined voices. In this app, we'll use 'en-US_AllisonVoice' to speak English text and