
# 应用数学在密码学和信息安全中的实践

Version 1.0

All trademarks are trademarks of their respective owners. Rather than put a trademark symbol after every occurrence of a trademarked name, we use names in an editorial fashion only, and to the benefit of the trademark owner, with no intention of infringement of the trademark. Where such designations appear in this book, they have been printed with initial caps.

McGraw-Hill Education eBooks are available at special quantity discounts to use as premiums and sales promotions or for use in corporate training programs. To contact a representative, please visit the Contact Us page at [www.mhprofessional.com](http://www.mhprofessional.com).

Information has been obtained by McGraw-Hill Education from sources believed to be reliable. However, because of the possibility of human or mechanical error by our sources, McGraw-Hill Education, or others, McGraw-Hill Education does not guarantee the accuracy, adequacy, or completeness of any information and is not responsible for any errors or omissions or the results obtained from the use of such information.

*This book is dedicated to the men and women working in military and intelligence agencies who implement cryptography, work with cryptanalysis, and apply cryptography to computer security.*

#### About the Author

**Chuck Easttom** has more than 20 years of experience working in various aspects of the computer industry. For the past 15 years, he has focused primarily on computer security. He has wide experience in security, penetration testing, and forensics, but his favorite security topic is cryptography. Easttom has taught cryptography to U.S. government personnel, Department of Defense–related personnel, and friendly foreign governments. Of his six computer science patents, one is a method of distributed steganography. He has published papers on cryptography, and his various computer security books always include chapters on cryptography. He is a frequent speaker on cryptographic topics including RSA encryption, cryptographic backdoors, and cryptanalysis.

Easttom’s security-related background includes 30 industry certifications, work with various vendors in the creation or revision of their certification tests, years of hands-on direct experience, and extensive teaching experience.

**3.** 下列哪种方法使用了带有文字缠绕的圆柱？

**A.** 维纳尔密码

**B.** 杰斐逊磁盘

**C.** 密码磁盘

**D.** Scytale

**4.** 什么是仿射密码？

**A.** 任何形式的 ax + b (mod m) 的密码

**B.** 仅单字母替换密码

**C.** 任何单字母替换密码

**D.** 多字母密码

**5.** 混合字母替换的关键特征是什么？

**A.** 使用多个替换字母表。

**B.** 同一平文字母可能有多种密文表示。

**C.** 密文在音调上与明文相似。

**D.** 它结合了替换与转位。

### 答案

**1.** A

**2.** C

**3.** D

## 4

A

## 5

B

#### Endnotes

1. Bruce Schneier, “The Strange Story of `DUAL_EC_DRBG`,” [`www.schneier.com/blog/archives/2007/11/the_strange_sto.html`](http://www.schneier.com/blog/archives/2007/11/the_strange_sto.html).

2. Merriam-Webster Dictionary, [`www.merriam-webster.com/dictionary/cryptography`](http://www.merriam-webster.com/dictionary/cryptography).

3. Columbia University “Introduction to Cryptography” course, [`www.cs.columbia.edu/~hgs/teaching/security/slides/crypto2.pdf`](http://www.cs.columbia.edu/~hgs/teaching/security/slides/crypto2.pdf).

4. For more about 更多关于单词和字母频率的信息，请参见“`Puzzle Barron’s Cryptograms`,” [`www.cryptograms.org/letter-frequencies.php`](http://www.cryptograms.org/letter-frequencies.php); “Cornell University Letter Frequency: “Letter Frequencies in English,” [`www.letterfrequency.org/`](http://www.letterfrequency.org/).

5. Suetonius, `Lives of the Caesars` (Oxford University Press, 2009).

6. Ken Harthun discusses the use of `ROT 13` in the Windows Registry in “`How to Use the Windows Registry for Cyber Forensics: Part 2`,” at [`http://itknowledgeexchange.techtarget.com/security-corner/how-to-use-the-windows-registry-for-cyberforensics-part-2/`](http://itknowledgeexchange.techtarget.com/security-corner/how-to-use-the-windows-registry-for-cyberforensics-part-2/).

7. Tap codes were discussed in “`Return with Honor`,” an episode of `American Experience` on PBS television. For information on the POWs’ use of the tap code, see [`www.pbs.org/wgbh/amex/honor/sfeature/sf_tap.html`](http://www.pbs.org/wgbh/amex/honor/sfeature/sf_tap.html).

8. Jim and Sybil Stockdale, `In Love and War: The Story of a Family’s Ordeal and Sacrifice During the Vietnam Years` (Harper & Row, 1984).

9. From Plutarch’s `Parallel Lives`, “The Life of Lysander”: [`http://penelope.uchicago.edu/Thayer/E/Roman/Texts/Plutarch/Lives/Lysander*.html`](http://penelope.uchicago.edu/Thayer/E/Roman/Texts/Plutarch/Lives/Lysander*.html).

## 2

## History of Cryptography from the 1800s

## In this chapter we will cover the following:

![image](img/image00483.jpeg) `Playfair cipher`

![image](img/image00483.jpeg) `Two-square and four-square ciphers`

![image](img/image00483.jpeg) `Hill cipher`

![image](img/image00483.jpeg) `ADFGX and ADFGVX ciphers`

![image](img/image00483.jpeg) `Bifid ciphers`

![image](img/image00483.jpeg) `Gronsfeld cipher`

![image](img/image00483.jpeg) `Vernam cipher`

![image](img/image00483.jpeg) `Enigma`

![image](img/image00483.jpeg) `Historical figures in cryptography`

In Chapter 1, you were introduced to several relatively simple ciphers that were widely used for many centuries. Beginning in the 1800s, the art of cryptography entered an age of growth as more complex ciphers were developed. In this chapter we will look at the end of the classical (pre-computer) days of cryptography and continue on to the 20th century. The ciphers in this chapter are, for the most part, more complex than those of Chapter 1. You may find yourself having to reread the descriptions of some. If you have any difficulty with a cipher, I urge you to take a pencil and paper and experiment with it until you are comfortable.

### Cryptography Marches On

Although these ciphers are more complex than those in Chapter 1, they are still not adequate for the modern computer age, so it would be an egregious mistake to attempt to implement one of these, perhaps via computer code, and then presume your data is secure. Modern computers can utilize brute-force methods, and, in fact, noncomputerized cryptanalysis methods have been developed to attack many of these ciphers. I examine those methods in Chapter 17, when we explore cryptanalysis in general.

**Tip**

Most people have some level of difficulty with cryptography when they first encounter it. In this chapter, as well as the rest of this book, keep in mind that some topics will require some hands-on practice and others will require reading the text more than once. But make sure you fully understand a topic before moving on to the next topic.

### Playfair Cipher

The `Playfair cipher` was invented in 1854 by Charles Wheatstone, but it was popularized by Scottish politician and scientist Lord Playfair, thus it bears his name. This cipher works by encrypting pairs of letters, also called `digraphs`, at a time. Although it was first rejected by the British government as being too complex, it was actually used by the British military in World War I and to some extent in World War II. It was also used by the government of New Zealand as late as the early 1940s for non-military communications.

**Note**

Charles Wheatstone (1802–1875) was an accomplished inventor and scientist. Among his various contributions to science was the `Wheatstone bridge`, an electrical circuit that is used to measure electrical resistance. The original bridge was invented by Samuel Hunter Christie, but Wheatstone improved it. Wheatstone also made a number of contributions to our knowledge and application of electricity.
