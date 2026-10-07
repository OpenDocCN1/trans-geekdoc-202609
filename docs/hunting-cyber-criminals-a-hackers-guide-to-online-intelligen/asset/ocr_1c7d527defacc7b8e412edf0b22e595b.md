# Chapter 10 - Certificate Transparency and Internet Archives 207

```
DNS.*.ardysv.gq
DNS.*.ayrescreta.com.br
DNS.*.bleudecode.com
DNS.*.bolnichnye-listi.com
DNS.*.booksport1.cf
DNS.*.cabinetpaintingfinishing.com
DNS.*.colombia-sexo.tk
DNS.*.donji-vafuk.tk
DNS.*ebookfrees91.cf
DNS.*.galileguros.com.br
DNS.*.ditsmalek.tk
DNS.*.guessmantra.ga
DNS.*.homespaces.com
DNS.*.instaptics.bid
DNS.*.instaptics.party
DNS.*.jand.tk
DNS.*.meettabernacle.com
DNS.*.memoriasguros.com.br
DNS.*.mindbendingbeats.ca
DNS.*.naysatgheuros.com.br
DNS.*.og.money
DNS.*.originsgranite.com
DNS.*.palwalonline.in
DNS.*.peterkomorowski.com
DNS.*.phpturtle.com
DNS.*.reenu.com
DNS.*.satanism.ca
DNS.*.seguros6.com.br
DNS.*.spravka-moscowl77.ru
DNS.*.taskbook-s.cf
DNS.*.toolzdepot.com
DNS.*.whitepacket.com
```

We have a literal swarm of domains that are sharing the SSL certificate as WhitePacket.com. In a best-case scenario, this will reveal domains that are all of the same Cloudflare account. This does not necessarily imply they are of the same owner, just that they are all sharing the same Cloudflare account.

# NOTE FROM Cloudflare

I reached out to someone on Cloudflare's investigative team regarding the use of certificates to find related domain owners. This was their response: "In the vast majority of cases completely unrelated domains end grouped together on shared TLS SNI certificates."
Noted! As anything OSINT related, this is just one more technique you can use to gain more clues as you spiral down the rabbit hole of information. In our test case, the information turned out to be valid. However, it's important to note that Cloudflare has pointed out that this may not always be the case. Tread carefully.