https://github.com/watson-developer-cloud/python-sdk/tree/master/examples

# # 13.6 CASE STUDY: TRAVELER'S COMPANION TRANSLATION APP

Suppose you’re traveling in a Spanish-speaking country, but you do not speak Spanish, and you need to communicate with someone who does not speak English. You could use a translation app to speak in English, and the app could translate that, then speak it in Spanish. The Spanish-speaking person could then respond, and the app could translate that and speak it to you in English.

Here, you’ll use three powerful IBM Watson services to implement such a traveler’s companion translation app,⁹ enabling people who speak different languages to converse in near real time. Combining services like this is known as creating a mashup. This app also uses simple file-processing capabilities that we introduced in the “Files and Exceptions” chapter.

⁹These services could change in the future. If they do, we’ll post updates on the books web page at ttp://www.deitel.com/books/IntroToPython.

# ## 13.6.1 Before You Run the App

You’ll build this app using the Lite (free) tiers of several IBM Watson services. Before executing the app, make sure that you’ve registered for an IBM Cloud account, as we discussed earlier in the chapter, so you can get credentials for each of the three services the app uses. Once you have your credentials (described below), you’ll insert them in our keys.py file (located in the ch13 examples folder) that we import into the example. Never share your credentials.

As you configure the services below, each service’s credentials page also shows you the service’s URL. These are the default URLs used by the Watson Developer Cloud Python SDK, so you do not need to copy them. In ection 13.6.3, we present the SimpleLanguageTranslator.py script and a detailed walkthrough of the code.

# ### Registering for the Speech to Text Service

This app uses the Watson Speech to Text service to transcribe English and Spanish audio files to English and Spanish text, respectively. To interact with the service, you must get a username and password. To do so:

+   1. **Create a Service Instance:** Go to