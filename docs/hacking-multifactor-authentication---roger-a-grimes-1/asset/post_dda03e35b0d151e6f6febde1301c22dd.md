
# Hacking Multifactor Authentication

## Hand Geometry

Hand geometry readers measure the outlining shapes and lengths of a candidate's hand, including:

- Hand length and width
- Individual finger length and width
- Individual joint length and width
- Angles and geometric shapes between different fingers, joints, and features

Hand geometry researchers have identified 30 distinct measurements that can be taken and compared to identify a specific hand, and each hand is believed to be unique. Hand geometry is not considered as provable globally unique as compared to fingerprints and other biometric attributes, but I haven't read of a documented exact yet.

Hand readers usually have small posts that separate the fingers and help place the hand in the right position and orientation. See Figure 16.2 for an example of a popular hand geometry scanner.

![](img/c78b0f79db62998ee317a35df5629d85_348_0.png)

**Figure 16.2:** Popular hand geometry reader example
Source: Z22, used under the Attribution-Share Alike 3.0 Unported license, creativecommons.org/licenses/by-sa/3.0/deed

# Chapter 16 Attacks Against Biometrics

I used a hand geometry reader as part of my employer's computerized time clock system over two decades ago. My current health-care system uses hand geometry scanners to recognize and identify ER patients. Hand geometry scanners are often used in conjunction with fingerprint readers (using more than one biometric attribute for authentication at the same time is known as multimodal) to improve their overall accuracy, and this seems to be the combination I've been involved with. With my current employer, KnowB4 uses this combination for building entry. We had false-positives before using multimodal scanners.

For more information on hand geometry scanning, see cdn.intechopen.com/pdfs/40073/Intech-Basic_principles_and_trends_in_hand_geometry_and_shape_biometrics.pdf. Palm scanning, using the same technology as finger vessel scanning, is a semi-common biometric solution as well. Palm vein readers have been used in corporate and high-security offices. We have even seen of banking ATM systems using palm veins of their customers as a way to authenticate cash card users and even portable user tokens based on palm vein reading. By many of these early, more projects eventually went away because of complexity, cost, and disease transmission concerns.

> NOTE Microsoft Windows Hello allows palm vein scanning as well: newatlas.com/windows-10-palm-vein-scan/53344.

## Iris

The iris is the colored part of the eye (see example in Figure 16.3), which is attached to sphincter muscles that control the size of the pupil to regulate how much light enters the internal structures of the eye. The iris's scannable image is composed of the pigment, muscles, fibrous tissue, texture, and blood vessels. This combination is considered highly unique within humans.

![](img/c78b0f79db62998ee317a35df5629d85_349_0.png)

**Figure 16.3:** Example of an eye iris
Source: FreeImages.com/Sofi gamache

# 332 Hacking Multifactor Authentication

Biometric eye readers will read one or both eyes. Iris scanners work using visible light or near-infrared light, with the near-infrared light revealing more detail, especially in (very) brown-eyed people who typically have less visible distinctions. Iris recognition works even if the candidate is wearing glasses or contacts. Irises usually change very slowly, over decades. There can be iris changes, and a good overview of why they may be due to be found here: https://www.aaa.org/eye-health/tips-vision/why-are-my-eyes-changing-color. But in the general population, iris changes are usually rare and occur slowly over many years. Most people do not change over their lifetime after the first year of age.

Iris recognition has been used for decades, initially moving increasingly in different nations as part of border control measures. A good list of iris recognition projects can be found here: https://en.wikipedia.org/wiki/Iris_recognition. One major disadvantage to shared iris readers, more like tactile fingerprints, is potential deamination. No one wants to get "pink eye" from a coworker.

Potential iris recognition forgeries are prevented using a variety of methods, including confirming the submitted image is not flat.

**NOTE** An interesting story involves the iris recognition de-identification: de-identification.

## Retina

The retina is the inner structure of the eye. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals.

# Chapter 16 Attacks Against Biometrics 333

server room. It was very impressive. However, in my experience, I haven't seen a. Other parts of the eyes are also used in biometrics, such as veins of the sclera. You can read more about this type of eye scan: en.wikipedia.org/.

The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals. The retina is the inner structure of the eye that converts light into signals.

## Face

It is often said that, today, in any industrialized country, a person’s image is recorded without them aware at several times, if not dozen times, by video cameras. Using facial recognition and authentication is becoming very popular, perhaps surpassed by fingerprint by sheer number of users.

There are serious, global, concerns about appropriate use of facial recognition. So many enforcement agencies are are using biometrics for identifying people in crowds that what the world is asking for national or global controls to determine what should or shouldn’t be allowed by default.

Facial recognition is built into modern-day smartphones and operating systems. Apple introduced Face ID (en.wikipedia.org/wiki/Face_ID) facial biometrics in their iPhone X and iPad Pro to allow users to unlock their devices, and many other providers followed it.

Microsoft followed by introducing fingerprint and facial recognition authentication for Microsoft Windows with Windows Hello (www.microsoft.com/en-us/windows/windows-hello), and later added palm vein recognition support. Users with the appropriate hardware requirements and Windows 10 can enable it. It has fairly strict requirements for accuracy and security (anti-spoofing) and is one of the systems to hack the more popular technologies as far as operating systems and biometrics. Here’s a real-world picture of Microsoft Windows Hello (see Figure 16.4) using facial recognition to get into my laptop.

If Microsoft Windows Hello facial recognition doesn’t recognize your face, it allows you to log in another previously registered method, like a PIN. This could be another potential example that could be listed in Chapter 13, “Downgrade/Recovery Attacks.”

Face recognition, analysis, storage, and comparison. The acquisition of the face and its characteristics can be done using regular light, infrared light, skin texture analysis, or thermal imaging. Face ID apparently uses over 30,000 separate points of infrared light to map a face.
