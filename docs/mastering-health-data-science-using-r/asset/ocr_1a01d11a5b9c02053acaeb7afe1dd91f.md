```
#>   New Hampshire   New Jersey    New Mexico    New York
#>   27              27            27            27
#>   North Carolina  North Dakota  Ohio          Oklahoma
#>   27              27            27            27
#>   Oregon          Pennsylvania  Rhode Island  South Carolina
#>   27              27            27            27
#>   South Dakota    Tennessee     Texas         Utah
#>   27              27            27            27
#>   Vermont         Virginia      Washington Washington, D.C.
#>   27              27            27            27
#>   West Virginia   Wisconsin     Wyoming
#>   27              27            27
```

For the covidcases data, our data is at the county level. We need to summarize the data instead. In this case, some states were observed for fewer weeks than others.

```
# Find state names and number of weeks recorded for each state
unique(covidcases$state)
#>  [1] "California"        "Florida"
#>  [3] "New Hampshire"     "Washington"
#>  [5] "Massachusetts"     "Arizona"
#>  [7] "Texas"             "Georgia"
#>  [9] "New York"          "Wisconsin"
#> [11] "Oregon"            "North Carolina"
#> [13] "Nebraska"          "Illinois"
#> [15] "Utah"              "Indiana"
#> [17] "Tennessee"         "Pennsylvania"
#> [19] "Michigan"          "Oklahoma"
#> [21] "Kentucky"          "Connecticut"
#> [23] "Colorado"          "Virginia"
#> [25] "Nevada"            "South Dakota"
#> [27] "Minnesota"         "Ohio"
#> [29] "Vermont"           "New Jersey"
#> [31] "Maryland"          "Iowa"
#> [33] "Missouri"          "South Carolina"
#> [35] "Hawaii"            "District of Columbia"
#> [37] "Louisiana"         "Kansas"
#> [39] "Maine"             "Arkansas"
#> [41] "Idaho"             "Alabama"
#> [43] "Montana"           "Mississippi"
#> [45] "North Dakota"      "New Mexico"
#> [47] "Alaska"            "Wyoming"
```