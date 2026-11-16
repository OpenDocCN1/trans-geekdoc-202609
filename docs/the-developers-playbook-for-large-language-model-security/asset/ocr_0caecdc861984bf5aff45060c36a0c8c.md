# Education

Educating users about the capabilities and limitations of LLMs is critical to promoting responsible and ethical usage.

# Regulation

Regulatory frameworks may be necessary to govern the use of LLMs in critical domains, ensuring data privacy, algorithmic accountability, and user protection. The Hood case highlights the potential need for legal clarification around AI responsibility and liability.

The Brian Hood case exemplifies the potential pitfalls of hallucination and overreliance in LLMs. It calls for more robust safeguards, user education, and responsible application of this powerful technology. Only through a multipronged approach can we prevent future harm and ensure AI's beneficial integration into society.

# Open Source Package Hallucinations

This incident centers around using LLMs as coding assistants. It has become commonplace now for developers to use LLMs to assist them while writing code. Developers might use general-purpose chatbots, such as ChatGPT, or dedicated copilots, such as GitHub Copilot. A survey by GitHub in June 2023 showed that 92% of developers working in large companies were using LLMs to help them code. This section will look at a notable example of the risks of hallucination and overreliance using these code generation tools.

These days, a substantial portion of code written uses open source libraries. This includes code written by AI coding assistants, which may leverage existing open source libraries to make code more compact or efficient. Usually, this works fine, but in some cases, these assistants have been shown to hallucinate about the existence of various open source libraries. They imagine a useful library to solve problems and generate code that uses the imaginary library. This may seem harmless enough, but in 2023, the research team at Vulcan Cyber demonstrated how hackers could use this flaw to insert malicious code into applications. They dubbed the issue simply “AI package hallucination.”

In this case, the research team crafted the attack by searching through popular Stack Overflow questions and asking ChatGPT to solve them. They quickly found over 100 hallucinated packages suggested by an assistant bot that were not published on any popular code repository. Because these were based on popular questions, many other developers will likely ask their AI assistants to generate similar code, which may include the same hallucination.