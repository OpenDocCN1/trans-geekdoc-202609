```
3rd Qu.:37.00  3rd Qu.:27.72
Max.     :41.85  Max.     :35.62
NA's     :63    NA's     :31

> sd(validation$FAM, na.rm = TRUE)

[1] 8.088397

> sum(is.na(validation$FAM))

[1] 63

> sum(is.na(validation$FAM[(validation$Content == "NTC")]))

[1] 6

> sum(is.na(validation$FAM[(validation$Content == "Neg Ctrl")]))

[1] 2
```

This quick data exploration showed that the raw amplification file contained 5304 data points, each uniquely identified with an index. The single target ‘SIV’ included 120 reactions subdivided into actual biological samples (‘Unknown’/‘Unkn’), positive controls (‘Control’/‘Pos Ctrl’), non-template controls (‘NTC’), and negative controls (‘Negative’/‘Neg Ctrl’). The reaction was completed in 50 cycles. The mean FAM Cq was 29.01 ± 8.09 cycles, and there were 63 samples with undetermined amplification cycle (Cq=NA). Of these 63 non-reactive reactions, six were NTC and two were negative controls, leaving 55 actual samples as PCR-negative. However, there were 264 missing data only from the FAM and HEX channels. The following commands will further explore the presence of missing entries in the data frame:

```
> colSums(is.na(amplification))
Run Cycle FAM HEX Well Index Type Target
0   0   -264 -264 0   0   0   0

> colSums(is.na(validation))
Run Well Fluor Target Content FAM HEX Index
0   0   0   0   0   63  31  0
```

The 63 missing values found for the validation data frame matched with the information retrieved in the previous step; the 264 missing values only in the FAM/HEX fields looks suspicious. The following commands will attempt to isolate the missing value and understand what the cause might be.