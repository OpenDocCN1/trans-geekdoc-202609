# 1.3 Data in the wild

Most data science and statistics textbooks use example data sets that are nicely formatted and easy to import. Anscombe’s Quartet (Anscombe, 1973) is a famous example of a small data set that was designed to produce specific statistical results; it is included in the base version of R (R Core Team, 2021). Other data sets might be excerpted to use as teaching examples (Bryan, 2017), chosen for their statistical properties (Horst et al., 2022), compiled as examples to demonstrate a methodology or technique (Kuhn, 2020), or used to clean, validate, and aggregate still-larger data collections (Friendly et al., 2020).

But in real life the data we find ourselves working with is, more often than not, entirely different from those text book examples.

> *Classroom data are like teddy bears; real data are like a grizzly with salmon blood dripping out of its mouth¹.*

+   - Data can be stored in different formats–spreadsheets, databases, software-specific file formats, websites, and PDF files. We need to have tools to access the data, no matter the file format.
+   - The data might be stored in an untidy layout (Wickham, 2014), or inconsistently structured.
+   - We might receive data from multiple sources, so we end up with two files that have the same value but are coded in different ways. For example, my home province in Canada can be represented as “British Columbia”, “B.C.”, or “BC”. All three are accurate, but these variations can cause problems if they are inconsistent across the data sources (or even more problematically, in the same variable). And don’t get me started on date formats—we’ll save that for later.
+   - Data might have as-of-yet undetected errors. It might be incomplete, inconsistent, or it might have data entry mistakes and typos.
+   - It might have bias...and there are many different types of bias.