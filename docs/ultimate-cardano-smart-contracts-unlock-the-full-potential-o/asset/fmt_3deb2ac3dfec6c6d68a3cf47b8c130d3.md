
# Double Satisfaction Vulnerability

One of the most frequent vulnerabilities in Cardano Smart Contracts is the double satisfaction vulnerability, as shown in *Figure 11.10*. In this simple NFT swap implementation, the validator script looks at the datum values in each swap to validate the business logic. The assumption is that only one NFT swap is executed at one time. However, there is nothing preventing a transaction from having two swaps included in the same transaction. When this occurs, the swap validator validates each UTXO separately and both hold true so the amount of Ada that goes to Alice is double counted. She should receive 250 Ada for both NFTs but only receives 150 Ada. This is because the higher amount of 150 Ada satisfies both the NFT swap conditions, hence the double satisfaction vulnerability.

![](images/Figure-11.10.jpg)

**Figure 11.10:** Double Satisfaction Validator

There are several approaches we can take to address this exploit:

1.  Create a unique address for each swap script corresponding to the NFT being sold.
2.  Match inputs to outputs so there is a one-to-one correspondence between them.
3.  Verify and restrict the outputs that if Alice gets 150 Ada, Bob only gets one NFT B.
4.  Use a validity token such that if it is present, the transaction can proceed because validation has occurred elsewhere.
5.  We should also restrict other transaction types such as Minting and Withdraws unless there is specific business logic.

*Figure 11.11* shows a code example written in Helios for this vulnerability. On line 15, the check to see if the amount sent to the seller is at or above the price is performed.

![](images/Figure-11.11.jpg)

**Figure 11.11:** Double Satisfaction Code Exploit[^(13)](#c11.xhtml#ftn13)

To fix this code and avoid the double satisfaction vulnerability, we add a few additional checks, as shown in *Figure 11.12*. First, we require the `PKH` of the buyer in the redeemer on line 8. Second, we define contract parameters to hard code the `NFT` minting policy hash and token name for the validator script on lines 10 and 11. We also create a utility function on line 15 to recursively go through the given outputs and return the total value. Inside the main function, we check that the `NFT` value is sent to the buyer’s address using the `PKH` provided by the redeemer. Then, we calculate the total value of all of the outputs, subtract the `NFT` going to the buyer, and verify the remaining value. If the remaining value contains no other tokens, we know that the transaction only had one `NFT` in the outputs and that it went to the buyer.

![](images/Figure-11.12.jpg)

**Figure 11.12:** Double Satisfaction Fix[^(14)](#c11.xhtml#ftn14)

# Invalid Datums

We saw in the design patterns in *Chapter 9, Ticket Application Design*, that a state machine is frequently used in UTXO architecture. It involves maintaining the state in a datum and ensuring the correct datum state is updated as part of a transaction. It is always important to remember that anyone can create a UTXO and lock it at a script address with a malicious datum. Therefore, it is extremely important that a Plutus script always checks whether the inbound and outbound datums are valid. The example we will look at is a multi-sig contract for controlling when the funds can be spent by a beneficiary. It is a two-step process to exploit the vulnerability. The first step is for each required signature to sign a transaction and update the datum with their `PKH`, as shown in *Figure 11.13*.

![](images/Figure-11.13.jpg)

**Figure 11.13:** Invalid Datum Sign Tx

Although there is a check that the `PKH` of the signer is included in the outbound Datum, there is no check that the other Datum fields are not modified. This leads to the exploit where Carol changes the required number of signers from 2 to 1. Now, Bob the beneficiary can release the funds and not have to wait for the second signature, as shown in *Figure 11.14*.

![](images/Figure-11.14.jpg)

**Figure 11.14:** Invalid Datum Withdraw Tx

Let’s examine the code that contains the vulnerability, as shown in *Figure 11.15*. We define the `Datum` on line 3 and the `Redeemer` on line 9 accordingly. The two signatures allowed to sign and update the datum are hard coded as contract parameters.

![](images/Figure-11.15.jpg)

**Figure 11.15:** Invalid Datum Exploit Datum[^(15)](#c11.xhtml#ftn15)

The business logic is contained in the main function in *Figure 11.16*. In particular, line 31 checks that the datum created for the output contains the signers `PKH` in the signatures array.

![](images/Figure-11.16.jpg)

**Figure 11.16:** Invalid Datum Exploit[^(16)](#c11.xhtml#ftn16)

As we can see, the exploit allows the signer (Carol in this case) to change the required number of signatures so that Alice’s signature is no longer required. Fixing this vulnerability requires checking *all* datum values and not just the one that is getting updated. In *Figure 11.17*, we create what the output Datum is supposed to look like on line 24. We only look for an output UTXO that matches the new datum on line 30. We perform the same check that the signing `PKH` is included in the updated signatures array on line 32 but tighten the restriction to make sure there are no duplicate signatures on line 38. Finally, we ensure that the signatures list has increased by 1 on line 39.

![](images/Figure-11.17.jpg)

**Figure 11.17:** Invalid Datum Fix[^(17)](#c11.xhtml#ftn17)

# Token Leakage

Another common vulnerability we will delve into is token leakage. This can seriously impact state machines or liquidity pools that rely on a unique token being minted. Smart Contracts may incorrectly validate a transaction if more than one unique token is minted. A high-profile Cardano example was with MinSwap[^(18)](#c11.xhtml#ftn18), where this type of vulnerability was identified. Fortunately, no funds were lost, thanks to WingRiders[^(19)](#c11.xhtml#ftn19) and their quick action. An excellent write-up was provided by Tweag, who performed an audit on the code[^(20)](#c11.xhtml#ftn20).

There are variations of this type of vulnerability, and we will look at one particular type in *Figure 11.18*. It can be difficult to spot these types of vulnerabilities in multi-contract, complex applications.

![](images/Figure-11.18.jpg)

**Figure 11.18:** Token Leakage

The code in *Figure 11.19* contains an exploit allowing an attacker to mint their thread token. The `Mint Redeemer` correctly tests that the Value of what is being minted is the thread token and is a quantity of one. So, the vulnerability actually lies in the Burn redeemer used for burning a thread token. The Burn allows any token to be burned as long as it has the minting policy on line 29.

![](images/Figure-11.19.jpg)

**Figure 11.19:** Thread Token Exploit[^(21)](#c11.xhtml#ftn21)

The issue is that we are not checking the token quantity that is actually being burned; only the minted value contains a particular minting policy. To fix this issue, explicitly check the quantity that is being minted and confirm that it is negative. The code for the fix is shown in *Figure 11.20*, lines 29—31. It looks at the value that is being minted and then iterates through a `map` to check that every entry has a value of negative one.

![](images/Figure-11.20.jpg)

**Figure 11.20:** Thread Token Fix[^(22)](#c11.xhtml#ftn22)

# Audits
