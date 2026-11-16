# # Find the Weakest Link

> > You are the weakest link. Goodbye!
> > —Every episode of The Weakest Link game show (BBC/NBC)

On the morning of December 10th, 2021, I woke up to an overnight message from David Linder, my company’s Chief Information Security Officer (CISO). It said, “Call me as soon as you’re up. It’s important.” I knew this wasn’t going to be good news. Your CISO calling in the middle of the night is the last thing an executive wants.

Once I got ahold of David, he told me that in the past 24 hours, major corporations worldwide were being hacked. The problem had been traced back to a single, open source library embedded into *millions* of applications. *Wired* magazine published a story about the incident that cried, “The Internet Is on Fire!”

Later in this chapter, I’ll tell you more about that story. I give that snippet now to impress upon you how critical the issue of *software supply chain security* has become for software development today. Some readers of this book may be coming from an application security (AppSec) background and are reading this chapter for specific guidance about securing LLMs. However, I’m sure other readers are coming here already understanding LLMs and looking for guidance on security best practices. Knowing this, I will set up this chapter to cover both.

We’ll start by covering the basic concepts of supply chain security. Then, we will examine the unique structure and challenges of an LLM application’s supply chain. We’ll discuss some best practices, but we must also acknowledge this is a fast-moving part of the LLM security landscape. So, we’ll wrap up with a discussion about the future of the space.