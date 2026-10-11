
# Ethereum Art Market

## Smart Contract Code

```
{   (def ‘next-record 0x10)(def ‘RECORD-SIZE 64)   
;; Next record position   
;; This starts one cell above the maximum value of RipeMD   
[[next-record]] 0x10000000000000000000000000000000000000000   
(return   
   0x0   
   (lll {   
      ;; Action   
      ;; 0 - first cell in message   
      [action] (calldataload 0)   
       (when (= @action “register”)   
         {   
         ;;TODO: Check correct message length   
         ;;TODO: Check digest in range   
          ;; Artwork digest   
         [digest] (calldataload 32)   
         ;; If already registered, don’t continue   
          (when @@ @digest   
            (return “Artwork already registered.”))   
         ;; Get storage for new record   
         [storage] @@next-record   
         ;; Store digest   
         [[@storage]] @digest   
         ;; Artist account   
         [storage] (+ @storage 1)   
         [[@storage]] (caller)   
         ;; Artist resale percentage   
         [storage] (+ @storage 1)   
         [[@storage]] (calldataload 64)   
         ;; Artist is the current owner   
         [storage] (+ @storage 1)   
         [[@storage]] (caller)   
         ;; Skip purchaser and price   
         [storage] (+ @storage 3)   
         ;; Copy over the url and description   
         ;; 96 is 32 x 3 = 3rd cell in message   
         [source] 96   
            (for [i] 6 (< @i 64) [i] (+ @i 1)   
               {   
               [[@storage]] (calldataload @source)   
               [storage] (+ @storage 1)   
               [source] (+ @source 32)   
               })   
         ;; Store digest-to-record link   
         [[@digest]] @@next-record   
         ;; Increment next record position   
         [[next-record]] (+ @@next-record RECORD-SIZE)   
         })   
      (when (= @action “offer”)   
         {   
         ;; TODO: Check correct message length   
         ;; TODO: Check digest in range   
         ;; Get artwork record storage for digest or stop   
         ;; 32 = second cell in message   
         [storage] @@(calldataload 32)   
         (when (not @storage)   
            (return “Artwork not registered.”))   
         ;; If the caller is the owner   
         (when (= @@ (+ @storage 3) (caller))   
            {   
            ;; Offer subject   
            [[(+ @storage 4)]] (calldataload 64)   
            ;; Offer price   
            [[(+ @storage 5)]] (calldataload 96)   
            })   
            })   
      (when (= @action “accept”)   
         {   
         ;;TODO: Check digest in range   
         ;;TODO: Error messages for bad price or buyer   
         ;; Get artwork record storage for digest or stop   
         ;; 32 = second cell in message   
         [storage] @@(calldataload 32)   
         (when (not @storage)   
            (return “Artwork not registered.”))   
         [buyer] @@(+ @storage 4)   
         [price] @@(+ @storage 5)   
         ;; If the caller is the buyer and it’s the correct payment   
         ;; Or there’s no buyer and it’s the correct nonzero payment   
         (= @price (callvalue)))   
         (&&   
        (= @buyer 0)   
            (> @price 0)))   
            {   
            ;; For payment 
            ;; Ethereum doesn’t allow fractional amounts   
            ;; Warn users about making prices divisible   
            [hundredth] (/ @price 100)   
            [arr] @@(+ @storage 2)   
            ;; Pay artist   
            (call (- (gas) 250) @@(+ @storage 1) (* @hundredth @arr) 0 0 0 0)   
            ;; Pay owner   
            (call (- (gas) 250) @@(+ @storage 3) (* @hundredth (- 100 @arr)) 0 0 0 0)   
            ;; Transfer ownership   
            [[(+ @storage 3)]] (caller)   
            ;; Clear offer subject and price   
            [[(+ @storage 4)]] 0   
            [[(+ @storage 5)]] 0   
            })   
         })   
         })   
      } 0x0))}
```

## UI Screenshots

Here’s the top and the bottom of the main UI (implemented in HTML and JavaScript for the AlethZero Ethereum client).

![UI Top and Bottom](image/140724_myers-Ethereum_art_market-01.jpg) ![UI Top and Bottom](image/140724_myers-Ethereum_art_market-03.jpg)

You can enter a URL and get the cryptographic hash for it. If the artwork has already been registered, this will show its details.

![Artwork Details](image/140724_myers-Ethereum_art_market-02.jpg) ![Registry](image/registry5.jpg)

Or if not, you can register it.

![Register Artwork](image/140724_myers-Ethereum_art_market-05.jpg)

Once you’ve registered an artwork, you are the artist of it and you also own it. You can offer any artwork you own for sale.

![Offer for Sale](image/140724_myers-Ethereum_art_market-06.jpg)

And you can accept a sale offer, paying the specified amount of Ether.

![Accept Sale](image/140724_myers-Ethereum_art_market-07.jpg)

The UI warns you how much Ether you are about to spend.

![Spend Warning](image/140724_myers-Ethereum_art_market-08.jpg)

And when you buy an artwork it lets you know when the transfer is complete.

![Transfer Complete](image/140724_myers-Ethereum_art_market-09.jpg)

It’s a market in allographic digital art. In contrast to the existing art market, it is entirely public and transparent. And in contrast to many jurisdictions, it implements the controversial ‘Artist’s Resale Right’ in a voluntary way (in a way similar to that suggested in *The Social Life of Artistic Property*).[4](#7-Ethereum-art-market.xhtml#footnote-143) If it’s prohibitively difficult to experiment in the existing art market, we can make new markets for new kinds of art. Like this one.

## Notes

[1](#7-Ethereum-art-market.xhtml#footnote-146-backlink) See ‘[Artworld Ethereum](#6-Artworld-ethereum.xhtml)’.

[2](#7-Ethereum-art-market.xhtml#footnote-145-backlink) A. Dash, ‘A Bitcoin for Digital Art’, medium.com, [<https://medium.com/message/a-bitcoin-for-digital-art-8c7db719e495>](https://medium.com/message/a-bitcoin-for-digital-art-8c7db719e495).

[3](#7-Ethereum-art-market.xhtml#footnote-144-backlink) [<https://eth.wiki/>](https://eth.wiki/).

[4](#7-Ethereum-art-market.xhtml#footnote-143-backlink) A. Whitaker, *The Social Life of Artistic Property*, [<https://www.thing.net/~rdom/ucsd/3somesPlus/sociallifeofartisticproperty.pdf>](https://www.thing.net/~rdom/ucsd/3somesPlus/sociallifeofartisticproperty.pdf).

# Crypto Sigils

## 2014

![Sigil](image/sigil.png)

A cryptographic hash function is a piece of computer code that takes a piece of data and produces a (hopefully) unique short string representing it. This string will in no way resemble the input data, and you will not be able to guess the input data from it. The function always outputs the same string for the same data, and changing the data will change the output string.

For example, I can use the `sha256` function on the UNIX command line to make a unique representation of my name:

```
# echo rhea | sha256sum
2466a0da1499e193618f43b392a408b2101710fef023f8b01ec351ab393d9ea4 –
```

And if I do this again I get the same result:

```
# echo rhea | sha256sum
2466a0da1499e193618f43b392a408b2101710fef023f8b01ec351ab393d9ea4 –
```

But if I add just one extra character I get a different result:

```
# echo rheaM | sha256sum
aa0aaa2835c977137200480dae2672603eb368b80adaae4aef79a385c451ff95 –
```

And importantly the amount of difference in the input has no effect on the amount of difference between the output strings:

```
# echo rheaN | sha256sum
81744d575e87892fa40992b20a001036a871f7401839beed78aab114c2e00818 –
```

So, the outputs of cryptographic hash functions produce identities for data that can be used to uniquely refer to the data but do not disclose the content of the data.

Hash functions achieve this by feeding the data through a complex mathematical transformation. This is a mapping through mathematical space that maintains identity and difference while occulting content.

Much like a sigil.

It’s true that if one knows the word or words abstracted to make a sigil, one can recognise their traces in the sigil. But these traces are a means to an end, they are a way of producing a striking and unique new identity to focus on and invest in.
