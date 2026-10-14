
In the previous example, it is not possible to know which addresses belong to Bob, Dave, and Kirsten, nor who is paying whom in which output.

# Tumbler Services

Tumbler services are provided by anonymous exchanges and are untraceable because they mostly use the TOR network. They charge a fee for the mixing transaction. Tumbler services receive bitcoins from the sender and forward them to the receiver, but in the intermediate process, they mix these bitcoins with other transactions or their own transactions and move them between multiple addresses. This makes tracing impossible.

This can be understood from the figure below:

![](images/Figure-8.15.jpg)

**Figure 8.15:** Tumbler Service Example

In the figure above, it is not possible to know if Alice is paying Bob, or Carol is paying Dave, or John is paying Kirsten, because all transactions are completely mixed, separated, and uncorrelated.

Unlike CoinJoin offered by some popular wallets, Tumbler services are not offered by any known entity. This is the nature of their operation. Hence, such services carry a risk because they may steal your coins.

# Bitcoin Mining Energy Consumption

Bitcoin has a bad reputation for its high energy consumption, which is indeed true, as shown in the figure below:

![](images/Figure-8.16.jpg)

**Figure 8.16:** Bitcoin Mining Energy Consumption Compared to Top Countries by Electricity Usage

The figure above shows the top 50 countries by energy consumption. Bitcoin currently ranks 24th, with energy consumption close to Poland—a developed, wealthy European country.

In comparison, global energy consumption is 23,000 TWh, while Bitcoin's energy consumption is only 154 TWh, less than 1.0%. Bitcoin energy consumption correlates with currency growth. As interest in Bitcoin grows, the energy consumption of the Bitcoin network will increase accordingly.

We will perform some calculations to understand why the situation is not as bad as it looks.

To avoid promoting mining equipment, we will not disclose the name of the mining equipment used as a reference.

Assume I am using a mining device at a location in Bangalore city, with current electricity rates as follows:

![](images/262.jpg)

**Table 8.2:** Bangalore City Electricity Rates

We use the same procedure as in the "Mining Cost" topic in *Chapter 6 Blockchain, Transactions, and Mining*.

We adopt a miner with a hash rate of 90 TH/s and power consumption of 3050W, defined as follows:

```
def getMinerHashRate():
    return 100 * 10**12

def getMinerPowerWatt():
    return 3050
```

We define the unit price as follows:

```
electricity_rates = {"rate_slabs": [{"min": 1, "max": 30, "unit_price": 4}, {"min": 31, "max": 100, "unit_price": 5.45}, {"min": 101, "max": 200, "unit_price": 7}, {"min": 201, "unit_price": 8.05}]}
```

If the current Bitcoin price is ₹28,05,753, defined as follows:

```
def getCurrentSellPrice():
    return 2805753
```

The following code calls the `miningReturn` method to get mining profitability:

```
blk_hash = '000000000000000000016acc33775c2ea52abeb4407381b84fee5f7af97fdd8b'
blk_hash_b = bytes.fromhex(blk_hash)[::-1]
blk_index = getBlockIndex(blk_hash, block_db_g)
blk_hdr_b = getBlockHeaderBytes(blk_hash_b)
jsonobj = getBlockHeader(blk_hdr_b)
blk_reward = getBlockReward(blk_index['height'])
miner_hashrate = getMinerHashRate()
print("Miner hashrate = %d" % (miner_hashrate))
miner_power = getMinerPowerWatt()
print("Miner Power in Watt = %f" % (miner_power))
expense = getMiningPowerExpense(miner_power)
print("Miner Power Expense Per Month = %.2f" % (expense))
bits_b = bytes.fromhex(jsonobj['bits'])[::-1]
mining_return = miningReturn(miner_power, miner_hashrate, bits_b, blk_reward)
print("Mining Return Per Month = %s" % (mining_return))
```

Upon running, we get the following results:

![](images/Figure-8.17.jpg)

**Figure 8.17:** Mining Profitability of Test Miner in Bangalore

The equipment cost is nearly ₹9,00,000/-.

If the mining reward remains constant, it will take 3 years to break even on the equipment cost. This looks like a reasonable return, but considering the mining hashrate may double during this period, monthly mining returns could drop to between 0 and ₹5,000, becoming negligible, at which point you would need to buy another device, which may cost more and consume more power. Hence, you may never break even. On the positive side, Bitcoin prices may rise within 3 years, keeping mining profitable.

This makes mining a risky proposition unless you have subsidized electricity, cheap power, or power from waste fuel or energy.

Hence, large miners are mostly located in countries where electricity is subsidized. Also, many power generation companies and fossil fuel companies are mining Bitcoin to utilize their excess power and fuel. Natural gas and oil drilling companies use flare gas for Bitcoin mining, which is particularly beneficial for the environment because methane is a much more potent greenhouse gas than carbon dioxide.

Wind and solar have better fuel efficiency than non-renewables, except for natural gas and nuclear. Also, off-grid power saves energy waste in transmission, further improving mining profitability. This makes off-grid renewables the preferred energy source for non-subsidized mining.

For governments subsidizing Bitcoin mining electricity, it is costly because it creates almost no jobs, so governments tend to crack down on such facilities, as seen in China and Iran.

Therefore, contrary to contemporary views, we learn that Bitcoin mining is beneficial for the environment because:

*   Miners tend to use off-grid renewables as a power source.
*   Waste fuel composed of the most potent greenhouse gas is used for Bitcoin mining and converted into a less potent greenhouse gas—carbon dioxide.
*   Bitcoin mining discourages governments from subsidizing electricity for mining companies.

# Threats to Individuals and the Network

So far in this chapter, you have learned about design limitations and how the Bitcoin developer community strives to overcome them. You also learned that the high energy consumption of Bitcoin mining is not a major problem for the environment.

Bitcoin, as a decentralized peer-to-peer open value transfer network, is both a target of interest for attackers and perceived as a threat to the existing global monetary system. Therefore, the Bitcoin network and Bitcoin investors may have to deal with various attacks, such as those from governments, central banks, malicious hackers, fraudsters, or theft.

However, threats do not always arise from various types of attacks; they can also stem from risks and potential vulnerabilities that currently exist or may arise in the future.

# Threats from Governments

As seen in *Chapter 4 Bitcoin in the Real World* under the topic "Bitcoin and Cryptocurrency Regulation," in most countries of the world, cryptocurrency laws are unclear or non-existent. This gives authorities quasi-judicial powers to deal with cryptocurrencies, sometimes involving threats and corruption. Sometimes taxes are due, but tax clauses are unclear. This is a problem in India and many other countries. This affects exchanges, traders, investors, and merchants, leading to inflated prices for cryptocurrencies and related services, and the risk of investment or business loss.

There is also a lack of legal protection, which is sometimes abused by miscreants through extortion and fraud.

Banning Bitcoin transactions is a potential risk, and some countries have indeed taken this route, meaning anyone dealing in cryptocurrencies would be punished. However, very few countries have done so.
