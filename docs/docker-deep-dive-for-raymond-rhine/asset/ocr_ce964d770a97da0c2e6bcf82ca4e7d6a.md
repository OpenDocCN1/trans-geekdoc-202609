# 13: Docker Networking

It’s always the network!

Any time we experience infrastructure issues, we always blame the network. One of the reasons we do this is that networks are at the center of everything. With this in mind, it’s important you have a strong understanding of Docker networking.

In the early days of Docker, networking was hard. Fortunately, these days it’s almost a pleasure ;)

This chapter will get you up to speed with the fundamentals of Docker networking. You’ll learn all the theory behind the Container Network Model (CNM) and libnetwork, and you’ll get your hands dirty with lots of examples. You’ll learn about overlay networks in the next chapter.

I’ve divided the chapter into the following sections:

+   - Docker networking – the TLDR
- Docker networking theory
- Single-host bridge networks via port mappings
- Connecting to existing networks and VLANs
- Service Discovery