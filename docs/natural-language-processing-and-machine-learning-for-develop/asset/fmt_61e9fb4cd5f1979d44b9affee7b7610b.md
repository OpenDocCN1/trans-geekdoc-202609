
A dataset can be a CSV, TSV, Excel spreadsheet, a table in an RDMBS, a document in a NoSQL database, the output from a Web service, and so forth. As you will see, someone needs to analyze the dataset to determine which features are the most important and which features can be safely ignored in order to train a model with the given dataset.

A dataset can vary from very small (a couple of features and 100 rows) to very large (more than 1,000 features and more than one million rows). If you are unfamiliar with the problem domain, then you might struggle to determine the most important features in a large dataset. In this situation, you might need a “domain expert” who understands the importance of the features, their inter-dependencies (if any), and whether or not the data values for the features are valid. In addition, there are algorithms (called dimensionality reduction algorithms) that can help you determine the most important features. For example, Principal Component Analysis (PCA) s one such algorithm, which is discussed in more detail later in this appendix.

### Data Preprocessing

Data preprocessing is the initial step that involves validating the contents of a dataset, which involves making decisions about missing and incorrect data values:

*   dealing with missing data values

*   cleaning “noisy” text-based data

*   removing HTML tags

*   dealing with emojis/emoticons

*   filtering data

*   grouping data

*   handling currency and date formats (i18n)

Cleaning data is a subset of data wrangling that involves removing unwanted data as well as handling missing data. In the case of text-based data, you might need to remove HTML tags, punctuation, and so forth. In the case of numeric data, it’s less likely (although still possible) that alphabetic characters are mixed together with numeric data. However, a dataset with numeric features might have incorrect values or missing values (discussed later). In addition, calculating the minimum, maximum, mean, median, and standard deviation of the values of a feature obviously pertain only to numeric values.

After the preprocessing step is completed, data wrangling is performed, which refers to transforming data into a new format. For example, you might have to combine data from multiple sources into a single dataset. For example, you might need to convert between different units of measurement (such as date formats, currency values, and so forth so that the data values can be represented in a consistent manner in a dataset.

In case you didn’t already know, currency and date values are part of something that is called i18n (internationalization), whereas l10n (localization) targets a specific nationality, language, or region. Hard-coded values (such as text strings) can be stored as resource strings in a file that’s often called a resource bundle, where each string is referenced via a code. Each language has its own resource bundle.

### Data Types

If you have written computer programs, then you know that explicit data types exist in many programming languages, such as C, C++, Java, TypeScript, and so forth. Some programming languages, such as JavaScript and awk, do not require initializing variables with an explicit type: the type of a variable is inferred dynamically via an implicit type system (i.e., one that is not directly exposed to a developer).

In machine learning, datasets can contain features that have different types of data, such as a combination of one or more of the following:

*   numeric data (integer/floating point and discrete/continuous)

*   character/categorical data (different languages)

*   date-related data (different formats)

*   currency data (different formats)

*   binary data (yes/no, 0/1, and so forth)

*   nominal data (multiple unrelated values for identification)

*   ordinal data (multiple and related values for ordering)

Consider a dataset that contains real-estate data, which can have as many as 30 columns (or even more), often with the following features:

*   the number of bedrooms in a house: numeric value and a discrete value

*   the number of square feet: a numeric value and (probably) a continuous value

*   the name of the city: character data

*   the construction date: a date value

*   the selling price: a currency value and probably a continuous value

*   the “for sale” status: binary data (either “yes” or “no”)

Nominal data is qualitative, which includes: categories, colors, names, labels, and yes/no values. Another example of nominal data is a set of colors such as {red, green, blue}. A third example of nominal data is the seasons in a year: although many (most?) countries have four distinct seasons, some countries have two distinct seasons. However, keep in mind that seasons can be associated with different temperature ranges (summer versus winter). An example of ordinal data is an employee pay grade: 1=entry level, 2=one year of experience, and so forth. Just to add a bit more emphasis to three types of numeric data:

*nominal data* involving numbers simply name or identify something (such as members of a team or a particular zip code) without reference to quantity or rank

*ordinal data* involves numbers that indicate the order or rank of items (such as third place or second in a queue)

*cardinal data* involves numbers that indicate quantity (such as 8 employees)

An example of binary data is the pair {male, female}, and in some (many?) cases, this feature needs to be included during the training of a model. The solution involves converting {male, female} to a numeric counterpart, such as {0,1}. If you needed to do so with the previous set of colors, you could use {0,1,2} as the counterparts for {red, green, blue}. Categorical data is discussed in more detail later in this chapter.

## Preparing Datasets

If you have the good fortune to inherit a dataset that is in pristine condition, then data-cleaning tasks (discussed later) are vastly simplified: in fact, it might not be necessary to perform *any* data cleaning for the dataset. However, if you need to create a dataset that combines data from multiple datasets that contain different formats for dates and currency, then you need to perform a conversion to a common format.

If you need to train a model that includes features that have categorical data, then you need to convert that categorical data to numeric data. For instance, the Titanic dataset contains a feature called “gender,” which is either male or female. As you will see later in this appendix, Pandas makes it extremely simple to “map” male to 0 and female to 1.

### Continuous versus Discrete Data

As a simple rule of thumb: *discrete data* is a set of values that can be counted whereas *continuous data* must be measured. Discrete data can “reasonably” fit in a drop-down list of values, but there is no exact value for making such a determination. One person might think that a list of 500 values is discrete, whereas another person might think it’s continuous.

For example, the list of provinces of Canada and the list of states of the United States are discrete data values, but is the same true for the number of countries in the world (roughly 200) or for the number of languages in the world (more than 7,000)?

However, values for temperature, humidity, and barometric pressure are considered continuous. Currency is also treated as continuous, even though there is a measurable difference between two consecutive values. The smallest unit of currency for US currency is one penny, which is 1/100th of a dollar (accounting-based measurements use the “mil,” which is 1/1,000th of a dollar).

Continuous data types can have subtle differences. For example, someone who is 200 centimeters tall is twice as tall as someone who is 100 centimeters tall; similarly for 100 kilograms versus 50 kilograms. However, temperature is different: 80 degrees Fahrenheit is not twice as hot as 40 degrees Fahrenheit.
