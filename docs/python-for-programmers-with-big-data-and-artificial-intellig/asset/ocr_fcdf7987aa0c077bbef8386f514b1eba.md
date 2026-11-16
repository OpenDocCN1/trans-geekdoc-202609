grade level.

+   • smog_score—The Simple Measure of Gobbledygook (SMOG), which corresponds to the years of education required to understand text. This measure is considered particularly effective for healthcare materials. ⁸

⁸ tps://en.wikipedia.org/wiki/SMOG.

+   • dalechall_score—The Dale-Chall score, which can be mapped to grade levels from 4 and below to college graduate (grade 16) and above. This score considered to be most reliable for a broad range of text types. ⁹ ᵒ

⁹ tps://en.wikipedia.org/wiki/Readability#The_Dale%E2%80%93Chall_formula.

ᵒ ttp://www.readabilityformulas.com/articles/how-do-i-decide-hich-readability-formula-to-use.php.

For more details on each of the readability scores produced here and several others, see

tps://en.wikipedia.org/wiki/Readability

The Textatistic documentation also shows the readability formulas used:

ttp://www.erinhengel.com/software/textatistic/

# 11.5 NAMED ENTITY RECOGNITION WITH SPACY

NLP can determine what a text is about. A key aspect of this is named entity recognition, which attempts to locate and categorize items like dates, times, quantities, places, people, things, organizations and more. In this section, we’ll use the named entity recognition capabilities in the spaCy NLP library ¹, ² to analyze text.

¹ tps://spacy.io/.

²You may also want to check out Textacy ( tps://github.com/chartbeat-abs/textacy)an NLP library built on spaCy that supports additional NLP tasks.

# Install spaCy

To install spaCy, open your Anaconda Prompt (Windows), Terminal (macOS/Linux) or shell (Linux), then execute the following command:

lick here to view code image

```
conda install -c conda-forge spacy
```

Windows users might need to run the Anaconda Prompt as an Administrator for proper software installation privileges. To do so, right-click Anaconda Prompt in the start menu and select More > Run as administrator.

Once the install completes, you also need to execute the following command, so spaCy can