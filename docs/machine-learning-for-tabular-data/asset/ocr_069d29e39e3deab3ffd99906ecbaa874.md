# 250 CHAPTER 7 An end-to-end example using XGBoost

```
summary_listings = summary_listings.assign(
type_of_accommodation=(
    summary_listings['name']
    .str.extract(
        f'(!|)'.join(classification_list))',
        flags=re.IGNORECASE),
area_of_tokyo=(
    summary_listings['name']
    .str.extract(
        r(\d+)?\s*',
        flags=re.IGNORECASE),
score=(
    summary_listings['name']
    .str.extract(
        r'(\d+),(\d+)',
        flags=re.IGNORECASE)
    .astype(float),
number_of_bedrooms=(
    summary_listings['name']
    .str.extract(
        r'(\d+)?\s*(?:bedrooms)?',
        flags=re.IGNORECASE)
    .fillna(0)
    .astype(int),
number_of_beds=(
    summary_listings['name']
    .str.extract(
        r'(\d+)\s+(?:beds)?\b',\n        flags=re.IGNORECASE)
    .fillna(0)
    .astype(int),
number_of_baths=(
    summary_listings['name']
    .str.extract(
        r'(?P<bath>\d+)?\s*(?:shared\s)?+' + r'(?P<half>-half)?baths?\b',
        flags=re.IGNORECASE)
    .fillna(0)
    .astype(int)))
```

Extracts the type of accommodation from a list of options

Extracts the area of Tokyo in the listing name

Extracts the rating score from a star symbol followed by a numerical

Extracts the number of bedrooms from the listing name

Extracts the number of beds from the listing name

Extracts the number of baths from the listing name

Listing 7.2 completes the feature extraction by creating additional Boolean columns based on specific keywords in the name column. It computes calculated features based on a difference telling us the number of days between today's date and the last_review date and a ratio expressing how the number of reviews in the last year relates to the total number of reviews. A ratio can reveal if the bulk of reviews is recent or if the listing has been successfully maintained in the past.

# Listing 7.2 Extracting binary flags and time information

```
import numpy as np
import pandas as pd
from datetime import datetime
```