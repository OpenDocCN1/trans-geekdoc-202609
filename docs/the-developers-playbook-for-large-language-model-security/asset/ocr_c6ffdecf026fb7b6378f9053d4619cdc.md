Let's go ahead and add that sanitization step to our flow:

```
if toxicity_level > 0.7 or contains_PII:
    print("Warning: The output is not safe to return to the user.")
    is_safe = False
else:
    print("The output is safe to return to the user.")
    llm_output = sanitize_output(llm_output)

log_results(prompt, llm_output, is_safe)
```

# Conclusion

Following the techniques in this chapter, you can plan where you should trust your LLM and where you shouldn't; take sound, fact-based, risk-aware decisions; and balance your app's needs to be fully functional against our outlined risks.

Remember, Fox Mulder trusted no one at the start of the X-Files series. It was his fundamental mantra. However, he found people he could trust over time, like Agent Scully, Director Skinner, and the Lone Gunmen. However, he never lost his sense of paranoia, and the need to investigate and verify kept him alive through many perils. Remember, the truth is out there!

In this chapter, we reviewed the tenets of a zero trust architecture and discussed how that might apply to your LLM application. The vulnerabilities we've looked at in the book, ranging from prompt injection to hallucination to sensitive information disclosure, imply that zero trust is one of the essential tools you must add to your mental model. It's not just that you must worry about untrusted data coming *into* your LLM; you shouldn't fully trust the data or instructions coming *out* of your LLM. Your LLM is an untrusted entity because it lacks common sense. LLMs are powerful, but you must provide an additional layer of supervision for your application to be safe and secure.