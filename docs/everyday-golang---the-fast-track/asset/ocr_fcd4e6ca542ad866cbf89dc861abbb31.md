+   - More focused on a single use-case or responsibility
+   - Scaled & monitored automatically
+   - Built with a template, without dealing with HTTP servers

But they cover the same use-cases as microservices. They can read from and write to databases. They can serve webpages to customers, and have custom domains. They can be used to run batch jobs and to process data. There's not much that a function cannot do.

When we say functions, we're really saying: “It’s a microservice that has some additional management” and by being able to manage all your services in one way, it reduces the repetition, so that you can ship code faster.

So if you write, maintain or monitor back-end services for a living, then you could probably make use of functions in your day-job.

See also: Serverless 2.0: Get started with the PLONK Stack • Alex Ellis • GOTO 2019

I cover specific use-cases from the community and from commercial users in the blog post: Exploring Serverless Use-cases from Companies and the Community.

# Introduction to OpenFaaS

My earliest memory of Go was when I was learning and writing about Docker in 2015. The concept of reproducible builds fixed a major pain point at the company I was working at, but the technology was a world apart from what was being used at the time, so I embarked on a journey to relate it to others. In 2016 Docker released their “Swarm” product that allowed multiple computers running containers to work together as part of a distributed system. It must have been around that time that I heard of the term FaaS and Serverless, and I had no idea what the difference was between the two.

It was only when I started trying to use AWS Lambda for writing, debugging and shipping Alexa skills that I realised what containers could do for functions.

At the time, there was no way to run Go code inside AWS Lambda and the common trick was to add a binary to the Node.js runtime and have it get executed for every request. Then there was the pipeline. Working at an enterprise company, I couldn’t understand why it was so hard to link source control to AWS Lambda and have it deploy changes directly. Instead ZIP files and binaries compiled on your local machine were the way to go.

That’s when I started OpenFaaS, then called “faas” in late 2016 and the first version was demoed on the main stage at Dockercon in May the following year. One of the demos involved responding to Star events on the alexellis/faas GitHub repository. For each star, a virtual polaroid was generated and then uploaded to an S3 bucket and presented on the big screen.

Back then, if you asked 10 people what Serverless meant, they would probably give a different answer depending on where they worked, how much work they had done with functions and what time they started their journey. I started in 2016 and at the time, Serverless was largely synonymous with Functions as a Service (FaaS). Various working groups have tried to define the term, or to create a specification, but these efforts have resulted in weak standards and a lot of confusion. I was part of the CNCF’s Serverless Working Group that wrote the CNCF Whitepaper.

When I talk to users of OpenFaaS, they tend to care less about granular billing and whether server management is required, and more on having a cloud-agnostic runtime for code and events.

# The value vs cloud functions

So what’s the value of OpenFaaS vs. cloud functions?

+   - Avoid getting locked-in with a specific cloud provider This means if you have a product, you can run it on a public cloud for customers, but also run it on their own private cloud on-premises.
+   - Set your own limits Rather than being told the maximum amount of RAM allowable for a function, or the maximum size, number of concurrent requests, or timeout value, you can set this yourself. What would you do, if you hit a limit and it affected an important customer?