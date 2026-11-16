
record_audio then records audio for five seconds and stores it in the file english.wav:

Click here to view code image

```
def run_translator():
    """Calls the functions that interact with Watson services."""
    # Step 1: Prompt for then record English speech into an audio file
    input('Press Enter then ask your question in English')
    record_audio('english.wav')
```

In Step 2, we call function speech_to_text, passing the file english.wav for transcription and telling the Speech to Text service to transcribe the text using its predefined model 'en-US_BroadbandModel'.4 We then display the transcribed text:

4For most languages, the Watson Speech to Text service supports broadband and narrowband models. Each has to do with the audio quality. For audio captured at 16 kHz and higher, IBM recommends using the broadband models. In this app, we capture the audio at 44.1 kHz.

Click here to view code image

```
# Step 2: Transcribe the English speech to English text
english = speech_to_text(
    file_name='english.wav', model_id='en-US_BroadbandModel')
print('English:', english)
```

In Step 3, we call function translate, passing the transcribed text from Step 2 as the text to translate. Here we tell the Language Translator service to translate the text using its predefined model 'en-es' to translate from English (en) to Spanish (es). We then display the Spanish translation:

Click here to view code image

```
# Step 3: Translate the English text into Spanish text
spanish = translate(text_to_translate=english, model='en-es')
print('Spanish:', spanish)
```

In Step 4, we call function text_to_speech, passing the Spanish text from Step 3 for the Text to Speech service to speak using its voice 'es-US_SofiaVoice'. We also specify the file in which the audio should be saved:

Click here to view code image

```
28    # Step 4: Synthesize the Spanish text into Spanish speech
29    text_to_speech(text_to_speak=spanish,   voice_to_use='es-US_SofiaVoice',
30           file_name='spanish.wav')
31
```

In Step 5, we call function play_audio to play the file 'spanish.wav', which contains the Spanish audio for the text we translated in Step 3.

Click here to view code image

```
32    # Step 5: Play the Spanish audio file
33    play_audio(file_name='spanish.wav')
34
```

Finally, Steps 6–10 repeat what we did in Steps 1–5, but for Spanish speech to English speech:

- Step 6 records the Spanish audio.
- Step 7 transcribes the Spanish audio to Spanish text using the Speech to Text service's predefined model 'es-ES_BroadbandModel'.
- Step 8 translates the Spanish text to English text using the Language Translator Service's 'es-en' (Spanish-to-English) model.
- Step 9 creates the English audio using the Text to Speech Service's voice 'en-US_AllisonVoice'.
- Step 10 plays the English audio.

Click here to view code image

```
35    # Step 6: Prompt for then record Spanish speech into an audio file
36    input('Press Enter then speak the Spanish answer')
37    record_audio('spanishresponse.wav')
38
39  # Step 7: Transcribe the Spanish speech to Spanish text
40  spanish = speech_to_text(
41      file_name='spanishresponse.wav', model_id='es-ES_BroadbandModel')
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

Now let's implement the functions we call from Steps 1 through 10.

### Function speech_to_text

To access Watson's Speech to Text service, function speech_to_text (lines 56–87) creates a SpeechToTextV1 object named stt (short for speech-to-text), passing as the argument the API key you set up earlier. The with statement (lines 62–65) opens the audio file specified by the file_name parameter and assigns the resulting file object to audio_file. The open mode 'rb' indicates that we'll read (r) binary data (b)—audio files are stored as bytes in binary format. Next, lines 64–65 use the SpeechToTextV1 object's recognize method to invoke the Speech to Text service. The method receives three keyword arguments:

- audio is the file (audio_file) to pass to the Speech to Text service.
- content_type is the media type of the file's contents—'audio/wav' indicates that this is an audio file stored in WAV format.⁵

⁵Media types were formerly known as MIME (Multipurpose Internet Mail Extensions) types—a standard that specifies data formats, which programs can use to interpret data correctly.

- model indicates which spoken language model the service will use to recognize the speech and transcribe it to text. This app uses predefined models—either 'en-US_BroadbandModel' (for English) or 'es-ES_BroadbandModel' (for

Click here to view code image

```
56 def speech_to_text(file_name, model_id):
57     """Use Watson Speech to Text to convert audio file to text."""
58     # create Watson Speech to Text client
59     stt = SpeechToTextV1(iam_apikey=keys.speech_to_text_key)
60
61     # open the audio file
62     with open(file_name, 'rb') as audio_file:
63         # pass the file to Watson for transcription
64         result = stt.recognize(audio=audio_file,
65                              content_type='audio/wav', model=model_id).get_result()
66
67     # Get the 'results' list. This may contain intermediate and final
68     # results, depending on method recognize's arguments. We asked
69     # for only final results, so this list contains one element.
70     results_list = result['results']
71
72     # Get the final speech recognition result--the list's only element
73     speech_recognition_result = results_list[0]
74
75     # Get the 'alternatives' list. This may contain multiple alternatives
76     # transcriptions, depending on method recognize's arguments. We
77     # did not ask for alternatives, so this list contains one element.
78     alternatives_list = speech_recognition_result['alternatives']
79
80     # Get the only alternative transcription from alternatives_list.
81     first_alternative = alternatives_list[0]
82
83     # Get the 'transcript' key's value, which contains the audio's
84     # text transcription.
85     transcript = first_alternative['transcript']
86
87     return transcript  # return the audio's text transcription
```

The `recognize` method returns a DetailedResponse object. Its getResult method returns a JSON document containing the transcribed text, which we store in result. The JSON will look similar to the following but depends on the question you ask:

```
{
  "results": [
    {
      "alternatives": [
        {
          "confidence": 0.983,
          "transcript": "where is the closest bathroom "
        }
      ],
      "final": true
    }
  ],
  "result_index": 0
}
```

The JSON contains nested dictionaries and lists. To simplify navigating this data structure, lines 70–85 use separate small statements to "pick off" one piece at a time until we get the transcribed text—"where is the closest bathroom ", which we then return. The boxes around portions of the JSON and the line numbers in each box correspond to the statements in lines 70–85. The statements operate as follows:

- Line 70 assigns to results_list the list associated with the key 'results':

```
results_list = result['results']
```

Depending on the arguments you pass to method recognize, this list may contain intermediate and final results. Intermediate results might be useful, for example, if you were transcribing live audio, such as a newscast. We asked for only final results, so this list contains one element.⁶

⁶For method recognizes arguments and JSON response details, see https://www.ibm.com/watson/developercloud/speech-to-text/api/v1/python.html?python#recognize-sessionless.

- Line 73 assigns to speech_recognition_result the final speech-recognition result—the only element in results_list:

```
speech_recognition_result = results_list[0]
```

- Line 78
