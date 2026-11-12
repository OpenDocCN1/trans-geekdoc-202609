inspect its internal attributes. Moreover, a SmartInspect approach can introspect the current state of a smart contract instance without the need to redeploy it or develop additional code for decoding. SmartInspect is implemented in Pharo and it is publicly available in GitHub as part of the SmartAnvil tool suite (github.com/RMODINRIA- Blockchain/SmartShackle).

The general idea of the Smart Inspector is to decompile the storage layout encoded by the Ethereum API. By using the contract source code as reference, it is possible to know where the attribute values are stored in the encoded binary structure (Figure 13.3). It was a challenge to decompile the memory layout because the Solidity documentation [Eth18c] is incomplete regarding how some types are encoded. Therefore, we had to reverse engineer some of the encoding performed by the compiler ourselves.

After we decoded the memory layout, we still needed to apply our solution to any contract for a general reusable solution. We employ a mirror-based architecture [BU04] that mimics the structure of any contract for us to access the memory layout that we can decode. A mirror works like an independent meta-programming layer that splits the concern of reflection capabilities into a mirror object. First, we require the contract source code as input to start building the mirror. Then we parse the source code (using our Solidity parser described earlier) to create an AST (abstract syntax tree). By interpreting the

![](bbox=[0.126, 0.51, 0.873, 0.87])

# Figure 13.3 Memory layout representation