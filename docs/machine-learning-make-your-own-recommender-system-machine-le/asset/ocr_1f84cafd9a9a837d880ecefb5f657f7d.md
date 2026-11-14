| Feature | Feature Class | Feature | Feature Class |
|---|---|---|---|
| Suburb | String | Bedroom2 | Integer |
| Address | String | Bathroom | Integer |
| Rooms | Integer | Car | Integer |
| Type | String | Landsize | Integer |
| Price | Integer | BuildingArea | Integer |
| Method | String | YearBuilt | Integer |
| SellerG | String | CouncilArea | String |
| Date | TimeDate | Latitude | String |
| Distance | Float | Longitude | String |
| Postcode | Integer | Regionname | String |
| Propertycount | Integer | |

Table 7: Feature information from the Melbourne Housing dataset

```
#Specify included features
X = df.loc[:, ['Price', 'Distance', 'Bedroom2', 'Bathroom', 'Landsize', 'BuildingArea', 'YearBuilt']].values
```

# Step 5

Next, input the values of our target as listed in the following table.

| Feature | Target Value |
|---|---|
| Price | $1,350,000 |
| Distance to the City | 2km |
| Bedrooms | 2 |
| Bathrooms | 2 |
| Land Size | 220m² |
| Building Size | 200m² |
| Year Built | 2005 |

Table 8: Known preferences of the target user based on their search history

```
#Specify target values
target = [1350000, 2, 2, 2, 220, 200, 2005]
```

# Step 6