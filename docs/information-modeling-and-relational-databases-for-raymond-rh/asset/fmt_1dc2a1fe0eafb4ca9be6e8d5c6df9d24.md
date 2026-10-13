
### 3.6 The following table lists the common names by which beer drinks of various volumes may be ordered in hotels in the states of Australia. Volumes are measured in fluid ounces (oz). The sample data is significant. A double hyphen “−” indicates that beer drinks of that volume are not on sale in that state. For instance, in Queensland exactly three different beer drinks may be ordered. Schematize this UoD.

| ![u05-09-9780443237904](images/B9780443237904000098/u05-09-9780443237904.jpg) |

---

### 3.7 The following report is from a system that records the driving test results. A person may take as many tests as he/she wishes, but cannot take more than one test on the same day. A minimum score of 80 is required to pass the test. Sometimes a person takes another test simply to try for a better score. Schematize this UoD.

| ![u05-10-9780443237904](images/B9780443237904000098/u05-10-9780443237904.jpg) |

---

## 5.4 Case Study: A Compact Disc Retailer

The following small case study is designed to consolidate the main ideas in CSDP steps 1–5. To derive maximum benefit from it, you should attempt to solve the problem yourself before looking at the solution. The business domain concerns a compact disc (CD) retailer who uses an information system to help with account and stock control, and to provide a specialized service to customers seeking information about specific musical compositions and artists.

[Fig. 5.32](#Ch005_159-209_B9780443237904000098.xhtml#f0165) illustrates the kind of musical information required for compact discs (some of the data is fictitious). Each disc contains several individual musical items, referred to as “tracks”. Although compact discs usually have about 20 tracks, for this example only a few tracks are listed.

![Fig. 5.32 Musical details about four compact discs.](images/B9780443237904000098/f05-32-9780443237904.jpg)

[Fig. 5.32](#Ch005_159-209_B9780443237904000098.xhtml#B-f0165) Musical details about four compact discs.

Before reading on, try to verbalize information from [Fig. 5.32](#Ch005_159-209_B9780443237904000098.xhtml#f0165) as elementary facts. Pay particular attention to the reference schemes involved.

Each compact disc has a CD number as its preferred identifier. Although not shown here, different discs may have the same name. Here, “CD” is used in a generic sense, like a catalog stock item. The retailer may have many copies of CD `654321-2` in stock, but for our purposes these are all treated as the same CD. In some applications (e.g., car sales), you do need to distinguish between different copies of the same model, but for our application this is not a requirement.

An artist is a person or a group of persons. For a given CD, a main artist is listed if and only if most of the tracks on the disc are by this artist (this constraint is enforced by a data entry operator, not by the system). Assuming each artist has an identifying name, we use the fact type `CompactDisc(CDNr) has main- Artist(.Name)`; otherwise we must replace `Artist` by `ArtistName`, thus `CompactDisc(CDNr) has main- ArtistName()`.

The record company that releases the disc must be recorded.

A challenging aspect of this application is understanding what is meant by “track” and determining its identification scheme. To clarify terms, you often need to consult the domain expert. The term “track” is commonly used in two senses: the `physical track` on a compact disc and the musical composition, or `work`, recorded on this track.

Within the context of a given CD, tracks are identified by their track number, or sequential position on the disc. But there are many CDs in this domain, so we need both the CD number and the track number to identify a track. Using “track” in the physical sense, the fact involving “Maya’s Dance” in the first CD report may be verbalized thus:

|  |
| --- |
| `The Track that is on the CompactDisc with CDNr ‘654,321–2’ and has TrackNr 1` |
| `stores a work with the Title ‘Maya’s Dance’.` |

This used the compound reference scheme: `Track(is on CompactDisc, has TrackNr)`. Notice that the fact predicate says “*a* work” of that title, not “*the* work”. Different musical works may have the same title. Although a physical track occurs on only one CD, the same work may appear on many discs. For example, track 5 of CD `654321-2` and track 2 of CD `925838-2` hold the same title, and probably the same work. There are also two tracks titled “Sultans of Swing”, but these have different durations so are not the same work. In rare cases, two tracks with the same title can occur on the same CD (not shown here).

The previous verbalization did not include `Work` as an entity type. Should we include it? Do we need to know whether a work on one disc is exactly the same as a work on another disc? Only the domain expert can tell us whether he/she wants to know this. For our solution, let’s assume the answer to this question is “no”.

However, if the answer were “yes”, we would need a 1:1 identification scheme for `Work`. A natural reference scheme for `Work` is hard to find (even the combination of title, artist, and duration might not be enough). We might use an artificial identifier (e.g., `WorkNr`), but this might be hard to enforce because humans are responsible for enforcing the constraints in preferred reference schemes.

The duration of a track is the time it takes to play. Each track has exactly one duration, measured in seconds. Most tracks have one or more singers. Some tracks may have no singers (these are instrumental rather than vocal tracks).

[Table 5.12](#Ch005_159-209_B9780443237904000098.xhtml#t0065) shows an extract from another report from the same application. This lists the quantity in stock and recommended retail price (in US dollars) of each compact disc. This table is updated when required, on a daily basis. The stock quantity of a disc may drop to zero. For simplicity, let’s assume that only the current stock and price figures are recorded (no history).

[Table 5.12](#Ch005_159-209_B9780443237904000098.xhtml#B-t0065)

Stock quantity and recommended retail price of compact discs.

| ![t05-12-9780443237904](images/B9780443237904000098/t05-12-9780443237904.jpg) |

---

An extract from a third report required of the information system is shown in [Table 5.13](#Ch005_159-209_B9780443237904000098.xhtml#t0070). For simplicity, let’s assume that sales records are kept only for the current calendar year of operation (otherwise, the year needs to be included). For each month that has passed, figures are kept of the quantity of copies sold and the net revenue (profit) accruing from sales of the compact discs in that month.

[Table 5.13](#Ch005_159-209_B9780443237904000098.xhtml#B-t0070)

Monthly sales figures (small sample only).

| ![t05-13-9780443237904](images/B9780443237904000098/t05-13-9780443237904.jpg) |

---

For simplicity, these figures are restricted to the four compact discs shown earlier. In reality, this table would have thousands of rows and much larger totals. This table is updated on a monthly basis. Daily sales figures are kept manually but are not part of the application.

For each month, if a disc was on the stock list and had no sales for that month, then a figure of zero is recorded for it. If a disc is a new stock item in the month, then it has no sales figures recorded for previous months (e.g., disc `792542-2` was not in stock in January).

This is the last report we need to model. Before reading on, try to verbalize this report and then schematize the whole application. Include all uniqueness and mandatory role constraints, and derivation rules.
