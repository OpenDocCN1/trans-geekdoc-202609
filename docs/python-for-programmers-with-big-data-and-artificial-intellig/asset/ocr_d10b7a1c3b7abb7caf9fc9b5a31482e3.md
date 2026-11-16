# # Retrieving Your Credentials

To view your credentials at any time, click the appropriate service instance at:

https://console.bluemix.net/dashboard/apps

# # 13.6.2 Test-Driving the App

Once you've added your credentials to the script, open an Anaconda Prompt (Windows), a Terminal (macOS/Linux) or a shell (Linux). Run the script ⁰ by executing the following command from the ch13 examples folder:

The pydub.playback module we use in this app issues a warning when you run our script. The warning has to do with module features we dont use and can be ignored. To eliminate this warning, you can install ffmpeg for Windows, macOS or Linux from https://www.ffmpeg.org.

```
ipython SimpleLanguageTranslator.py
```

# # Processing the Question

The app performs 10 steps, which we point out via comments in the code. When the app begins executing:

**Step 1** prompts for and records a question. First, the app displays:

```
Press Enter then ask your question in English
```

and waits for you to press Enter. When you do, the app displays:

```
Recording 5 seconds of audio
```

Speak your question. We said, "Where is the closest bathroom?" After five seconds, the app displays:

```
Recording complete
```

**Step 2** interacts with Watson's Speech to Text service to transcribe your audio to text and displays the result: