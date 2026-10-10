
# Ethereum: Tools & Skills

Copyright © 2018 SitePoint Pty. Ltd.

Ebook ISBN: 978-1-925836-02-8

- **Cover Design:** Alex Walker
- **Project Editor:** Bruno Škvorc

## Notice of Rights

All rights reserved. No part of this book may be reproduced, stored in a retrieval system or transmitted in any form or by any means, without the prior written permission of the publisher, except in the case of brief quotations embodied in critical articles or reviews.

## Notice of Liability

The author and publisher have made every effort to ensure the accuracy of the information herein. However, the information contained in this book is sold without warranty, either express or implied. Neither the authors and SitePoint Pty. Ltd., nor its dealers or distributors will be held liable for any damages to be caused either directly or indirectly by the instructions contained in this book, or by the software or hardware products described herein.

## Trademark Notice

Rather than indicating every occurrence of a trademarked name as such, this book uses the names only in an editorial fashion and to the benefit of the trademark owner with no intention of infringement of the trademark.

![SitePoint logo](images/00001.gif)

Published by SitePoint Pty. Ltd.

48 Cambridge Street Collingwood  
VIC Australia 3066  

Web: www.sitepoint.com  
Email: books@sitepoint.com

## About SitePoint

SitePoint specializes in publishing fun, practical, and easy-to-understand content for web professionals. Visit [http://www.sitepoint.com/](http://www.sitepoint.com/) to access our blogs, books, newsletters, articles, and community forums. You'll find a stack of information on JavaScript, PHP, design, and more.

# Preface

As the Ethereum platform has grown, so has the ecosystem of tools that support it. In this book, we'll examine some of the most popular Ethereum tools, and walk you through how to use them when building your own Ethereum-based apps.

## Who Should Read This Book?

This book is for anyone interested in using the Ethereum platform for development. It's advised that you read *The Developer's Guide to Ethereum* before reading this book if you are not familiar with blockchain technology.

## Conventions Used

### Code Samples

Code in this book is displayed using a fixed-width font, like so:

```
<h1>A Perfect Summer's Day</h1>
<p>It was a lovely day for a walk in the park.
The birds were singing and the kids were all back at school.</p>
```

Where existing code is required for context, rather than repeat all of it, `⋮` will be displayed:

```
function animate() {
    ⋮
    new_variable = "Hello";
}
```

Some lines of code should be entered on one line, but we've had to wrap them because of page constraints. An `➥` indicates a line break that exists for formatting purposes only, and should be ignored:

```
URL.open("http://www.sitepoint.com/responsive-web-
➥design-real-user-testing/?responsive1");
```

You'll notice that we've used certain layout styles throughout this book to signify different types of information. Look out for the following items.

### Tips, Notes, and Warnings

#### Hey, You!

Tips provide helpful little pointers.

#### Ahem, Excuse Me ...

Notes are useful asides that are related—but not critical—to the topic at hand. Think of them as extra tidbits of information.

#### Make Sure You Always ...

... pay attention to these important points.

#### Watch Out!

Warnings highlight any gotchas that are likely to trip you up along the way.

# Chapter 1: Remix: Develop Smart Contracts for the Ethereum Blockchain

### by Ahmed Bouchefra

**Remix is a Solidity IDE that's used to write, compile and debug Solidity code. [Solidity](https://solidity.readthedocs.io) is a high-level, contract-oriented programming language for writing smart contracts. It was influenced by popular languages such as C++, Python and JavaScript.**

`IDE` stands for Integrated Development Environment and is an application with a set of tools designed to help programmers execute different tasks related to software development such as writing, compiling, executing and debugging code.

Before you begin using Remix to develop smart contracts, make sure you're familiar with some basic concepts. In particular, give these articles about [blockchain](https://www.sitepoint.com/blockchain-what-it-is-how-it-works-why-its-so-popular) and [Ethereum](https://bitfalls.com/2017/09/19/what-ethereum-compare-to-bitcoin/) a read.

### What's a Smart Contract/Dapp?

A smart contract is a trust-less agreement between two parties that makes use of blockchain technology, to enforce the parties to adhere to the terms, rather than relying on the traditional ways such as trusting a middleman or using laws to handle disputes.

Using the Ethereum blockchain, you can create smart contracts with the Solidity language (among others). Ethereum is not the only platform that can be used to create smart contacts, but it's the most popular choice, as it was designed from the start to support building them.

[Dapp](http://ethdocs.org/en/latest/contracts-and-transactions/developer-tools.html#dapps) stands for **de*centralized *app*lication** and is a web3 application that can have a front-end written in traditional languages such as JavaScript, HTML, CSS and a smart contract (as back-end code) which runs on the blockchain. So you can simply think of a Dapp as the front end plus the associated blockchain smart contract(s).

Unlike the smart contract deployed on the blockchain itself, the front end of a Dapp can be either hosted on a centralized server like a CDN or on decentralized storage like [Swarm](http://ethdocs.org/en/latest/contracts-and-transactions/developer-tools.html#swarm).

## Accessing the Remix IDE

You can access the Remix IDE in different ways: online, via a web browser like Chrome, from a locally installed copy, or from Mist (the Ethereum Dapp browser).

### Using the In-Browser Remix IDE

You can access the Remix IDE from your web browser without any special installation. Visit [https://remix.ethereum.org/](https://remix.ethereum.org/) and you'll be presented with a complete IDE with a code editor and various panels for compiling, running and debugging your smart contracts. You'll have a default example *Ballot* contract that you can play with.

![Remix IDE](images/00002.jpeg)

### Starting Remix IDE from Mist

You can start the Remix IDE from Mist by clicking on *Develop*, then *Open Remix IDE*. Remix will be opened in a new window. If this is your first time running the IDE, you'll be presented with a simple example *Ballot* contract.

To get familiar with Mist, please see [this article](https://bitfalls.com/2018/02/12/explaining-ethereum-tools-geth-mist/).

### Running your Own Copy of Remix IDE

You can also run your own copy of Remix IDE by executing the following commands:

```
npm install remix-ide -g
remix-ide
```

You need to have Node.js and npm installed. Check this [GitHub repository](https://github.com/ethereum/remix-ide) for more information.

## Remix Panels

After seeing how to open the Remix IDE, let's now see the various panels composing the IDE.

### File Explorer

The file explorer provides a view with the created files stored in the browser's storage. You can rename or delete any file by right-clicking on it, then choosing the right operation from the context menu.

![context menu options](images/00003.jpeg)

Please note that the file explorer uses the browser's local storage by default, which means you can lose all your files if you clear or the operating system automatically clears the storage. For advanced work, it's recommended to use [Remixd](https://github.com/ethereum/remixd) — a Node.js tool (available from npm `npm install -g remixd`) which allows the Remix IDE to access your computer's file system.

Now let's see the different actions that you can perform using the buttons at the top of the explorer.

![Remix buttons](images/00004.jpeg)

#### Creating/Opening Files in Remix
