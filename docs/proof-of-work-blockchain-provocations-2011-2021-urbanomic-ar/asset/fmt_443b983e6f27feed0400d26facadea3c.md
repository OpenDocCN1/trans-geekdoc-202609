
Is Art is an Ethereum smart contract containing the assertion that it either ‘is’ or ‘is not’ art. Anyone can send this smart contract an Ethereum transaction instructing it to nominate itself as art (or not). A web page connected to the Ethereum network displays the state of this assertion to anyone who can access the contract and provides them with a convenient interface to toggle it between states. When they do so this will become a fact secured in Ethereum’s blockchain with the strength of millions of dollars of computing power a day.

This takes the Conceptual Art ideas of dematerialisation (art that is not presented in a fixed physical form) and nomination (something that is art because someone or something says it is) and combines them with the net.art idea of the interactive artwork that exists within or interferes with network protocols. Whoever toggles the contract’s state as art sets it unimpeded until the next person sends a transaction to change it. A more rational system (and one that does not reduce to mere capital) should be used—bidding, voting, or a prediction market.

The Duchampian strategy of aesthetic transubstantiation through artistic nomination is long played out. It is an art-historical found object, as basic as a smart contract with a single boolean bit of state. This combination of nomination and information invokes Conceptual Art and net.art.

Late 1960s Conceptual Art and mid-1990s net.art are useful inspiration for thinking about the blockchain and smart contracts. These art movements stood in critical tension with the systems of communication, law, and commerce of their eras. Each treated rootless information, whether about sense data or network messages, as the critical subject of art and a new potential art world. Their promise and their eventual recuperation by the existing art world chimes with the historical experience of the blockchain. Brought together, the art-historical and the contemporary technological (or their audiences) can mutually animate and interrogate each other.

Is all of this sufficient to determine whether the contract is or is not art? Where and how is the claim really being made and determined? How does this relate to historical examples of such artworks? And how does it relate to other claims of fact stored in other smart contracts?

# Art Is

## 2014, 2017 Ethereum DApp

![](image/art-is-2.0.png)

A contract that allows anyone to define what art is. It contains a single set of twelve statements about art. They are encoded as hexadecimal values which are interpreted as sentences in a simple subset of International Art English and displayed by the UI.

```
{  ;; Constant values  ;; Price base (wei), doubled for each definition up to DEFS-COUNT
  (def ‘PRICE-BASE 10)
  ;; Add to the index to get the price base exponent
  (def ‘PRICE-FACTOR-ADD 10)
  ;; Number of definitions
  (def ‘DEFS-COUNT 12)
  ;; Range of values for definitions
  (def ‘DEF-MIN 0x1)
  (def ‘DEF-MAX 0x0F0F0F0F)
  ;; Storage locations
  (def ‘artist 0x10)
  (def ‘defs-base 0x100)
  (def ‘theorists-base 0x200)
  ;; State
  ;; Contract owner/payee
  [[artist]] (caller)
  (return
    0x0
    (lll
      {
      [action] (calldataload 0)
        (when (= @action “set”)
          {
          [index] (calldataload 32)
          [definition] (calldataload 64)
          [price] (exp PRICE-BASE (+ @index 1 PRICE-FACTOR-ADD))
          ;; If the index is in range and the caller paid enough to set it
          (when (&& (>= @definition DEF-MIN)
                    (<= @definition DEF-MAX)
                    (< @index DEFS-COUNT)
                    (= (callvalue) @price))
            {
            ;; Update definition
            [[(+ defs-base @index)]] @definition
            [[(+ theorists-base @index)]] (caller)
            (- (gas) 100) @@artist @price 0 0 0 0
            })
          })
      }
      0x0)) }
```

# MYSOUL

## 2014 Counterparty and Dogeparty assets

![](image/mysoul-counterparty.png)![](image/mysoul-dogeparty.png)

I have placed my soul on the blockchain, representing it as a cryptographic asset token.

The `MYSOUL` token is on the Dogecoin blockchain as a Dogeparty asset.

I’ve divided it up into 100 units. This is more efficient than having a single token to represent the soul and transferring it to a single owner, as competition within the market will both reduce costs and allocate this resource more efficiently than a monopoly could.

To make ownership of my soul more accessible, I’ve also created a `MYSOUL` asset on the Bitcoin blockchain with Counterparty.

This is also divided up into 100 units. Counterparty is more expensive for transactions than Dogeparty, but is more widespread, so it’s good to have both options.

Note that my wife will not allow me to sell any of the tokens, as she asserts quite reasonably that my soul belongs to her if anyone.

# Dogecode

## 2014 Python code and Dogeparty tokens

![dogecode](image/dogecode.jpg)

Cryptographic asset tokens can represent all kinds of things.

Including computer programs.

Dogecode takes computer programs in the Brainfuck programming language (chosen for simplicity of encoding):

```
++++++++[>++++[>++>+++>+++>+<<<<-]>+>+>->>+[<]<-]>>.>---.+++++++..+++.>>.<-.<.+++.------.--------.>>+.>++.
```

and translates them into a CSV file of token amounts using `dcc`:

```
INCB,8
JFOR,1
INCP,1
INCB,4
JFOR,1
INCP,1
INCB,2
INCP,1
INCB,3
INCP,1
...
```

which are then sent to a Dogeparty address (slowly) as a series of token transfer transactions using `dcsend`:

```
Sending lots of tokens. Make sure you really want to do this.
Waiting for token state to synch
Row 1: INCB,8
Waiting for token state to synch...........
Row 2: JFOR,1
Waiting for token state to synch.............
Row 3: INCP,1
Waiting for token state to synch........
Row 4: INCB,4
Waiting for token state to synch..................
Row 5: JFOR,1
Waiting for token state to synch.......................
Row 6: INCP,1
Waiting for token state to synch.......................
Row 7: INCB,2
Waiting for token state to synch......
Row 8: INCP,1
Waiting for token state to synch......
Row 9: INCB,3
Waiting for token state to synch......
```

The transactions encode the program on the address, which can then be fetched and run using `dcrun`:

```
> dcrun -u rpcuser -w rpcpassword \
 DCvDS9g9VUZ94MSLbWi4zWRtxHrXeEctZ3
Hello World!
```

There’s also an easier to use runner that uses dogepartychain.info‘s API rather than requiring a local dogepartyd instance to be running, which will fetch the program encoded as Dogeparty tokens at the specified address (DCvD…) and run it locally:

```
> dcrunw DCvDS9g9VUZ94MSLbWi4zWRtxHrXeEctZ3
Hello World!
```

Here are some addresses to try:

`DCvDS9g9VUZ94MSLbWi4zWRtxHrXeEctZ3`

`DFZkhTXwAWW7PqBvVkohCFWobipqw3xmAn`

`DFibwNZvuJaHM9bD6x1WA63urkHiE4tWzF`

`DQuineX1BTF4ZD6DQxxsbUgVttmR4LvrdY`

### Warning

Be careful when writing and uploading Dogecode programs. You are responsible for ensuring that programs run as expected and that you send the correct tokens to the correct addresses. Expense and sadness will accompany any errors.

## Dogecode White Paper v0.1

### Overview

Dogecode is a system for representing computer programs using sequences of Dogeparty tokens in order to store, send, and execute their code via the Dogecoin blockchain.

### Tokens

The encoding for programs is a minor variant of the ‘Brainfuck’ programming language, chosen for its minimalism.[1](#60-Dogecode.xhtml#footnote-003)

Each Brainfuck programming language command is represented by an indivisible Dogeparty asset.

A single occurrence of a command in a program is represented by the sending of a single token, e.g. `+` is represented by sending 1 `INCB` token.

Multiple occurrences are represented by sending multiple tokens in a single transfer, e.g. `+++++` is represented by sending 5 `INCB` tokens.
