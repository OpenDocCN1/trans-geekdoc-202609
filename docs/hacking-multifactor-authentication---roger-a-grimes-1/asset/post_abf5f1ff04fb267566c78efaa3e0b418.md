
# Chapter 16 Attacks Against Biometrics 347

(aholandminkley/biometric/MVI_4421.avi), but wouldn't work on the scanner. I like this example because it is similar to what I have experienced in my biometric testing. Not all techniques work on scanners, but all scanners can be faked out one way or another. And sometimes it takes $12.82 worth of glue, gummy bears, wax, and Play-Doh.

## Defeating Apple Touch with Gelatin Fingers

In this example (www.iphoneincancada.com/news/touch-id-bypassed-fingerprint-gelatin-finger), white-hat hackers successfully hacked Apple's fingerprint scanner using a fingerprint imprinted on plastic by smeared glue to fix it. A second hacker did it using common food gelatin. A video of the former method is shown here: www.youtube.com/watch?v=hMB0dB8SkNG. A second video successfully hacking Apple's fingerprint using another method: www.youtube.com/watch?v=2u4ZGsw1zo.

### Tencent Fingerprint Hack

At Tencent, a large Chinese security company, researchers used fingerprints printed on glass (www.tomguide.com/news/hackers-unlock-using-phone-photographed-fingerprints-in-just-20-minutes) to fool superbly every fingerprint reader they tried, using materials that cost $140. They demonstrated their technique at a Chinese security conference. They asked a member of the audience to bring up him, they took a picture of his fingerprint, and in under 20 minutes they had hacked his off.

> NOTE Sometimes it takes to defeat fingerprint sensors is the wrong type of sensor protector: www.theverge/2019/10/23/2092178/samsung-galaxy-s10-note-to-fingerprint-recognition-issue-patch-ultrasonic-sensor.

They tried to fool lots of different devices and systems, with mixed success. They were able to fool fingerprints fairly well but not a Samsung A70 (which had a high rejection rate with real fingerprints as well). They had no success against Microsoft's Windows Hello on multiple devices either, but they did against a MacBook Pro. They successfully broke into a biometric-protected pad-lock were not successful against two-tested biometrically protected USB encrypted drives.

## Hacking Multifactor Authentication

**NOTE** Make authentication too hard and criminals may just cut off your finger: news.bbc.co.uk/2/hi/asia-pacific/4396831.stm. But guy wishes he never bought a car with fingerprint biometric protection.

## Hand Vein Attack

In December 2018, some members of the infamous European-based Chaos Computer Club (CCC) faked out vein recognition (motherboard.vice.com/en_us/article/59v8dk/hackers-fake-hand-vein-authentication-biometrics-chaos-communication-congress). It wasn't easy. It took over 30 days of effort, but they were routinely fooling the scanners using vein-shaped lines printed on a hand-shaped flat surface covered in wax.

**NOTE** CCC also made news in 2014 when they claimed they had successfully cloned a German politician's fingerprint from a conference using a regular camera: www.bbc.com/news/technology-3026311.

## Eye Biometric Spoof Attacks

Eyes can be spoofed by biometric readers like any other biometric trait. In particular, iris spoofing is a common area of research for scientists and researchers around the world. Iris spoofing attacks (known as presentation attacks in the biometric world) usually involve reprinted images of eyes, replayed video of eyes, or textured lenses. The latter method has the best spoofing ability.

Unfortunately, there aren't a lot of YouTube videos showing attacks against eyeballs, iris, or retinas, because these attacks are more expensive and difficult to pull off than the average security geek. Does not mean eye biometric spoofing can't be done. In fact, it's proven that it can be. It's a huge worry for the vendors that we rely on. So, the research and demos of eye-biometric spoofing attacks tend to be done behind closed doors by university PhDs. Researchers around the world are trying their best to both hack and defend against eye biometric solutions.

There are even international competitions to both defeat and defend against iris spoofing attacks. The LiveDet-Liveness Detection Competition Series (livedet.org) is held every two years around the world. In 2017, the “winner” of LiveDet was able to successfully detect 15 percent of spoiled irises, using specially created contact lenses, the involved iris recognition scanners. This is against the best anti-spoofing, state-of-the-art technology in world.

One researcher who is part of competition, Daksha Yadav, has written extensively on the accuracy to detect and spoof eye biometric systems. Here is a presentation from a group of researchers that includes Yadav: www.youtube.com/watch?v=HShg-IX1xpg. You can read more of his individual papers on the subject here: (www.researchgate.net/scientific-contributions/2059653303-Daksha_(Yadav)) or download one of his relevant papers: (www.researchgate.net/publication/326915028_Fusion_of_Handcrafted_and_Deep_Learning_Features_for_Large-Scale_Multiple_Iris_Presentation_Attack_Detection/download. If you spend one of his

# Chapter 16 Attacks Against Biometrics 349

## Facial Recognition Attacks

Next we will look at some example facial attacks.

## Spoofing Windows Hello

As stated, Windows Hello is one of the more difficult (i.e., not just a picture of a face held up on a piece of paper) to fool. For a biometric camera that supports anti-spoofing, a facial recognition camera that enhances anti-spoofing, at the end of 2017, some German (www.youtube.com/watch?v=OaqBwlxSkGs&feature=youtube).

So, what is "enhanced anti-spoofing" and why doesn't Microsoft enable it by default? I could not find exact requirements for a biometric device to be branded as supporting anti-spoofing, but the best I can tell is that cameras supporting anti-spoofing likely do by this combination of one or more of the following between aed face (2D—pictures and videos) and real faces:

- Checks ensure submitted image is 3D and real checking for depth, height, and texture differences. Paper and masks are likely to be far uniform across all checks.
- Checks if eyes are moving
- Checks if it is moving
- Checks if the area around the face is distinctly (i.e., not just a picture of a face)

## 350 Hacking Multifactor Authentication

For more information on facial-anti-spoofing checks, see ynd-consult.com/blog/anti-spoofing-mechanisms-in-face-recognition-based-on-dnn and towardsdatascience.com/anti-spoofing-techniques-for-face-recognition-solutions-4257c5b1dfc9. Window Hello with enhanced-spoofing can be enabled if you have a version of Windows 10 or newer that supports the feature as a facial recognition camera that enhances anti-spoofing, and you have enabled the enhanced-spoofing feature (it is not enabled by default). To enable it in Windows 10 (assuming you have supporting software and hardware), open the local Group Policy Editor (gpedit.msc) and navigate to:

```
Computer Configuration\Administrative Templates\Windows Components\Biometrics\Fac Features
```

Then enable the Configure Anti-Spoofing setting. Figure 16.7 shows the Enhanced Anti-Spoofing Group Policy key.

![](img/c78b0f79db62998ee317a35df5629d85_368_0.png)

**Figure 16.7:** Microsoft's Enhanced Anti-Spoofing Group Policy key.
