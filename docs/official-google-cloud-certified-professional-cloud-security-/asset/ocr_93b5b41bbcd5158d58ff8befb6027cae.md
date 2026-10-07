Choose an infoType from the menu, and then click Add rule. A menu appears with two options:
Hotword rule and Exclusion rule.

For hotwords, choose Hotword rule. Then, the following:

+   I. In the Hotword field, enter a regular expression that Cloud DLP should look for.
II. From the Hotword proximity menu, choose whether the hotword you entered is before or after the chosen infoType.
III. In Hotword distance from infoType, enter the approximate number of characters between the hotword and the chosen infoType.
IV. In Confidence level adjustment, choose whether to assign matches to a fixed likelihood level or to decrease the likelihood level by a certain amount.
V. In the Exclude field, enter a regular expression (regex) that Cloud DLP should look for.
VI. From the Matching type, choose one of the following:

+   - Full match: The finding must completely match the regex.

+   - Partial match: A substring of the finding can match the regex.

+   - Inverse match: The finding doesn't match the regex.

For exclusion rules, choose Exclude rules. Then, the following:

You can add additional hotword or exclusion rules and rulesets to further refine your scan results.

# Confidence threshold

Every time Cloud DLP detects a potential match for sensitive data, it assigns it a likelihood value on a scale from Very unlikely to Very likely. When you set a likelihood value here, you are instructing Cloud DLP to only match data that corresponds to that likelihood value or higher.

The default value of Possible is sufficient for most purposes. If you routinely get matches that are too broad, move the slider. If you get too few matches, move the slider down.

When you're done, click Create to create the template. The template's summary information page appears.

Let us discuss some of the best practices for inspection.