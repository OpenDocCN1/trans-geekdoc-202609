
# Using the Art Market as a Network for Exploits

Using the art market itself as the network to exploit, rather than the internet, makes for even more powerful art malware exploits. Aesthetic analytics of the kind practiced by Lev Manovich[3](#14-Vampire-digital-art.xhtml#footnote-121) and already used to guide investment by Mutual Art[4](#14-Vampire-digital-art.xhtml#footnote-120) can be combined with the techniques of stock market high-frequency trading (HFT) to create new forms by intervening in and manipulating prices directly through art sales and auctions. As with HFT, the activity of the software used to do this can create aesthetic forms within market activity itself, like those found by Nanex.[5](#14-Vampire-digital-art.xhtml#footnote-119) This can be used to build and destroy artistic reputations, to create aesthetic trends within the market, and to create art movements and canons. Saatchi automated. The aesthetics of this activity can then be sold back into the market as art in itself, creating further patterns.

The techniques suggested here are at the very least illegal and immoral, so it goes without saying that you shouldn’t attempt to implement any of them. But they are useful as unrealised artworks for guiding thought experiments. They are useful for reflecting on the challenges that art in and outside the art world faces in the age of the attention-starved population of the pervasive internet and of media and markets increasingly determined by algorithms. And they are a means of at least thinking through an ethic rather than just an aesthetic of market critique in digital art.

### Notes

[1](#14-Vampire-digital-art.xhtml#footnote-123-backlink) C. Stross, ‘Polemic: How Readers Will Discover Books in Future’, 10 October 2013, [<https://www.antipope.org/charlie/blog-static/2013/10/polemic-how-readers-will-disco.html>](https://www.antipope.org/charlie/blog-static/2013/10/polemic-how-readers-will-disco.html).

[2](#14-Vampire-digital-art.xhtml#footnote-122-backlink) [<https://rhea.art/postscript-viruses>](https://rhea.art/postscript-viruses). See [Interview](#1-interview.xhtml) above.

[3](#14-Vampire-digital-art.xhtml#footnote-121-backlink) [<http://lab.softwarestudies.com/p/cultural-analytics.html>](http://lab.softwarestudies.com/p/cultural-analytics.html).

[4](#14-Vampire-digital-art.xhtml#footnote-120-backlink) M. Maneker, ‘Big Data and the Art World: Mutual Art’, Art Market Monitor, 13 October 2013, [<https://www.artmarketmonitor.com/2013/10/13/big-data-and-the-art-world-mutual-art/>](https://www.artmarketmonitor.com/2013/10/13/big-data-and-the-art-world-mutual-art/).

[5](#14-Vampire-digital-art.xhtml#footnote-119-backlink) A.C. Madrigal, ‘Market Data Firm Spots the Tracks of Bizarre Robot Traders’, The Atlantic, 4 August 2010, [<https://www.theatlantic.com/technology/archive/2010/08/market-data-firm-spots-the-tracks-of-bizarre-robot-traders/60829/>](https://www.theatlantic.com/technology/archive/2010/08/market-data-firm-spots-the-tracks-of-bizarre-robot-traders/60829/).

# Agoric Aesthetics and Philosophy

## 2014

Agorising aesthetics and philosophy means producing them using market pricing mechanisms. The model for this is the market-based software of agoric computing. The advantage of such a system is that it incentivises both production and efficiency. By internalising market forces, the perverse incentives of gamified systems such as academic research points can be avoided.

An agoric system needs a currency; for efficiency’s sake we will use a cryptocurrency. There are several ways of implementing a currency for an agoric system using cryptocurrency systems. We can use coloured coins, nxt or Counterparty assets, or Ethereum contracts similar to the Token System example in the Ethereum White Paper to create coins, tokens, or other quantifiable valences. For simplicity’s sake I will call all of these ‘tokens’. Different implementations allow different capabilities: fungibility, revocation, transferability.

An artist group or artistic movement can use a store of tokens allocated by vote or other mechanism to artists or artworks that they deem part of the movement and its output. The Cypherfunks project is an existing example of such a system. Such a system combines the nominative practices of Dadaist, Conceptual, and some Pop/Post-Pop art with the social and aesthetic function of materially identifying in- and out-groups. A single-artist token could be used to create an oeuvre in the style of Duchamp or Kostabi.

Art critics can use tokens to embody critique. A single-value token can be used to embody critical approval, a pair of oppositely valenced tokens to represent approval/opprobrium (and to revise critical opinion should it later change), a family of tokens with different star rankings can be used to implement a star system at the cost of fungibility. The critic sends tokens either to the artist’s address in the cryptocurrency system or to an address representing the hash or proxy hash of the artwork. The artist or artwork’s standing can be discovered by counting the number and kind of critical tokens associated with it.

Philosophical treatises can be constructed agorically. Axioms and citations, logical and rhetorical moves can be assigned point costs either as classes (premise, objection, rebuttal) or individually (Derrida, Arendt, Meillassoux). Each usage increases the price of the essay. Point costs and budgets can be assigned per hundred words or for a given form (short essay, review, thesis, journal article etc.) or context (particular journals, web sites, or educational institutions). Essays are then written to the budget. Or price essays according to the system and then let publishers (and readers) choose which to consume on that basis. For a more dynamic system, prices can be set using a PageRank-style system as a product of the cost of cited works.

The pricing of this essay is left as an exercise for the reader….

# Ethereum Standardised Art Contract API

## 2015

The Ethereum project allows you to create arbitrary smart contracts to run on its blockchain. To ensure that those arbitrary contracts can communicate where they need to, they have published a list of standard contract interfaces.[1](#16-Ethereum-Standardised.xhtml#footnote-118)

These standards allow different coins, registries, data feeds, and other common contracts to communicate with and use each other in a well understood way.

Let’s extend this to art contracts, starting with a smart artwork. Next we’ll cover exhibitions and reviews.

These interfaces are applicable to contracts other than for art. Feedback and suggestions on how to generalise them gratefully received.

## Purchasable Artwork

A smart contract artwork either embodies an artwork in itself, represents or controls some aspect of an artwork, or contains or is a proxy for it in some way.

The contract’s owner is expected to be the artist, and not to change. ‘Ownership’ of the artwork is recorded within the contract.

## Methods

### offer

```
offer(address _purchaser, uint _price, uint _until)
```

Only callable by the artwork owner. This is separate from the contract owner.

Offer the work for sale. The `_purchaser` address can be zero, in which case anyone can buy the artwork. The `_price` can be zero, in which case the `_purchaser` need not send any funds. And `_until` can be a UNIX timestamp in the past, in which case the artwork is not actually for sale. Zero works well for this.

### purchase

```
purchase() returns (bool _success)
```

If the caller matches the `_purchaser` (or it is set to zero), sends enough Ether to match `_price` (or `_price` is zero), and the offer has not expired, the caller becomes the new owner of the artwork.

### purchaseFee

```
purchaseFee() return (uint8 _percentage)
```

The percentage of the purchase price that goes to the contract owner (the artist) rather than the purchaser. A functional equivalent to the ‘Artist Resale Right’.

### setPurchaseFee

```
setPurchaseFee(uint8 _percentage)
```
