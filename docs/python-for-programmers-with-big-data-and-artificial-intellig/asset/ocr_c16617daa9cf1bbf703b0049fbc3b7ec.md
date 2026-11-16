```
38
39  # Step 7: Transcribe the Spanish speech to Spanish text
40  spanish = speech_to_text(
41      file_name='spanishresponse.wav', model_id='es-ES_BroadbandMode.
42  print('Spanish response:', spanish)
43
44  # Step 8: Translate the Spanish text into English text
45  english = translate(text_to_translate=spanish, model='es-en')
46  print('English response:', english)
47
48  # Step 9: Synthesize the English text into English speech
49  text_to_speech(text_to_speak=english,
50      voice_to_use='en-US_AllisonVoice',
51      file_name='englishresponse.wav')
52
53  # Step 10: Play the English audio
54  play_audio(file_name='englishresponse.wav')
55
```

ow let's implement the functions we call from **Steps 1** through **10**.

# Function speech_to_text

To access Watson's Speech to Text service, function speech_to_text (lines 56–87) creates a SpeechToTextV1 object named stt (short for speech-to-text), passing as the argument the API key you set up earlier. The with statement (lines 62–65) opens the audio file specified by the file_name parameter and assigns the resulting file object to audio_file. The open mode 'rb' indicates that we'll read (r) binary data (b)—audio files are stored as bytes in binary format. Next, lines 64–65 use the SpeechToTextV1 object's recognize method to invoke the Speech to Text service. The method receives three keyword arguments:

+   • audio is the file (audio_file) to pass to the Speech to Text service.

+   • content_type is the media type of the file’s contents—'audio/wav' indicates that this is an audio file stored in WAV format.⁵

⁵Media types were formerly known as MIME (Multipurpose Internet Mail Extensions) typesa standard that specifies data formats, which programs can use to interpret data correctly.

+   • model indicates which spoken language model the service will use to recognize the speech and transcribe it to text. This app uses predefined models—either 'en-US_BroadbandModel' (for English) or 'es-ES_BroadbandModel' (for