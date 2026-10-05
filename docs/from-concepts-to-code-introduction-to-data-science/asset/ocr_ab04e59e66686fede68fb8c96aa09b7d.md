```
'state': 'VA',
  'country': 'United States',
  'zipcode': 22902,
  'reviews': {
  'num_5_star' : 10,
  'num_4_star' : 5,
  'num_3_star' : 3,
  'num_2_star' : 1,
  'num_1_star' : 1
}
```

Notice there is a hierarchy, where address and reviews are separate objects at the top level. Inside the address, there are components at the same level, such as street number and state. 'street_number' is an example of a key, and it is associated with its value of 200. This is a key-value pair. In this format, it is straightforward for computer programs to retrieve data elements.

From the website NFL.com/standings, we might care about rankings in a division such as:

| Division: AFC West |
| Chiefs |
| Chargers |
| Raiders |
| Broncos |
| Division: AFC East |
| Bills |
| Dolphins |
| Patriots |
| Jets |

This data might be structured as follows:

```
{
  'division': {
    'AFC West': {
      {'rank':['Chiefs', 'Chargers', 'Raiders', 'Broncos']},
    },
    'AFC East': {
      {'rank':['Bills', 'Dolphins', 'Patriots', 'Jets']}
    }
  }
}
```