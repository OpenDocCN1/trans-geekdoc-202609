I also wrote this book because cryptography has expanded into a multi-disciplinary field. To do anything useful and relevant in crypto, you need to understand the concepts *around* crypto: how networks and computers work, what users and systems need, and how attackers can abuse algorithms and their implementations. In other words, you need a connection to reality.

# This Book’s Approach

The initial title of this book was *Crypto for Real* to stress the practice-oriented, real-world, no-nonsense approach I follow. I wanted to make cryptography approachable not by dumbing it down but by tying it to real applications. I provide source code examples and describe real bugs and horror stories.

Along with a clear connection to reality, other cornerstones of this book are its simplicity and its modernity. I focus on simplicity in form more than in substance: I present nontrivial concepts without the dull mathematical formalism. Instead, I attempt to impart an understanding of cryptography’s core ideas, which are more important than remembering a bunch of equations. To ensure the book’s modernity, I cover the latest developments and applications of cryptography, such as TLS 1.3 and post-quantum cryptography. I don’t discuss the details of obsolete or insecure algorithms such as DES or MD5. An exception to this is RC4, but it’s included only to explain how weak it is and to show how a stream cipher of its kind works.

*Serious Cryptography* isn’t a guide to crypto software, nor is it a compendium of technical specifications—stuff that you’ll easily find online. Instead, its foremost goal is to get you excited about cryptography and teach you its fundamental concepts along the way.

# Who This Book Is For

While writing, I often imagined the reader as a developer who’d been exposed to cryptography but still felt clueless and frustrated after reading abstruse textbooks and research papers. Developers often need—and want—a better grasp of crypto to avoid unfortunate design choices, and I hope this book helps.

If you aren’t a developer, don’t worry! The book doesn’t require coding skills and is accessible to anyone who understands the basics of computer science and high school math (notions of probabilities, modular arithmetic, and so on).

This book can nonetheless be intimidating, and despite its relative accessibility, it requires some effort to get the most out of it. I like the mountaineering analogy: the author paves the way, providing you with ropes and ice axes to facilitate your work, but you make the ascent yourself. Learning the concepts in this book takes effort but is rewarding.