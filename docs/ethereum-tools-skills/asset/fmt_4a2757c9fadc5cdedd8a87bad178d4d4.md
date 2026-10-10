
Downloading...
Unpacking...
Setting up...
Unbox successful. Sweet!

Commands:

*   Compile contracts: `truffle compile`
*   Migrate contracts: `truffle migrate`
*   Test contracts: `truffle test`

If you get some errors, it could be that you’re using a different version of Truffle. The version this tutorial is written for is `Truffle v4.1.5`, but the instructions should stay relevant for at least a couple of versions.

## The Truffle Project Structure

Your Truffle folder should look a little bit like this:

```
.
├── contracts
│   ├── ConvertLib.sol
│   ├── MetaCoin.sol
│   └── Migrations.sol
├── migrations
│   ├── 1_initial_migration.js
│   └── 2_deploy_contracts.js
├── test
│   ├── TestMetacoin.sol
│   └── metacoin.js
├── truffle-config.js
└── truffle.js
```

### Contracts Folder

This is the folder where you will put all of your smart contracts.

In your contracts folder, there’s also a `Migrations.sol` file, which is a special file — but more about that in the following section.

When Truffle compiles the project, it will go through the `contracts` folder and compile all the compatible files. For now, the most used files are Solidity files with the `.sol` extension.

In the future, this might transition to Vyper or SolidityX (both better for smart contract development, but less used for now).

## Migrations Folder

What is a truffle migration? In essence it’s a script which defines *how* the contracts will be deployed to the blockchain.

### Why do we need migrations?

As your project becomes more and more complex, the complexity of your deployments becomes more and more complex accordingly.

Let’s take an example:

*   You have smart contracts `One`, `Two` and `Three`
*   The smart contract `Three` contains a reference to the smart contract `One` *and* requires the address of contract `Two` in its constructor.

This example requires that contracts not only to be deployed sequentially, but also that they cross reference each other. Migrations, in a nutshell, enable us to automate this process.

A rough overview of how you would do this would be as follows:

```
var One = artifacts.require("One");
var Two = artifacts.require("Two");
var Three = artifacts.require("Three");

module.exports = function(deployer) {
  deployer.deploy(One).then(function() {
    deployer.deploy(Two).then(function() {
      deployer.deploy(Three, One.address);
    })
  });
};
```

Beyond that, migrations allow you to do a lot of other cool things like:

*   set max gas for deployments
*   change the `from` address of deployments
*   deploy libraries
*   call arbitrary contract functions

### Initial Migration

As you’ve noticed in your `MetaCoin` project, you have a file called `1_initial_migration.js`. What this file does is deploy the `Migrations.sol` contract to the blockchain.

Usually you don’t have to do anything to this file once it’s initialized, so we won’t focus too much on this.

## Test Folder

As I’ve said: YOU! MUST! TEST! SMART! CONTRACTS! No buts, no ifs, no maybes: you MUST do it.

But if you’re going to do it, it would be cool to have an automatic tool to enable you to do it seamlessly.

Truffle enables this by having a built-in testing framework. It enables you to write tests either in Solidity or JavaScript.

The examples in the MetaCoin project speak for themselves basically, so we won’t get too much into this.

The key is, if you’re writing Solidity tests, you import your contracts into the tests with the Solidity `import` directive:

```
import "../contracts/MetaCoin.sol";
```

And if you’re writing them in JavaScript, you import them with the `artifacts.require()` helper function:

```
var MetaCoin = artifacts.require("./MetaCoin.sol");
```

## Configuration File

The configuration file is called either `truffle.js` or `truffle-config.js`. In most cases it’ll be called `truffle.js`, but the fallback is there because of weird command precedence rules on Windows machines.

Just know that, when you see `truffle.js` or `truffle-config.js`, they’re the same thing, basically. (Also, don’t use CMD on windows; PowerShell is significantly better.)

The config file defines a couple of things, detailed below.

**Environments** Develop, TestNet, Live (Production). You can define the address of the Geth note, the `network_id`, max gas for deployment, the gas price you’re willing to pay.

**Project structure** You can change where the files are built and located, but it isn’t necessary or even recommended.

**Compiler version and settings** Fix the `solc` version and set the `-O` (optimization) parameters.

**Package management**

*   Truffle can work with EthPM (the Ethereum Package Manager), but it’s still very iffy.
*   You can set up dependencies for EthPM to use in your Truffle project.

**Project description** Who made the project, what is the project name, contact addresses etc.

**License** Use [GPLv3](https://pbs.twimg.com/profile_images/561116211258220544/FlICmGnj_400x400.jpeg).

## Running the Code

In order to compile your contracts, run this:

```
truffle compile
```

In order to run migrations, you can just use this:

```
truffle migrate
```

Or you can do it by specifying an environment:

```
truffle migrate --network live
```

In order to test your contracts run this:

```
truffle test
```

Or you can run a *specific* test by running this:

```
truffle test ./path/to/FileTest.sol
```

## Conclusion

Truffle is a very handy tool that makes development in this brand new ecosystem a little easier. It aims to bring standards and common practices from the rest of the development world into a little corner of blockchain experimentation.

# Chapter 5: Quality Solidity Code with OpenZeppelin and Friends

### by Tonino Jankov

**Given the fact that all of [Ethereum’s](https://bitfalls.com/2017/09/19/what-ethereum-compare-to-bitcoin/) computations need to be reproduced on all the [nodes](https://bitfalls.com/2017/11/26/whats-bitcoin-node-mining-vs-validation/) in the network, Ethereum’s computing is inherently costly and inefficient. (In fact, Ethereum’s developer docs on GitHub state that we shouldn’t expect more computational power from Ethereum than we do from a 1999 phone.)**

So, security on the Ethereum Virtual Machine — meaning, the security of smart contracts deployed on Ethereum blockchain — is of paramount importance. All the errors on it cost real money — whether it’s errors thrown by badly-written contracts, or hackers exploiting loopholes in contracts, like in the well-known DAO hack, which caused a community split and sprang the Ethereum Classic blockchain into existence.

*Turing Completeness* — and a whole range of other design decisions that have made Ethereum a lot more capable and sophisticated — have come at a cost. Ethereum’s richness has made it more vulnerable to errors and hackers.

To add to the problem, smart contracts deployed on Ethereum cannot be modified. The [blockchain](https://www.sitepoint.com/blockchain-what-it-is-how-it-works-why-its-so-popular) is an immutable data structure.

[This](https://medium.com/loom-network/how-to-secure-your-smart-contracts-6-solidity-vulnerabilities-and-how-to-avoid-them-part-1-c33048d4d17d) and [this](https://medium.com/loom-network/how-to-secure-your-smart-contracts-6-solidity-vulnerabilities-and-how-to-avoid-them-part-2-730db0aa4834) article go into more depth regarding security of smart contracts, and the ecosystem of tools and libraries to help us to make our smart contracts secure.

Let’s look at some amazing upgrades to our toolset we can use *today* to utilize the best practices the Solidity environment can offer.

## Helper Tools
