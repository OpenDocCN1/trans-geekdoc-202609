else:

return text, 0

```
import re
```

identifyAndRemoveEmailAddress('Immediately reply to some.one@somewhere.com and send the filled form to leader@somewhere.com')

‘Immediately reply to and send the filled form to ‘, 1)

# Detecting and treating hashtags and mentions in the text

We must decide how to treat hashtags and mentions like URLs and email addresses. Provided here is a function to remove hashtags and mentions. You may modify the function as per the requirement of the application.

```
import re
```

```
removeHashtagsAndMentions(text):

return re.sub('(@[A-Za-z0-9]+)|([^0-9A-Za-z t][A-Za-z0-9]+) |(\w+:\//\S+)', ‘, text)
```

removeHashtagsAndMentions('#MIT this is a test @Ramesh Harvard’)

‘this is a test Harvard’

# Dealing with emojis

In modern days, people use Emojis in the text quite frequently. Emojis are not only used in social media activities, but they are also frequently used in emails, SMS, WhatsApp messages, and even in articles. Information regarding Emojis is critical for some applications like Emotion Analysis. So, based on the application, it is necessary to decide whether to retain the information from Emojis in the text. If the information on Emojis needs to be retained, essential feature engineering must be conducted. In every situation, the Emois must be removed from the text before the text can be analyzed.