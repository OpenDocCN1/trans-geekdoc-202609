9 Such as Dropbox or Google Drive.

10 Some examples of total system backups would be SpiderOak, Carbonite, Backblaze, or Crashplan.

11 In particular, avoid special regular expression symbols as we often match filenames with regex to read them into R . See Wrangling Words .

12 Note the file extensions. Some operating systems hide this by default, but this can and should be changed by the user.

Backup systems are slightly different from “cloud sync” platforms as they typically back up an entire system and only in one direction. This allows us to reinstate an older version of our system should our current system be damaged beyond repair.

Folders are intuitive organizational tools. So are file names. Names should be unique and informative. They should avoid capitalization and spaces, because different operating systems and programs may treat these inconsistently. We should also avoid “special characters,” such as & or (). Below are a few examples (see also Bryan and Hester 2019).

```
01_script_load_packages.R
02_script_wrangle_text.R
data_survey_attributes_movies.csv
data_survey_attributes_books.csv
data_demographics_nmsu.txt
2020-05-01_scrape_reddit_maliciouscompliance.rds
```

# MEMOING AND DATASHEETS

In qualitative research, especially ethnography, it is common practice to write “analytic memos.” This is different from “field-notes” in that the focus is self-reflection and self-observation. What did we do today? What did we learn? How has our thinking changed today? What will we do differently tomorrow? This is also where we explicitly bring together theory and analysis. This is the narrative counterpart to our coding. Certainly, researchers will have different strategies, but at minimum, we should approach a day of coding as a day in the field and set aside time for memoing, and periodically review these memos as a project progresses.

Despite some tendencies to use the largest available corpora, we cannot ignore the ways every analysis of text is drawn from a subset. We need to know, as best we can, what subset we’re studying. If we do not consider this, we can mistake patterns in the assembly of the corpus for patterns within the texts. Essential to this process, then, is documenting—in meticulous detail—the steps we take to collect and select our texts.

Our analytic memos, with our scripts, can be used later to create datasheets. To keep in step with open science, our corpus and/or derivatives will need to be shared with our community. Without accompanying documentation, researchers may use our corpus but misunderstand their findings. Therefore, following Gebru and colleagues (2021:86), we argue that “every dataset be accompanied with a datasheet that documents its motivation, composition, collection process, recommended uses, and so