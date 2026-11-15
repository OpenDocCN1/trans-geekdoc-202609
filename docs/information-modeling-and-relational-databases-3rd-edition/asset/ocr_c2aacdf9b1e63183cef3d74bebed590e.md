![](bbox=[0.22, 0.1, 0.78, 0.38])

+   * Each Viewer is defined as a Person who watches television for PeriodRate > 0.
+   * Each Reader is defined as a Person who reads newspapers for PeriodRate > 0.
+   * Each MediaAdult is defined as both a Viewer and a Reader who has Age >= 18.

# FIG. 6.53 The conceptual schema for the media survey example.

This analysis yields the “diamond-shaped” subtype graph of Fig. 6.53 as well as the information recorded for each node in the graph. However, we can only make educated guesses as to the actual subtype definitions—these should be checked with a domain expert if one is available.

In practice, reports often display different kinds of nulls in the same way. For example, a blank space might be used for both our simply unknown “?” and inapplicable “–” marks. So, you should clarify the meaning of any nulls with the domain expert before deciding how to handle them.

Sometimes, subtype-specific details appear in separate reports, and the titles of these reports may then correspond to subtypes or to subtype components (disjuncts or conjuncts).

# Table 6.6 An output report from the media survey.

| Person | Age (y) | Television (h/week) | Newspaper (h/week) | Favorite channel | Favorite paper | Preferred news |
|---|---|---|---|---|---|---|
| 5001 | 41 | 0 | 10 | - | The Times | - |
| 5002 | 60 | 0 | 25 | - | The Times | - |
| 5003 | 16 | 20 | 2 | 9 | The Times | - |
| 5004 | 18 | 20 | 5 | 2 | Daily Mail | TV |
| 5005 | 13 | 35 | 0 | 7 | - | - |
| 5006 | 17 | 14 | 4 | 9 | Daily Sun | - |
| 5007 | 50 | 8 | 10 | 2 | Daily Sun | NP |
| 5008 | 33 | 0 | 0 | - | - | - |
| 5009 | 13 | 50 | 0 | 10 | - | - |