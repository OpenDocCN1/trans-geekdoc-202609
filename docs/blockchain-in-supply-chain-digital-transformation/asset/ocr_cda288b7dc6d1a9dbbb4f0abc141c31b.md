+   - *Step 5:* The new strategy is deployed on the actual network in an attempt to increase α, consequently resulting in a lower *Revenue*<sub>honest</sub>.

# 4.5.2 Difficulty Recalibration Attack

The Bitcoin network aims to, on average, generate one block every 10 minutes. To maintain this block creation time, the network periodically makes it harder or easier for the rest of the network to find a solution for the nontrivial mathematical problem. This change in the difficulty of mining is referred to as the difficulty of recalibration. In Bitcoin, the difficulty recalibration is performed after 2015 blocks [54].

The block creation time is often referred to as a bottleneck for the performance of the blockchain, which is often measured in transactions per second (TPS) [44], [31]. In contrast to the traditional payment systems, Bitcoin exhibits a low TPS speed. The low TPS has been speculated to be a barrier in the mainstream adoption of bitcoin as a payment system [40].

The irrational attacker can further slow the adoption by artificially manipulating the TPS of Bitcoin. We speculate that the time difference between two difficulty recalibrations may be exploited to harm the network. We devise a novel strategy in which the attacker will first attain a significant α followed by sudden withdrawal from the network. We have illustrated the attack flow in Figure 2.

The attack is significantly limited by the security provision in the Bitcoin core client, which limits the maximum rise or fall in the value of the difficulty after every recalibration [22]. However, this limit does not omit the possibility of an attack over a more extended period. The abrupt change in the total hash power induced by the irrational attacker will cause the *Revenue*<sub>honest</sub> to fluctuate significantly over time, making it less reliable to mine. When the difficulty decreases after the attacker leaves the network, the block creation time will increase significantly due to the high difficulty. This increase in block creation time will subsequently

![](bbox=[0.238, 0.697, 0.812, 0.872])