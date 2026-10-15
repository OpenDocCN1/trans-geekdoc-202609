
“Dirty data” is data that falls short on the *believability* dimension, in particular, evaluating whether the data are complete, consistent, and accurate. It is important to note that these categories are not mutually exclusive; a variable might be simultaneously inconsistent and inaccurate.

## Complete

For our purposes, “complete” means whether any values in each record are missing (internally complete).

“Complete” does not mean that every possible member of the population is represented in the data. With a well-designed sample, it is possible that a subset of the population can provide an accurate set of measures about the population. Furthermore, it is possible to determine whether the records are an accurate representation of the whole.

## Consistent

We will consider a measure to be “consistent” if the same value is reported in the same way.

Some examples of consistency:

- Units are consistent. One example is temperature, and ensuring that the values are consistently reporting in degrees Celsius, not mixing Fahrenheit and Kelvin. Another might be in a survey or form with an international audience, where salary might be completed by respondents in the values of their local currency.
- Spelling is consistent. My home province in Canada is “British Columbia”, but is often abbreviated to “B.C.” or “BC”. Or consider the 57 different ways that “Philadelphia” was spelled in the US Paycheck Protection Program (PPP) applications. (Au, 2020a)
- In some cases, the mode of data collection can introduce differences in the value recorded. This can apply to everything from variability of scientific instruments such as air quality sensors (Khreis et al., 2008) to how people respond to surveys conducted in different media (Abeysundera, 2015) (Holbrook et al., 2003) (St-Pierre and Béland, 2004).

## Accurate

When we say “accurate”, we mean that the value recorded in our data is the value measured.

Some examples of inaccurate data are:

- The use of a default (or sentinel) value, inserted as a placeholder for unknown or missing values in place of a missing or “unknown” value. This is sometimes part of the data collection or database software, leading to values that should have been “unknown” being entered as the default. This can be the consequence of a data entry validation process that requires an entry (that is, data entry cannot continue until the field has an entry) or an entry in a particular format, such as a date. In these cases, the sentinel value can be entered instead of an explicit “NA”.

  > Dr Davis Lawrence, director of safety-literature database the SafeLit Foundation...tells me that ‘in most US states the quality of police crash reports is at best poor for use as a research tool. ... Data-quality checks were rare and when quality was evaluated it was found wanting. For example, in Louisiana for most crashes in the 1980s most of the occupants were males who were born on January 1st, 1950. Almost all of the vehicles involved in crashes were the 1960 model year.’ Except they weren’t. These were just the default settings. (Perez, 2019, p.190)

- A data entry error. Perhaps the most common are typographical errors, where the wrong value is entered. Another type is what we might call a “variable transposition error” (where the value is transposed one column over, something that happens all too often with address records, where the city name might end up in the state/province column).
- Values are transformed automagically by software. Microsoft’s Excel spreadsheet program is the most famous of these, converting many non-date values into date format, and assigning new values to store the data. For example, entering the character string “SEPT1” gets converted to September 1st of the current year. There is documented evidence that this software behaviour has caused errors in gene research. (Zeeberg et al., 2004), (Abeysooriya et al., 2021)
- Dates may be stored as a numeric value (or “serial number”) representing the number of days elapsed from a fixed starting point—a starting point that varies by operating system. For example, Excel for Windows uses January 1, 1900 as the first day, while earlier version Macintosh computers, and by extension Excel for Macintosh, used January 1, 1904 as the start date. Thus the same date would be stored as different values¹. (https://docs.microsoft.com/en-us/office/troubleshoot/excel/1900-and-1904-date-system)

  1. “Differences between the 1900 and the 1904 date system in Excel”

- Contradiction. For example, imagine that a single individual is entered into two databases, but when we compare them we see that the date of birth differs, perhaps due to a non-ISO8601 entry: 07-08-79 and 08-07-79 both have the same digits but one could be mm-dd-yy and the other dd-mm-yy...we just don’t know which is the correct one. Or is one a typo?
- Cultural ignorance (for want of a better term).

  > “Prawo Jazdy” was a supposed Polish national who was listed by the Garda Síochána in a police criminal database as having committed more than 50 traffic violations in Ireland. A 2007 memorandum stated that an investigation revealed prawo jazdy [pra.v jaz.d] to be Polish for ‘driving licence’, with the error arising due to officers mistaking the phrase, printed on Polish driving licences, to be a personal name while issuing traffic tickets. (Wikipedia contributors, 2021)

## 2.2.1 Tidy data

When we are cleaning our data, we should also consider the structure. The goal should be a tidy structure, one that meets the following three principles or rules:

- Each variable must have its own column.
- Each observation must have its own row.
- Each value must have its own cell. (Wickham, 2014)

In many instances, achieving a tidy structure may require reshaping the data, using the {tidyr} package’s pivot_() functions (Wickham, 2021b). In others, the data may have multiple variables in each cell which need to be split (such as addresses) into a separate column for each variable.

Other common structural problems that fall outside the four broad data quality categories include:

1. Column headers are values instead of variable names. A frequently-encountered example are units of time, as in the example below. In the table below, the “values” are the years. Tables structured in this way can only display the values of one variable; in this case, it is the population of the country.

| country | 1952 | 2007 |
|---|---|---|
| Canada | 14,785,584 | 33,390,141 |
| United States | 157,553,000 | 301,139,947 |

A preferable structure would be to have a variable “year” and another “population”. This tidy structure also permits other variables measured during those years to be incorporated, rather than displayed in a separate table.

| country | year | population | life expectancy |
|---|---|---|---|
| Canada | 1952 | 14,785,584 | 68.75 |
| Canada | 2007 | 33,390,141 | 80.65 |
| United States | 1952 | 157,553,000 | 68.44 |
| United States | 2007 | 301,139,947 | 78.24 |

2. Variable names that are duplicated (this is possible in some data storage formats, including plain-text and Excel files).
3. Inappropriate data types, such as numbers or logical values stored as character strings.
4. Multiple data types in a column. For example, some records are numbers and some are character strings. The values themselves could be entirely correct, but if some number entry includes commas as thousands separators, the variable will be read and stored as a character type.

## 2.3 Cleaning the data

If the data fails to meet our standards or quality, we need to clean the data. Which doesn’t sound like a lot of fun. Didn’t we want to be data scientists or business intelligence experts or academic scientists uncovering the insights hiding in the data? Don’t we want to be doing analysis?

There is a strong argument to be made that the process of cleaning data is a fundamental part of the analytic process, or the corresponding statement that any analytic process requires data cleaning.
