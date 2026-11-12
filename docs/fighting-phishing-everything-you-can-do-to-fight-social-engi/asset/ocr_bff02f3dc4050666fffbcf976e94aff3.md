social engineering attacks manipulate URLs in an attempt to trick users. By understanding and recognizing these tricks, you can be one of the defenders who is never fooled.

# Look-Alike Domains

One of the most common phishing URL tricks is the phisher creating domains that aren't real but look like they are and contain a legitimate brand's name or URL. The next figures give multiple examples of fraudulent, look-alike domains. The example in Figure 13-10 shows a common trick.

![](bbox=[0.247, 0.396, 0.703, 0.423])

FIGURE 13-10 A real-world example of a phishing URL pretending to be from Bank of America.

The URL in Figure 13-10 was created to look like it's the legit URL of Bank of America (i.e., bankofamerica.com), but bankofamerica is just a child domain under the DNS domain doc.com. Bank of America does not own or manage doc.com. Phishers were able to create a subdomain that looked like bankofamerica.com, which was not bankofamerica.com.

![](bbox=[0.283, 0.671, 0.679, 0.695])

FIGURE 13-11 A real-world phishing URL pretending to be from PayPal.

In Figure 13-11, the phisher is hoping potential victims will see the paypal.com portion of the URL and think it is paypal.com, the legitimate URL for PayPal. But paypal.com is simply a (rogue) child domain under the .bank TLD. The domain registrar handling the .bank TLD was tricked into issuing the domain paypal.com under its .bank TLD for a few days until