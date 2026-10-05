# Chapter 5 Hacking MFA in Germany

long logon names, logon names composed of numbers, printer control characters, or executable code, for example. The idea is that a fuzzer would proactively try all sorts of combinations, expected and unexpected, looking to see if the accepting program would throw an error—and if an error is thrown, it is an error that might be exploited. Many of today's most aggressive bug-finding hunters use fuzzers to ferret out programming bugs.

# Penetration Testing

Penetration testing involves software-driven or skilled human adversaries looking to exploit a target. They might use fuzzing techniques, but usually go beyond just varying responses to inputs. They will focus on all the involved components looking for new and old vulnerabilities. With code reviews, the best penetration testing uses a combination of automated and human-based attackers.

# Vulnerability Scanning

Vulnerability scanning is almost performed by automated software that looks for known exploitable vulnerabilities. Vulnerability scanning is a subset of penetration testing, but it's focused on finding application vulnerabilities caused by errors and weaknesses. Usually it's looking for known vulnerabilities that have been patched by the vendor but remain unimplemented on the investigated target. It can also include looking for coding bugs, misconfigurations, default passwords, and performance-reducing issues. The best vulnerability scanners have upward of over 50,000 tests. Vulnerability scanners are great tools, but if they are the only ones used by a defender to find and prevent vulnerabilities, they can come short. Other methods, such as those suggested earlier, should also be used.

# Human Testing

Many vulnerabilities have been found simply by a person looking at a particular solution and trying to guess at different possible exploits. Any professional penetration tester uses a combination of their favorite automation tools and their own to find bugs and vulnerabilities. It takes a combination of experience, ingenuity, and persistence to be a good bug finder. In my personal experience (with over 20 years of professional penetration testing), I found half of the most critical bugs by simply hunting for vulnerabilities and bugs. Sometimes I simply guessed and tried something randomly. I found bugs right away using my first hunches and found bugs just before the moment I gave up in exhaustion.

I think a bug finder is like a god player. Everyone is playing the same rules, but some people seem to have more talent as they tend to "win" a lot than others. Most testers need to specialize in the type of bugs they find. They focus on one operating system type (say, Windows versus Linux Apple iOS), one language (say, Python), one type of server functionality (web, database, file, etc.), and so on. The best have expertise at multiple disciplines.