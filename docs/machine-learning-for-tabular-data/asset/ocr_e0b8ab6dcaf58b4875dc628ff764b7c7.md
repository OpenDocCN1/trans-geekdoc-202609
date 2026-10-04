# Preparing and exploring your data

```
summary_listings = summary_listings.assign(
nis_new= (summary_listings['name']
    str.contains('new', case=False)
    .astype(int)),
is_studio=(summary_listings['name']
    str.contains('studio', case=False)
    .astype(int)),
has_shared_bath=(summary_listings['name']
    str.contains('shared', case=False)
    .astype(int)),
has_half_bath=(summary_listings['name']
    str.contains('half', case=False)
    .astype(int))
)
sum_listings['days_since_last_review'] = (
datetime.today()
    -summary_listings['last_review']
).dt.days
summary_listings['days_since_last_review'] = (
summary_listings['days_since_last_review']
    -summary_listings['days_since_last_review'].min()
)
zero_reviews = summary_listings['number_of_reviews'] == 0
ratio = summary_listings['number_of_reviews_ltm'] / /
summary_listings['number_of_reviews']
summary_listings['number_of_reviews_ltm_ratio'] = (
np.where(zero_reviews, 0, ratio)
)
```

Checks if the word **new** is present in the name (case-insensitive)

Checks if the word **studio** is present in the name (case-insensitive)

Checks if the word **shared** is present in the name (case-insensitive)

Checks if the word **half** is present in the name (case-insensitive)

Calculates the number of days between today's date and the last_review date

Calculates the number of reviews_ltm to number_of_reviews for each list

The summary data also has a price feature that we could use as a target. Still, we prefer to create by aggregating the calendar.csv to decide whether to pick an average of all prices, the minimum, or the maximum. The calendar .csv contains information for each day about the availability of the accommodation, its price (also adjusted for discounts), and the minimum and maximum of nights allowed booking at that time. We are interested in processing the adjusted price as a target, representing the effective market price of the accommodation.

# 7.3 Creating the calendar from daily listings

```
calendar = pd.read_csv("calendar.csv")

calendar['adjusted_price'] = (
    calendar['adjusted_price']
    .apply(lambda x: float(
        x.replace('$', ''))
        .replace(',', ''))
    )
)

```

Removes the dollar sign ($) and commas,) from the values and converts them to float