6,513,516,734,600,035,718,300,327,211,250,928,237,178,281,758,494,417, 357,560,
086,828,416,863,929,270,451,437,126,021,949,850,746,381

Moreover, the preceding number would be only one of two factors.

# Keys, Keyspace, and Key Management

In this section, you’ll learn how to describe the function of keys, the importance of keyspace size, and the requirements for adequate key management.

# Cryptographic Keys and Keyspace

You have been reading about keys for some time now. But what are they? A key is a value that is an input to a cryptosystem. The key participates in transforming the message in a particular manner. A well-designed cryptosystem produces different outputs of the same message for each key used. You can think about keys this way: A cipher performs a particular task, and a key gives the specific directions for how to do it.

Physical keys are similar to cryptographic keys, but they’re not the same. Many popular door locks have five tumblers, each with 10 possible positions. Thus there are 10^5, or 100,000, possible cuts for house keys. This gives a reasonable assurance that a person trying a random key in your front door won’t get in.

The set of all possible keys is a keyspace. Usually, although not always, the larger the keyspace, the more secure the algorithm. Let’s look at an example.

How large is the keyspace for a briefcase with two three-digit locks? Combinations run from 000–000 to 999–999, so there are 1,000,000 keys in the keyspace. Does this mean a thief would have to try 1 million combinations before guessing the correct combination? Not necessarily. A thief could be incredibly lucky and guess the correct combination on the first try. Alternatively, a thief could be incredibly unlucky and try every possible combination before finding the correct combination on the last try. On average, an attacker will guess the correct combination halfway through searching the keyspace. Does this mean that an attacker would need to try, on average, 500,000 combinations? If each attempt took two seconds, and the attacker worked nonstop day and night, he or she should need more than 11 days to open the briefcase. However, the actual resistance of a briefcase to brute-force attack is closer to 17 minutes! Why is this so?

It has to do with a weakness in the briefcase algorithm. Because there are two separate locks with 1,000 combinations each, on average it takes 500 attempts to guess each subcombination. After finding the left combination, the attacker proceeds to the right combination. At most, the attacker will need to try 1,000 + 1,000, or 2,000, combinations. On average, however, the attacker will need to try only 1,000. At two seconds each, this would take 16 minutes and 40 seconds.

This illustrates nicely that increased keyspace, or even an increase in the number of bits in a key, does not necessarily provide much more security. If a briefcase maker wanted to sell you a product with six three-digit locks, would you want to buy it? The company would be correct in claiming that the briefcase had more possible combinations (that is, keys) than DES. However, knowing what you know now, you can calculate that it would take less than an hour to open this secure briefcase.