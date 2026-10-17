
contracts or with other accounts.

`»` Transactions between accounts can only be requests to

`transfer` funds (ETH).

`»` An account is not a wallet, and a wallet is not an account.

Wallet services, such as MetaMask, are designed to help you

manage your Ethereum accounts. Much like you can use differ-

ent email clients to access emails sent to your email address, you

can use different wallet services to access your Ethereum

accounts.

Creating an account is simple and free. It doesn’t cost any ETH

to create an account, though you do need to fund your account

before you can submit transactions, which — as we discuss in

Chapter 6 — aren’t always simple and certainly aren’t free.

116  PART 3  Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

What it means to create 

an account

Many wallet services can create accounts for you. These services,

such as MetaMask, are just generating key pairs:

`»` A private key: You use your private key to access funds in

your account, so you should never share your private key.

`»` A corresponding public address: You can share your

public address with other, so that you can receive funds

from other accounts.

Of course, you don’t need a wallet service to generate your key

pairs for you. In fact, selecting a private key is as simple as pick-

ing a random number between 0 and 2256, which is greater than

1 trillion to the power of 6 — or 1 trillion × 1 trillion × 1 trillion ×

1 trillion × 1 trillion × 1 trillion ×

1 trillion × 1 trillion × 1 trillion.

Because there are so many possible private keys, even if all

8 billion people on Earth each created 1,000 accounts, the total

number of active accounts — 8 trillion, in this scenario — would

be far less than the total number of possible accounts. Guessing

or generating a private key that’s already being used is unlikely.

Still, having a wallet service do the heavy lifting has its benefits,

especially if you aren’t mathematically adept. Technically, you

must pick a private key value greater than 0 and less than

FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFEBAAEDCE6AF48A03BBF

D25E8CD0364141 (which is less than the value of 2256).

Private keys are expressed as 64-digit hexadecimal numbers,

which is a base 16 notional system where each digit is repre-

sented by one of the following 16 characters: 0, 1, 2, 3, 4, 5, 6, 7,

8, 9, A, B, C, D, E, or F. For example:

`»` 412 in hexadecimal is equal to (4 × 163) + (1 × 162) + (2 × 160)

= 16,642 in decimal numbers, with which we’re

more familiar.

`»` F9C3 in hexadecimal is equal to (15 × 164) + (9 × 163) +

(12 × 162) + (3 × 160) = 1,022,979 in decimal numbers.

CHAPTER 7 Creating an Ethereum Account  117

As you process the calculations above, keep in mind that any number to the power of zero is equal to one.

After you randomly generate a private key, you need to generate

a corresponding public key via an Elliptic Curve Digital Signature

Algorithm (ECDSA). (Both Bitcoin and Ethereum use the

secp256k1 ECDSA as their algorithm for public key generation.)

After that, you still need to hash the resulting public key using

the keccak256 hash function, take the last 40 hexadecimal dig-

its (or last 20 bytes), and then add “0x” to the beginning to

arrive at your public account address. See the later section “Dig-

ital signatures” to find out more about the mathematical algo-

rithms used for authentication.

Private versus public keys

You use your private key to withdraw funds from your account;

your public address is what you can publicly display to receive

funds to your account. Of course, you must know your account’s

private keys if you want to access your accounts from a different

wallet service that you haven’t yet used to access those particu-

larly accounts.

To access your account’s private key and public address on

MetaMask, follow these steps:

1`\.` Log in to MetaMask. 

Your account’s name appears with its public address

beneath it, as shown in Figure 7-1. In this case, the account

name is NFTs For Dummies, and the public address is

`0xf77a3cE366E32645ffC78B9a88B7e90583646df9`

2`\.` Click the account name to copy your public address. 

The public address has 42 digits in hexadecimal notation (or

40 hexadecimal digits with a “0x” prefix added.

118  PART 3  Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

![](images/00045.jpg)

![](images/00060.jpg)

FIGURE 7-1:

The account

name and

public

address

displayed

on

MetaMask.

3`\.` Click the vertical ellipses to the right of the account name 

and choose Account Details from the drop-down menu, as 

shown in Figure 7-2. 

The Account Details tab, shown in Figure 7-3, appears.

FIGURE 7-2:

Accessing

additional

account

details on

MetaMask.

4`\.` Click the Export Private Key button. 

5`\.` Enter your MetaMask wallet password and click Confirm, 

as shown in Figure 7-4. 

CHAPTER 7 Creating an Ethereum Account  119

![](images/00074.jpg)

![](images/00088.jpg)

FIGURE 7-3:

The Account

Details

tab on

MetaMask.

FIGURE 7-4:

Password

prompt to

access an

account’s

private

key on

MetaMask.

120  PART 3  Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

![](images/00104.jpg)

6`\.` Now you can simply click to copy the account’s private key. 

For the NFTs For Dummies account shown in Figure 7-5, we

get the following private key, which is 64 digits in hexadeci-

mal notation:

`0bf71f18f67efa95140d5fe4c68afe06f9c9e475b0dde`

`035d06a83d8026f441c`

FIGURE 7-5:

An

account’s

private key,

displayed

on

MetaMask.

Of course, do not announce your private key to the world (as we

have just done here).

Overall, private and public keys are used together to form a digi-

tal signature to validate a transaction. This process ensures that

only the rightful account owner can submit transactions from a

given account.

Digital signatures

How does the private/public key pair work to ensure that only

you can spend the ETH in your account? By using digital signa-

tures,  which are mathematical algorithms that validate the

authenticity of a digital message or document. Here, we provide

CHAPTER 7 Creating an Ethereum Account  121

a simple example of how digital signatures work. The basic elements are listed here:

`»` A single public key corresponds to each private key.

`»` Revealing your public key doesn’t provide information

about your private key.

`»` Your private key is combined with your public key and your

transaction information to form a signature.

`»` This signature, along with your requested transaction, is

broadcasted throughout the network.

`»` When validators apply your public key to the publicly

broadcasted signature, they should get back the original

transaction information.

Suppose that you have a private key, Kpriv = {7}, that only you

know and a corresponding public key, Kpub = {3, 33}, that is

shared with everyone. Also suppose that you want to send 16

ETH from this account.

The following steps show, in a simplified way, how digital sig-

natures can work to prove that you’re the rightful owner of the

account in question:

1`\.` Take the number 16 (the amount you wish to send) to 

the power of 7 (your private key) and then divide by 33 

(which is part of the public key). 

In other words, divide 167 by 33. The remainder of this

division is equal to 25. This number, 25, which is your digital

signature for this transaction, proves that you’re the rightful

account owner without revealing your private key.

2`\.` Submit your 16 ETH transfer request along with your digital 

signature of 25. 

That is, broadcast the pair of numbers {16, 25} for

verification.

3`\.` To verify that you’re the rightful owner, validators apply 

your known public key K  \= {3, 33} by taking 25 to the 

pub

power of 3 and then dividing by 33. 

The remainder of this division is exactly equal to 16, proving

that you’re the rightful owner.

122  PART 3  Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT
