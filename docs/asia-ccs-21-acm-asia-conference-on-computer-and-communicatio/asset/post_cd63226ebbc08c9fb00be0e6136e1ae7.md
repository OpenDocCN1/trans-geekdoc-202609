
```solidity
function transfer(address _from, address _to, uint _value) internal {
    require(_to != 0x0);
    require(balanceOf[_from] >= _value);
    require(balanceOf[_to] + _value >= balanceOf[_to]);
    uint previousBalances = balanceOf[_from] + balanceOf[
        _to];
    balanceOf[_from] -= _value;
    balanceOf[_to] += _value;
    emit Transfer(_from, _to, _value);
    assert(balanceOf[_from] + balanceOf[_to] ==
        previousBalances);
}
```

**Listing 3: Vulnerability example by Eth2Vec to the original function**

![](img/0d980298d6e695afbf52eecaa73818c4_8_0.png)

**Figure 2: Throughput of Eth2Vec:** We measured the throughput of Eth2Vec for each process. The “Eth2Vec Test” is identical to the vulnerability detection, which contains the detection itself and saving detection results. The “Summarizing” represents the processing time for the display process of the saved data. The entire process until a user obtains an output is a summation of EVM Extractor, Eth2Vec Test, and Summarizing. In this measurement, we randomly chose 20 contract files, where a threshold is 0.8 and five clones, i.e., candidates of vulnerabilities, at maximum for each function are output.

the given test data under such situation. Therefore, the precision becomes 0, resulting in a low average and a more extensive standard deviation. Nonetheless, when we re-compute the precision by removing the results with the few clones among ground-truth, the precision is updated to 42.7%.

## 5.4 Results of Vulnerability Detection

The results of the vulnerability detection by Eth2Vec are shown in Table 2.

First, the standard deviations of Eth2Vec are lower than those of the SVM-based method. This means that Eth2Vec diminishes the effect of difference among features of vulnerabilities because Eth2Vec can detect the vulnerabilities more stably than the SVM-based method. Therefore, Eth2Vec can precisely extract features and thus, it can take into account various vulnerabilities.

Second, we confirm that Eth2Vec is also robust against the dispersion of data. In particular, the appearance of vulnerabilities with high severity, i.e., reentrancy and time dependency, is low in the current dataset. Consequently, the number of the corresponding labels is less, and the recall of the SVM-based method became low. By contrast, the recall of Eth2Vec is more stable than that of the SVM-based method even against vulnerabilities, whose frequency of appearance is low, in comparison with the other vulnerabilities.

Moreover, when we checked an output of Eth2Vec in detail, we found a concrete example, as shown in Listing 3. The code is output as a clone of Listing 1 and the code similarity of Listing 1 with Listing 3 is lower than that with Listing 2. As difference between these codes, Listing 1 and Listing 2 do not have vulnerabilities while Listing 3 contains the integer overflow vulnerability. Specifically, line 4 in Listing 3 is different from Listing 1 with respect to an expression statement, and the statement in Listing 3 is identical to a typical form of integer overflow⁵.

The aforementioned example indicates that the vulnerability detection of Eth2Vec is robust against code rewrites. Although Listing 1 and Listing 3 seem to be more similar than Listing 1 and Listing 2, Listing 3 is different from a “precise” clone of Listing 1 because Listing 3 contains the integer vulnerability, which is not included in Listing 1. Therefore, Eth2Vec returns a higher code similarity for Listing 2 and Listing 1 than for Listing 3 and Listing 1. We thus confirm that Eth2Vec has robust vulnerability detection.

## 5.5 Inference Throughput

The throughput of the inference by Eth2Vec is shown in Figure 2. The processing time for vulnerability detection depends on the number of functions and that for displaying the detection results, i.e., summarizing by Kaml10, depends on the number of detected clones. According to the current measurement, the detection throughput of Eth2Vec is faster than that of the SVM-based method except for the process of EVM Extractor. Eth2Vec can analyze within about 0.371 seconds per contract in comparison with about 0.660 seconds per contract by the SVM-based method. Meanwhile, the processing time for displaying the detection results is longer than the detection itself. A long analysis needed 5.6 seconds for detection, 0.015 seconds for saving, and 3.5 seconds for summarizing, where the number of contracts is 9 and the number of functions is 94.

We also measured the throughput of existing symbolic execution tools, Oyente [27] and SmartCheck [45], which are publicly available and provides reproducibility. The results are shown in Table 3. According to the table, the Eth2Vec can detect vulnerabilities faster than Oyente and SmartCheck. More specifically, the standard deviation of Oyente is significantly large, and therefore the analysis time becomes exponentially large when a file containing a large number of contracts is analyzed. On the other hand, SmartCheck can detect vulnerabilities faster than Oyente since it considers only a subset of all execution paths. Nevertheless, Eth2Vec is still faster than SmartCheck. Moreover, the F1-score of SmartCheck calculated in accordance with the values in the paper [45] is 39.1% and lower than that of Eth2Vec.

## 6 DISCUSSION

In this section, we discuss further extensions and limitations of Eth2Vec.

⁵ https://github.com/ConsenSys/mythril/wiki/Integer-Overflow

## Table 2: Vulnerability Detection Results of Eth2Vec: In the following table, we measured well-known metrics for both Eth2Vec and the SVM-based method [31]. The values of the averages and standard deviations are computed from the values of each row. The "Severity" column refers to literature [45]. The numbers are truncated to one decimal place.

| Vulnerability | Severity | **Eth2Vec** Precision [%] | Recall [%] | F1-score [%] | **SVM [31]** Precision [%] | Recall [%] | F1-score [%] |
|---|---:|---:|---:|---:|---:|---:|---:|
| Reentrancy | 3 | 86.6 | 54.8 | 61.5 | 30.0 | 7.8 | 12.3 |
| Time Dependency | 2 | 75.2 | 17.0 | 27.3 | 55.0 | 2.8 | 5.3 |
| ERC-20 Transfer | 1 | 95.6 | 58.4 | 72.4 | 89.0 | 95.3 | 92.0 |
| Gas Consumption | 1 | 48.0 | 29.0 | 32.4 | 10.0 | 3.1 | 4.7 |
| Implicit Visibility | 1 | 68.9 | 82.0 | 74.8 | 71.5 | 77.5 | 73.8 |
| Integer Overflow | 1 | 89.9 | 57.6 | 70.1 | 84.9 | 73.1 | 78.3 |
| Integer Underflow | 1 | 74.6 | 56.0 | 63.7 | 75.1 | 39.2 | 50.0 |
| **Average** |  | 77.0 | 50.7 | 57.5 | 59.3 | 42.7 | 45.2 |
| **Standard Deviation** |  | 14.7 | 19.7 | 18.0 | 27.3 | 36.4 | 34.7 |

## Table 3: Comparison of Throughput with Existing Tools: We measured the throughput of Eth2Vec and those of several analysis tools. Oyente [27] and SmartCheck [45] are symbolic execution tools. Each value represents the average time per contract. The numbers are truncated to two decimal place.

|  | Eth2Vec | SVM [31] | Oyente [27] | SmartCheck [45] |
|---|---:|---:|---:|---:|
| Average [sec] | 0.37 | 0.66 | 3.52 | 0.50 |
| Standard Deviation | 0.59 | 0.60 | 11.45 | 0.71 |

Second, the current work only detected vulnerabilities in contracts included in the training dataset utilized in our experiment. There are potentially many vulnerable contracts that have already been deployed, and thus it would be ideal if all deployed contracts are analyzed to determine potential vulnerabilities.

Finally, the current construction does not support inter-contract analysis where multiple contracts are interconnected. For instance, Rodler et al. [37] presented a new kind of vulnerability by utilizing CALL and CREATE instructions, which requires inter-contract analysis [8, 49]. Thus, the attacks by Rodler et al. are out of the scope of Eth2Vec currently. Our future work will aim to extend the current construction of Eth2Vec and overcome the limitations described above.

### 6.1 Further Extensions

Possible extensions of Eth2Vec are described below.

First, important features for detecting vulnerabilities can be clarified by introducing the interpretability of neural networks. Although the current specification of Eth2Vec does not provide insight into the important features, the importance for each feature can be evaluated on Eth2Vec by utilizing a universal method, e.g., permutation importance [5].

Second, the output of Eth2Vec with respect to vulnerabilities can be extended from the current function-level to the instruction-level. Asm2Vec [11], which is an application of Kam1n0, outputs vulnerabilities for the instruction-level by utilizing AbstractCloneSearch Handler of Kam1n0. Eth2Vec will be able to output vulnerabilities for the instruction-level by incorporating the module.

### 6.2 Limitations

Several limitations of Eth2Vec, which will be improved in future works, are described below. First, the current construction is in the unsupervised setting, and the supervised setting is not implemented. According to Hill et al. [20], the supervised setting seems to be more suitable for the classification of natural language processing than the unsupervised setting. Intuitively, evaluating a kind of vulnerability contained in codes is a classification problem about vulnerabilities. Therefore, the performance of Eth2Vec can be improved by utilizing the supervised setting.

## 7 RELATED WORKS

In this section, we describe related works in terms of security analysis by machine learning.

### 7.1 Security Analysis of Ethereum by Machine Learning

As machine learning-based analysis, ContractWard [48] and the tool by Momeni et al. [31] are based on support vector machine (SVM) and random forest, whose features are extracted manually by an analyst. Hence, identifiable vulnerabilities are limited due to insufficient feature extraction as described in Section 3. As research on automated feature extraction, VulDeeSmartContract [36] has been proposed by combining Word2Vec with long-short term memory (LSTM), but it specializes only in reentrancy vulnerability. Eth2Vec can be considered as a tool dealing with more versatile vulnerabilities in a similar approach.

Next, EClone [25] is a tool that detects code clones of Ethereum smart contracts through the computation of code similarity. Although EClone does not utilize neural networks, a symbolic analysis tool suitable for vector computations of codes has also been proposed. The detectability of Eth2Vec can be improved potentially by combining it with EClone.
