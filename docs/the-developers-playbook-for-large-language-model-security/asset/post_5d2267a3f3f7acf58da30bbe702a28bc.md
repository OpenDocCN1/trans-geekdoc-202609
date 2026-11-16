
Beyond that core audience, I’ve learned that others have found much of this information useful. This includes the extended teams involved in these projects, who want to understand the underpinnings of the technologies to help mitigate the critical risks of adopting these new technologies. These include software development executives, chief information security officers (CISOs), quality engineers, and security operations teams.

## Why I Wrote This Book

I’ve always been fascinated by artificial intelligence. As a preteen, I fondly remember writing video games on my Atari 400 home computer. Circa 1980, this little machine had only 8 kilobytes of RAM. But I still managed to cram a complete clone of the Tron Lightcycles game onto that machine, complete with a simple but effective AI to drive one of the cycles when you were playing in single-player mode.

In my professional career, I’ve been involved with several AI-related projects. After college, my best friend Tom Santos and I started an AI software company based on a few thousand lines of handcrafted C++ code that solved seemingly intractable problems with genetic algorithms. I’d later help build a large-scale machine learning system at Citrix with my friends Kedar Poduri and Ebenezer Schubert. But when I saw ChatGPT for the first time, I knew everything had changed.

When I first encountered LLMs, I worked at a company that built cybersecurity software. My job was helping large companies find and track vulnerabilities in their software. It quickly became apparent that LLMs offered unique and serious security vulnerabilities. Over the next few months, I retooled my career to go after this disruption. I started a popular open source project around LLM security, which you’ll hear more about later. I even switched jobs to join Exabeam, a company that works at the intersection of AI and cybersecurity. When an editor from O’Reilly approached me about writing a book on this topic, I knew I had to jump at the chance.

## Navigating This Book

This book has 12 chapters that are divided into three logical sections. I’ll sketch out each section and chapter here to give you an idea of the approach and so you’ll know what’s coming as you read.

## Section 1: Laying the Foundation (Chapters 1–3)

The initial chapters of this book establish the groundwork for understanding the security posture of LLM-based applications. They should give you the grounding you can use to confidently unpack the issues facing the development of apps using LLMs:

- Chapter 1, “Chatbots Breaking Bad”, walks through a real-world case study whereby amateur hackers destroyed an expensive and promising chatbot project from one of the world’s largest software companies. This will set the stage for your forthcoming battles in this arena.

- Chapter 2, “The OWASP Top 10 for LLM Applications”, introduces a project I founded in 2023 that aims to identify and address the unique security challenges posed by LLMs. The knowledge gained working on that directly led to my writing this book.

- Chapter 3, “Architectures and Trust Boundaries”, explores the structure of applications using LLMs, emphasizing the importance of controlling the various data flows within the application.

## Section 2: Risks, Vulnerabilities, and Remediations (Chapters 4–9)

In these chapters, we’ll break down the significant risk areas you face when developing LLM applications. These risks include issues with flavors familiar to any application security practitioner, such as injection attacks, sensitive information leakage, and software supply chain risk. You’ll also be introduced to classes of vulnerabilities well known to machine learning aficionados but less familiar in web development, such as training data poisoning.

Along the way, you’ll also learn about all-new security and safety concerns plaguing these new generative AI systems, such as hallucinations, overreliance, and excessive agency. I’ll walk you through real-world case studies to help you understand the risks and implications and advise you on how to prevent or mitigate these risks on a case-by-case basis:

- Chapter 4, “Prompt Injection”, explores how attackers can manipulate LLMs by crafting specific inputs that cause them to perform unintended actions.

- Chapter 5, “Can Your LLM Know Too Much?”, dives into the risks of sensitive information leakage, showcasing how LLMs can inadvertently expose data they’ve been trained on and how to safeguard against this vulnerability.

- Chapter 6, “Do Language Models Dream of Electric Sheep?”, examines the unique phenomenon of “hallucinations” in LLMs—instances where models generate false or misleading information.

- Chapter 7, “Trust No One”, focuses on the principle of zero trust, explaining the importance of not taking any output at face value and ensuring rigorous validation processes are in place to handle LLM outputs.

- Chapter 8, “Don’t Lose Your Wallet”, tackles the economic risks of deploying LLM technologies, focusing on denial-of-service (DoS), denial-of-wallet (DoW), and model cloning attacks. These threats exploit similar vulnerabilities to impose financial burdens, disrupt services, or steal intellectual property.

- Chapter 9, “Find the Weakest Link”, highlights the vulnerabilities within the software supply chain and the critical steps needed to secure it from potential breaches that could compromise the entire application.

By understanding and addressing these risks, developers can better secure their applications against an evolving landscape of threats.

## Section 3: Building a Security Process and Preparing for the Future (Chapters 10–12)

The chapters in Section 2 will give you the tools you need to understand and address the various individual threats you’ll see in this space. This last section is about bringing it all together:

- In Chapter 10, “Learning from Future History”, I’ll use some famous science fiction anecdotes to illustrate how multiple weaknesses and design issues can stitch together to spell disaster. By explaining these futuristic case studies, I hope to help you prevent a future like this from ever occurring.

- In Chapter 11, “Trust the Process”, we’ll get down to the serious business of building LLM-savvy security practices into your software factory—without this, I do not believe you can successfully secure this type of software at scale.

- Finally, in Chapter 12, “A Practical Framework for Responsible AI Security”, we’ll examine the trajectory of LLM and AI technologies to see where they’re taking us and the likely implications to security and safety requirements. I’ll also introduce you to the Responsible Artificial Intelligence Software Engineering (RAISE) framework that will give you a simple, checklist-based approach to ensuring you’re putting into practice the most important tools and lessons to keep your software safe and secure.

## Conventions Used in This Book

The following typographical conventions are used in this book:

### Italic

Indicates new terms, URLs, email addresses, filenames, and file extensions.

### Constant width

Used for program listings, as well as within paragraphs to refer to program elements such as variable or function names, databases, data types, environment variables, statements, and keywords.

### Constant width bold

Shows commands or other text that should be typed literally by the user.

### Constant width italic

Shows text that should be replaced with user-supplied values or by values determined by context.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_16_0.png)

This element signifies a tip or suggestion.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_16_1.png)

This element signifies a general note.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_16_2.png)

This element indicates a warning or caution.

## O'Reilly Online Learning

For more than 40 years, O'Reilly Media has provided technology and business training, knowledge, and insight to help companies succeed.

Our unique network of experts and innovators share their knowledge and expertise through books, articles, and our online learning platform. O'Reilly's online learning platform gives you on-demand access to live training courses, in-depth learning paths, interactive coding environments, and a vast collection of text and video from O'Reilly and 200+ other publishers. For more information, visit https://oreilly.com.
