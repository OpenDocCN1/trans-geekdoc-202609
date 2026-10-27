
Because he created the genre of detective fiction, I’d like to think Poe would have enjoyed the work that went into solving the “Mystery of the Incorrect Letter Frequencies.”

David Kahn pointed out several other errors in The Gold Bug that have nothing to do with cryptography.24 Read the whole story and see how many you can find.

Other authors have made mistakes in their explanations of cryptanalysis. I came across an amusing example when I thought I was reading something far removed from crypto. If you can understand a little German, check out Das Geheimnis im Elbtunnel by Heinrich Wolff (National Textbook Company, 1988). A familiarity with vowel recognition algorithms (see Section 1.12) shows that the detective in this tale isn’t much better than Poe’s protagonist.

In Honoré de Balzac’s The Physiology of Marriage (published in 1829 as part of his Human Comedy), the author includes four pages of nonsense.25 This consisted of meaningless combinations of letters, as well as upside-down letters and punctuation. In the years since it first appeared, it has never been deciphered and it is widely believed among cryptanalysts that Balzac might have been blowing a little smoke. In fact, the nonsense pages changed from one edition to the next.

This nitpicking isn’t meant to detract from Poe’s greatness. Generations of cryptologists trace their interest in this subject back to reading “The Gold Bug” as children, and I will have more to say about Poe’s cipher challenge in Chapter 2. For now, note that Poe placed a hidden message in the following sonnet. Can you find it? The solution is given at the end of this chapter.

### An Enigma (1848)

by Edgar Allan Poe

> “Seldom we find,” says Solomon Don Dunce,
> “Half an idea in the profoundest sonnet.
> Through all the flimsy things we see at once
> As easily as through a Naples bonnet-
> Trash of all trash!—how can a lady don it?
> Yet heavier far than your Petrarchan stuff-
> Owl-downy nonsense that the faintest puff
> Twirls into trunk-paper the while you con it.”
> And, veritably, Sol is right enough.
> The general tuckermanities are arrant
> Bubbles—ephemeral and so transparent-
> But this is, now—you may depend upon it-
> Stable, opaque, immortal—all by dint
> Of the dear names that he concealed within’t.

## 1.8 Arthur Conan Doyle

Among cryptologists, the best known Sherlock Holmes story is “The Adventure of the Dancing Men” (1903).26 In this story, the cipher messages that Holmes attempts to crack have the letters replaced by dancing men; hence, the title of the tale. The ciphertexts are reproduced in Figure 1.8.

24 Kahn, David, The Codebreakers, second edition, Scribner, New York, 1996, pp. 790–791.

25 Kahn, David, The Codebreakers, second edition, Scribner, New York, 1996, p. 781.

26 Available online at http://sherlock-holm.es/stories/pdf/a4/1-sided/danc.pdf.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_41_0.png)

### Figure 1.8 Ciphertexts found in “The Adventure of the Dancing Men.”

We’ll develop techniques for breaking such ciphers later in this chapter, but let’s make a few simple observations now. First, observe that either the messages consist of very long words or word spacing has been disguised. Assuming the latter, either we have spacing eliminated completely or a special character represents the space. If a special symbol designates the space, it should be of very high frequency, but the highest frequency symbol in the ciphertexts sometimes appears at the end of a message. This would be pointless if it really represented a space.

Finally, we hit upon the idea that the flags represent the spaces. This makes our task much easier, as we now have word divisions. However, there are still some complicating factors. The messages are short, turn out to include proper names and locations (not just words you’d find in a dictionary) and there’s at least one typo present! The number of typos varies from edition to edition, but all have at least one!

Holmes never mentioned the typos, so one may assume that they were errors made by Doyle and/or the printers and not intended to make things more difficult. Anyone attempting to decipher a message must be able to deal with typos. These occur frequently in real-world messages. They can be caused by a careless encipherer or by problems in transmission. “Morse mutilation” is a term sometimes used to describe a message received in Morse code with errors arising from the transmission process.

Leo Marks, who was in charge of the Special Operations Executive (SOE) code and cipher group during World War II,27 frequently had to contend with “indecipherables” arising from agents in occupied Europe improperly enciphering. When he began in 1942, about 25% of incoming messages were indecipherable for one reason or another. At that time, only 3% were recovered, but Marks gave lectures on recovery techniques to his team and developed new methods. The

27 The Special Operations Executive was roughly the British equivalent of America’s Office of Strategic Services (OSS). They ran risky operations behind enemy lines.

number of solutions quickly rose to a peak of 92% and finally settled at an average of 80%. An individual message required an average of 2,000 attempted decipherments before Marks’s team hit upon the real error.[^28] It was worth the effort, for the only alternative was to have the agent resend the message, a risky activity with Nazis constantly on the lookout with direction-finding equipment for agents transmitting radio messages. A second attempt at transmission could easily result in capture and torture for the agent.

More recently, a copycat killer nicknamed Zodiac II sent an enciphered message to the *New York Post*. In order to get the correct decipherment, the cryptanalyst must grapple with some typos the killer made. See the online exercises for this cipher.

Sherlock Holmes, of course, was able to break the dancing men cipher completely and compose a message of his own using it ([Figure 1.9](#figure-1-9)).

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_42_0.png)

**Figure 1.9**  Sherlock Holmes’s dancing men ciphertext.

Holmes’s adversary in this tale had no idea that the message was from Holmes and this deception led to his capture. So, the story raises an issue that we’ll visit again in this book. Namely, how can we be sure that the message comes from the person we think it does? Holmes was able to impersonate another, because he learned the secret of the cipher, but in an ideal system this would not be possible.

Many agents were captured and impersonated over the course of World War II. In one instance, when it was suspected that a particular SOE agent had been compromised and that a Nazi was carrying out his end of the radio conversation, a test was devised to ascertain the truth. The suspicious British radio operator signed off on his message to the agent with HH, short for Heil Hitler. This was a standard sort of “goodbye” among the Nazis and the operator abroad responded automatically with HH, giving himself away.[^29]

Was Doyle’s use of dancing men to represent letters as creative as it might seem? It turns out that these fellows had been protecting messages long before Doyle wrote his story. When confronted with previous uses, he chalked it up to coincidence.[^30] Doyle’s dancing men are also reminiscent of some figures in a lost script, known as Rongorongo, which was used by the people of Easter Island and, oddly, resembles Indus Valley script, another indecipherable at the moment ([Figure 1.10](#figure-1-10)). The idea that there’s a connection between the two scripts is not backed by the leading experts, as the two cultures were widely separated, not only in terms of distance but also in time.

Although such topics are only treated in passing here, deciphering lost scripts attracts the interest of a decent number of cryptologists. See the References and Further Reading section at the end of this chapter for papers *Cryptologia* has published on Rongorongo script.

“The Adventure of the Dancing Men” is not the only story in which Doyle’s detective encountered cryptology. Another is discussed in [Section 1.21](#section-1-21).
