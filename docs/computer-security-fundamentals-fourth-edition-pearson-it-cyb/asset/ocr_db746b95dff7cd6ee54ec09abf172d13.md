+   - The ancient Chinese wrapped notes in wax and swallowed them for transport. This was a crude but effective method of hiding messages.
+   - In ancient Greece, a messenger’s head would be shaved, a message was written on his head, and then his hair was allowed to grow back. Obviously, this method required some time.
+   - In 1518 Johannes Trithemius wrote a book on cryptography and described a technique in which a message was hidden by having each letter taken as a word from a specific column.
+   - During World War II the French Resistance sent messages written on the backs of couriers using invisible ink.
+   - Microdots are images/undeveloped film the size of a typewriter period that are embedded in innocuous documents. These were said to be used by spies during the Cold War.
+   - Also during the Cold War, the U.S. Central Intelligence Agency used various devices to hide messages. For example, they developed a tobacco pipe that had a small space to hide microfilm but could still be smoked.

In more recent times, but before the advent of computers, other methods were used to hide messages.

# Steganography Methods and Tools

There are a number of tools available for implementing steganography. Many are free or at least have free trial versions. A few of these tools are listed here:

+   - **QuickStego:** Easy to use but very limited
+   - **Invisible Secrets:** Much more robust, with both a free version and a commercial version available
+   - **MP3Stego:** Specifically for hiding payload in MP3 files
+   - **Stealth Files 4:** Works with sound files, video files, and image files
+   - **Snow:** Hides data in whitespace
+   - **StegVideo:** Hides data in a video sequence
+   - **Invisible Secrets:** A very versatile steganography tool that has several options

# Cryptanalysis

Cryptanalysis is a daunting task. It essentially involves searching for some means to break through encryption of some sort. And, unlike what you see in the movies, it is a very time-consuming task that frequently leads to only partial success. Cryptanalysis involves using any method to decrypt the message that is more efficient than simple brute-force attempts. (Remember that brute forcing means simply trying every possible key.)

A cryptanalysis success is not necessarily breaking the target cipher. In fact, finding any information about the target cipher or key is considered a success. There are several types of cryptographic success:

+   - **Total break:** The attacker deduces the secret key.
+   - **Global deduction:** The attacker discovers a functionally equivalent algorithm for encryption and decryption but without learning the key.
+   - **Instance (local) deduction:** The attacker discovers additional plain texts (or cipher texts) not previously known.
+   - **Information deduction:** The attacker gains some Shannon information about plain texts (or cipher texts) not previously known.
+   - **Distinguishing algorithm:** The attacker can distinguish the cipher from a random permutation.