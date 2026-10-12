
# 13.3 Electronic Voting

Once again, we step back to examine a broad issue that cuts across several areas we encounter as we live our lives. Each of us is a citizen, and in most of our countries, we vote to express our views and choose people who represent us in our towns, states, and countries. Traditionally, voting has taken place by means of paper ballots: We mark our choices on a sheet of paper and then hand the paper to someone who will tally the votes.

But even on paper, security looms large. A good security engineer investigating what makes for good voting can point out the C-I-A requirements in the electoral process:

- **Confidentiality**. We want to be able to cast a ballot without revealing our votes to others.
- **Integrity**. We want votes to represent our actual choices, and not be changed between the time we mark the ballot and the time our vote is counted. We also want every counted ballot to reflect one single vote of an authorized person. That is, we want to be able to ensure that our votes are authentic and that the reported totals accurately reflect the votes cast.
- **Availability**. Usually, votes are cast during an approved pre-election period or on a designated election day, so we must be able to vote when voting is allowed. If we miss the chance to vote or if voting is suspended during the designated period, we lose the opportunity to cast a vote in the given election.

With careful control of paper ballots, we can largely satisfy these requirements, but for large populations the efficiency of such systems is poor. Moreover, it can be very expensive to provide paper voting opportunities in remote locations, thanks to travel costs and inefficiencies of small scale. For these reasons, many countries and localities have turned to computerizing voting systems to improve availability and efficiency without sacrificing privacy or accuracy. In this section, we consider first the definition of electronic voting and then the critical issues involved in ensuring that such systems are really fair, confidential, accurate, and available. Notice that we also mention the privacy aspects of electronic voting in [Chapter 9](#ch09.html#ch09).

---

**Paper-based and electronic elections both have weaknesses. Choosing one form requires evaluating the pros and cons of both.**

---

## What Is Electronic Voting?

Electronic voting (sometimes called e-voting) refers to an election process that is partially or completed automated. In other words, electronic means are provided for casting votes, counting votes, or both. Thus, you may see the phrase used in different ways, depending on the implied meaning. In this book, we use the phrase to mean complete automation of the voting process from end to end. Note, however, that other people focus on specific activities in the voting process (maintaining lists of registered voters or transmitting votes from a voting booth to a central tabulation facility) that could be done electronically. In particular, casting votes on the Internet has popular appeal, and so some people look at that as electronic voting. We recognize the importance of these individual efforts but want to consider the full case.

### Casting Ballots

Ballots can be cast electronically in many ways, including with punched cards, telephones, optical character readers, secure web pages, or special devices that support vote capture by touch screen or other input technology. For instance, Tony Blair, British prime minister, announced in July 2002 that in the British 2006 general election, citizens would vote in any of four ways: online (by Internet) from a work or home location, by mail, by touch-tone telephone, or at polling places through online terminals. Then all the votes would be counted electronically. Similarly, in Brazil, where voting is mandatory and fines are imposed for not voting, every jurisdiction has special-purpose voting machines that look like a variation of a bank’s automated teller devices. Brazilians cast their ballots from anywhere in the country, designating desired selections by using a unique number associated with each candidate.

---

**Electronic voting machines can make voting easier, which might increase voter turnout.**

---

Specialized voting devices are sometimes called direct-recording electronic voting systems, or DREs; they capture a voter’s choices automatically from touch screens, electronic pens, or other input devices. There are also hybrid technologies. For instance, a machine may electronically record a vote but then generate a paper copy that the voter can examine and verify. The paper ballot is then counted by hand or processed electronically.
