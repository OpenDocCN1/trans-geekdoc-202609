# 5.3 Blind Signatures

Eve, who is in the middle, watching this protocol, has even less information than Bob.

# Blind Signatures

With the completely blind signature protocol, Alice can have Bob sign anything; "Bob owes Alice a million dollars," "Bob owes Alice his first-born child," "Bob owes Alice a bag of chocolates. The possibilities are endless. This protocol is not useful in many applications.

However, there is a way that Bob can know what he is signing, while still maintaining the useful properties of a blind signature. The heart of this protocol is the cut-and-choose technique. Consider this example. Many people enter this country every day, and the Department of Immigration want to make sure they are not smuggling cocaine. The officials could search everyone, but instead they use a probabilistic solution. They will search one-tenth of the people coming in. One person in ten has belongings inspected, the other nine get untouched. Chronic smugglers will get away with their misdeeds most of the time, but they have a ten percent chance of getting caught. And if the court system is effective, the penalty for getting caught could more than wipe out the gains from the other side.

If the Department of Immigration want to increase the odds of smuggling, they have want to decrease the odds, they have to search fewer people. By manipulating the probabilities, they can control how successful the protocol is in catching smugglers.

The blind signature protocol works in a similar manner. Bob will be given a large pile of blind documents. He will open, that is examine, all but one and then sign the last.

Think of the blind document as being in an envelope. The process of blinding the document is putting the document in an envelope and the process of removing the blinding factor is opening the envelope. When the document is in an envelope, nobody can read it. The document is signed by a piece of carbon paper in the envelope: when the signer signs through the envelope, his signature goes through the carbon paper and signs the document below.

This scenario involves a group of counterintelligence agents. Their identities are secret; even the counterintelligence agents know who they are. The agency's director wants to give each agent a signed document stating: "The bearer of this signed document (insert agent's cover name), has diplomatic immunity." Each agent has his own list of cover names, so the agency can't hand out signed documents. The agents do not want to send their cover names to the agency; the enemy might have corrupted the agency's computer. On the other hand, the agency doesn't want to blindly sign any document an agent gets. A clever agent might substitute a message like: "Agent (name) has retired and collects a million-dollar-a-year pension. Signed, Mr. President." In this case, blind signatures could be useful.

Assume that all the agents have 10 possible cover names, which they have chosen themselves and which no one else knows. Also assume that the agents don't