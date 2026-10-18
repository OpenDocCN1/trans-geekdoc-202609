
> > > Could an encoder-decoder network attain the necessary mental models and real-world knowledge simply by exposure to a larger training set and more network layers, or is something fundamentally different needed? This is still an open question and is the subject of intense debate in the AI community. For now, I’ll simply say that while neural machine translation can be impressively effective and useful in many applications, the translations, without post-editing by knowledgeable humans, are still fundamentally unreliable. If you use machine translation—and I do so myself—you should take the results with a grain of salt. In fact, when I had Google Translate translate “take it with a grain of salt” from English to Chinese and then back to English, it told me to “bring a salt bar.” That might be a better idea.

## Translating Images to Sentences

Here’s a crazy idea: in addition to translating between languages, could something like an encoder-decoder pair of neural networks be trained to translate from *images* to language? The idea would be to use one network to encode an image and another network to “translate” that image into a sentence describing the content of the image. After all, isn’t creating an image caption just another kind of “translation”—this time between the “language” of an image and the language of a caption?

It turns out this idea is not so crazy. In 2015 two groups—one from Google and the other from Stanford University—independently published very similar papers on this topic at the same computer-vision conference.^()

[Figure 39](#chapter12.xhtml#fig39) gives a sketch of how the Show and Tell system works.^()

How does this system learn to produce reasonable captions? Recall that for language translation, the training data consists of pairs of sentences, in which the first sentence in a pair is in the source language and the second is a human translator’s translation into the target language. In the case of image captioning, each training example consists of an image paired with a caption. The images were downloaded from repositories such as Flickr.com, and the captions for these images were produced by humans—namely, Amazon Mechanical Turk workers, who were hired by Google for this study. Because captions can be so variable, each image was given a caption by five different people. Thus, each image appears in the training set five times, each time paired with a different caption. [Figure 40](#chapter12.xhtml#fig40) shows a sample training image and the captions given by the Mechanical Turk workers.

![FIGURE 39: Sketch of Google’s automated image-captioning system](images/Figure39.jpg)

FIGURE 39: Sketch of Google’s automated image-captioning system

![FIGURE 40: Sample training image with captions given by Amazon Mechanical Turk workers](images/Figure40.jpg)

FIGURE 40: Sample training image with captions given by Amazon Mechanical Turk workers

The Show and Tell decoder network was trained on about eighty thousand image-caption pairs. [Figure 41](#chapter12.xhtml#fig41) gives a few examples of captions that the trained Show and Tell system generated on test images—that is, images that were not in its training set.

It’s hard not to be dazzled, and maybe a bit stunned, that a machine can take in images in the form of raw pixels and produce such accurate captions. That’s certainly how I felt when I first read about these results in *The New York Times*. The author of that article, the journalist John Markoff, wrote a careful description: “Two groups of scientists, working independently, have created artificial intelligence software capable of recognizing and describing the content of photographs and videos with far greater accuracy than ever before, sometimes even mimicking human levels of understanding.”^() ![FIGURE 41: Four (accurate) automatically produced captions from Google’s Show and Tell system](images/Figure41.jpg)

FIGURE 41: Four (accurate) automatically produced captions from Google’s Show and Tell system

Other journalists were not so restrained. “Google’s AI Can Now Caption Images Almost as Well as Humans,” proclaimed one news website.^() ![FIGURE 42: Not-so-accurate captions from Google’s Show and Tell system and Microsoft’s CaptionBot](images/Figure42.jpg)

FIGURE 42: Not-so-accurate captions from Google’s Show and Tell system and Microsoft’s CaptionBot

But not so fast. Automated image captioning suffers from the same kind of bipolar performance seen in language translation. When it’s good, as in [figure 41](#chapter12.xhtml#fig41), it seems almost magical. But its errors can range from slightly off to completely nonsensical. [Figure 42](#chapter12.xhtml#fig42) shows some examples from this range. These wrongheaded captions might make you laugh, but if you are a blind person who can’t see the photo, it would be hard to know if the caption you are given is one of the good ones or one of the bad ones.

While Microsoft’s CaptionBot says it can “understand the content of any photograph,” the problem is that the opposite is true. Even when their captions are correct, these systems don’t understand photos in the sense that humans understand them. When I gave Microsoft’s CaptionBot the “soldier in the airport with dog” photo from chapter 4, the system’s output was “A man holding a dog.” Sort of. Except for the “man” part. But this caption misses everything interesting about the photo, everything about the way it speaks to us, to our experience, emotions, and knowledge about the world. That is, it misses the *meaning* of the photo.

I’m certain that these systems will improve as researchers apply more data and new algorithms. However, I believe that the fundamental lack of *understanding* in caption-generating networks inevitably means that, as in language translation, these systems will remain untrustworthy. They will work very well in some cases but fail spectacularly in others. Moreover, even when they are mostly correct, they will often fail to capture the gist of an image depicting a situation rich with meaning.

NLP systems that classify the sentiment of sentences, translate documents, and describe photos, while still far from human abilities at these tasks, are useful for many real-world purposes, and thus have become very profitable for their developers. But the ultimate dream of NLP researchers is a machine that can fluently and flexibly interact with its users in real time—in particular, converse with them and answer their questions. The next chapter explores the challenges of creating AI systems that can deal with all of our queries.

# [13](contents.xhtml#c_ch13)

# [Ask Me Anything](contents.xhtml#c_ch13)

# USS `Enterprise`. Stardate: 42402.7

> LIEUTENANT COMMANDER DATA: *Computer, I wish to know more about humor. Why certain combinations of words and actions make humans laugh.*

> 

> COMPUTER: *Source material on that subject is extensive. Please specify.*

> 

> LIEUTENANT COMMANDER DATA: *Animated presentation, humanoid. Interaction required.*

> 

> COMPUTER: *Physical humor, cerebral, or general raconteur?*

> 

> LIEUTENANT COMMANDER DATA: *Of all performers available, who is considered funniest?*

> 

> COMPUTER: *Twenty-third century Stan Orega specialized in jokes about quantum mathematics.*

> 

> LIEUTENANT COMMANDER DATA: *No. Too esoteric. More generic.*

> 

> COMPUTER: *Accessing.*

> 

> *(A list of names is displayed.)*

> 

> —*Star Trek: The Next Generation*, season 2, episode 4: “The Outrageous Okona”^()

> 

> The computer on the starship `Enterprise`—with its vast store of knowledge and seamless understanding of the questions put to it—has long been a lodestar for human-computer interaction, envied by *Star Trek* fans and AI researchers alike (and the intersection between these groups is, shall we say, not insignificant).

> 
