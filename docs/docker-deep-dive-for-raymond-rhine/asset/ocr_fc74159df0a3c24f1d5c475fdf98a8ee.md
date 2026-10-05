As with all consensus algorithms, more participants means
longer times to achieve consensus. It's like choosing where to
eat — it's always quicker and easier for three people to decide
than it is for 33! With this in mind, it's usually a best practice to
have three or five managers for HA. Seven might work, but
tthreeree or five usually right for most swarms.

A final word of caution regarding manager HA. While you
should definitely spread your managers across availability
zones, they they need to be connected by fast and reliable networks.
This means you should think carefully and do lots of testing
before implementing multi-cloud clusters implementing multi-
cloud HA.

# Built-in Swarm security

Swarm ships with a lot of security features, such as a built-in
cificate authority (CA), mutual TLS, an encrypted cluster
store, encrypted networks, cryptographic node IDs and join
tokens, and more. Fortunately, Swarm automatically configures
them with sensible defaults.

# Locking a Swarm

Despite all of Swarm's security features, restarting an old
manager or restoring an old backup can potentially